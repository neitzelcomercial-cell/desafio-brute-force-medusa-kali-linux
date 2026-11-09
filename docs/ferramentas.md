# Ferramentas utilizadas

## Kali Linux

Distribuição Linux utilizada como estação de análise no laboratório. Nas capturas, a interface `eth0` aparece ativa. O endereço registrado para o Kali é `192.168.56.20`.

## Nmap

Ferramenta de reconhecimento de rede usada para verificar o host de laboratório e identificar portas e serviços disponíveis.

### Resultados observados

- O host `192.168.56.10` respondeu ao reconhecimento.
- A verificação `nmap -sV -p 21,2121 192.168.56.10` mostrou as portas 21 e 2121 abertas. A identificação anterior apontou vsftpd 2.3.4 na porta 21 e ProFTPD 1.3.1 na porta 2121.
- A verificação `nmap -sV -p 139,445 192.168.56.10` identificou Samba `smbd 3.X - 4.X` nas portas 139 e 445, no grupo `WORKGROUP`.
- A captura do reconhecimento amplo também lista serviços SSH, Telnet, SMTP, DNS, HTTP, RPC, NFS, MySQL, PostgreSQL, VNC, IRC e Tomcat.

As versões são transcritas conforme apareceram nas saídas observadas. A identificação de serviço feita pelo Nmap pode ser genérica; por isso, não tratar o nome associado ao número da porta como confirmação isolada da versão do serviço.

## Cliente FTP

Foi estabelecida uma conexão FTP com o host de laboratório em etapa anterior. O serviço aceitou autenticação anônima (`anonymous`). Em uma validação manual posterior, o usuário de laboratório `msfadmin` também conseguiu autenticar na porta 21. A sessão foi encerrada com `bye`.

O reconhecimento diferencia dois serviços FTP: vsftpd na porta 21 e ProFTPD na porta 2121. Não há evidência de que ambos tenham sido testados com o cliente FTP.

## SMB / smbclient

Foi utilizada a ferramenta `smbclient` para consultar os compartilhamentos do host `192.168.56.10`, com o comando:

```bash
smbclient -L //192.168.56.10 -U msfadmin
```

A listagem exibiu os compartilhamentos `print$`, `tmp`, `opt`, `IPC$`, `ADMIN$` e `msfadmin`, associados ao servidor `METASPLOITABLE` e ao grupo `WORKGROUP`. Uma tentativa anterior exibiu `NT_STATUS_LOGON_FAILURE`; esse resultado deve ser mantido separado dos testes posteriores, sem generalizar o resultado de todas as tentativas.

## Medusa

Medusa 2.3 foi utilizado no laboratório para avaliar autenticação nos serviços FTP e SMB. O módulo FTP foi consultado e o módulo `smbnt` 3.0 foi identificado.

### Teste FTP — resultado observado

Comando executado:

```bash
medusa -h 192.168.56.10 -u msfadmin -P ~/ftp_senhas.txt -M ftp -n 21 -t 1 -f
```

Significado dos parâmetros:

- `-h`: endereço do host de laboratório.
- `-u`: usuário informado para o teste.
- `-P`: caminho do arquivo de candidatos a senha.
- `-M ftp`: seleciona o módulo FTP.
- `-n 21`: seleciona a porta TCP 21.
- `-t 1`: limita a execução a uma tarefa simultânea.
- `-f`: interrompe a execução após encontrar uma conta válida.

Resultado reportado pelo Medusa: `ACCOUNT FOUND: [ftp]` e `[SUCCESS]` para o usuário de laboratório `msfadmin` no host `192.168.56.10`. A saída original continha a senha em texto claro; ela foi omitida desta documentação para evitar exposição de credenciais.

### Teste SMB — resultado observado

Antes do teste, o comando `nmap -sV -p 139,445 192.168.56.10` confirmou Samba nas portas 139 e 445.

Comando executado:

```bash
medusa -h 192.168.56.10 -u msfadmin -P ~/ftp_senhas.txt -M smbnt -n 445 -t 1 -f
```

Significado dos parâmetros: os mesmos parâmetros de host, usuário, wordlist, concorrência e parada antecipada descritos no teste FTP; `-M smbnt` seleciona o módulo SMBNT e `-n 445` seleciona a porta TCP 445.

Resultado reportado pelo Medusa: `ACCOUNT FOUND: [smbnt]` com `SUCCESS (ADMIN$ - Access Allowed)` para o usuário de laboratório `msfadmin` no host `192.168.56.10`. Isso indica que o módulo reportou autenticação válida e acesso permitido ao compartilhamento administrativo `ADMIN$` durante sua verificação. A saída original continha a senha em texto claro; ela foi omitida desta documentação.

### Limites e cuidados

- Os testes foram direcionados ao Metasploitable 2 do laboratório isolado e autorizado.
- A wordlist utilizada tinha três entradas; seu conteúdo não é reproduzido aqui.
- O resultado descreve o que o Medusa reportou no ambiente de laboratório, não uma garantia de acesso equivalente em outros sistemas.
- Não publicar senhas, hashes, tokens ou outros segredos em capturas, logs ou no repositório.
- Em ambientes reais, preferir autenticação forte, limitar tentativas, monitorar falhas de login, restringir compartilhamentos administrativos e desabilitar protocolos/versões legados quando possível.

## Padrão para documentar comandos

Para cada comando efetivamente executado, registrar:

1. Finalidade.
2. Significado dos parâmetros.
3. Host ou serviço de laboratório utilizado.
4. Resultado observado.
5. Evidência correspondente.
6. Cuidados e limites de uso.
