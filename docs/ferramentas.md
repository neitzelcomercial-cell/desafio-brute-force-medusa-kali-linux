# Ferramentas utilizadas

## Kali Linux

Distribuição Linux utilizada como estação de análise no laboratório. Nas capturas, a interface `eth0` aparece ativa. O endereço registrado para o Kali é `192.168.56.20`.

## Nmap

Ferramenta de reconhecimento de rede usada para verificar o host de laboratório e identificar portas e serviços disponíveis.

### Resultados observados

- O host `192.168.56.10` respondeu ao reconhecimento.
- A verificação específica `nmap -sV -p 21 192.168.56.10` identificou `21/tcp` como FTP, `vsftpd 2.3.4`.
- A captura do reconhecimento amplo mostra, entre outros, FTP em `21/tcp` (vsftpd 2.3.4), SMB em `139/tcp` e `445/tcp` (Samba smbd 3.X–4.X) e outro serviço FTP em `2121/tcp` (ProFTPD 1.3.1).
- A captura ampla também lista serviços SSH, Telnet, SMTP, DNS, HTTP, RPC, NFS, MySQL, PostgreSQL, VNC, IRC e Tomcat.

As versões são transcritas conforme aparecem na captura de tela. Para reproduzir o levantamento, registrar também a linha completa do comando utilizado e a saída integral.

## Cliente FTP

Foi estabelecida uma conexão FTP com o host de laboratório em etapa anterior. O serviço aceitou autenticação anônima (`anonymous`). A sessão foi encerrada com o comando `bye`.

O reconhecimento atual também diferencia dois serviços FTP: vsftpd na porta 21 e ProFTPD na porta 2121. Não presumir que ambos foram testados com o cliente FTP sem uma evidência específica de cada sessão.

## SMB / smbclient

Foi utilizada a ferramenta `smbclient` para consultar os compartilhamentos do host `192.168.56.10`, com o comando visível na captura:

```bash
smbclient -L //192.168.56.10 -U msfadmin
```

A listagem exibiu os compartilhamentos `print$`, `tmp`, `opt`, `IPC$`, `ADMIN$` e `msfadmin`, associados ao servidor `METASPLOITABLE` e ao grupo `WORKGROUP`. Há também uma captura de uma listagem de diretório no prompt interativo do SMB. Uma tentativa exibiu `NT_STATUS_LOGON_FAILURE`; por isso, registrar cada tentativa separadamente, sem generalizar o resultado.

## Medusa

Medusa é uma ferramenta de auditoria de autenticação compatível com diferentes módulos de serviço.

### Progresso confirmado

- O comando de ajuda `medusa -h` foi executado para conhecer as opções disponíveis.
- Foi iniciada a exploração da documentação e dos módulos.
- Houve preparação inicial de uma wordlist para o cenário FTP.
- Não há registro confirmado de uma execução de tentativa de autenticação com Medusa contra o serviço. Portanto, nenhum resultado de brute force deve ser declarado como concluído.

### Próximos registros

Quando houver evidência, documentar o comando usado, o significado dos parâmetros, o serviço do laboratório, o resultado observado e as medidas de contenção. Os testes devem ser limitados ao ambiente autorizado.

## Padrão para documentar comandos

Para cada comando efetivamente executado, registrar:

1. Finalidade.
2. Significado dos parâmetros.
3. Host ou serviço de laboratório utilizado.
4. Resultado observado.
5. Evidência correspondente.
6. Cuidados e limites de uso.
