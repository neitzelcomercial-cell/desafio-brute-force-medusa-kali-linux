# Ferramentas utilizadas

## Kali Linux

Distribuição utilizada como estação de análise. O endereço atual confirmado no laboratório é `192.168.56.10`.

## Nmap

Ferramenta de reconhecimento utilizada para verificar o host de laboratório e identificar portas e serviços.

Resultados registrados em etapas anteriores:
- FTP na porta 21, identificado como vsftpd 2.3.4.
- FTP na porta 2121, identificado como ProFTPD 1.3.1.
- SMB/Samba nas portas 139 e 445.

As versões são transcritas conforme as saídas observadas. A identificação do Nmap deve ser interpretada como resultado de detecção de serviço, não como garantia absoluta da versão.

## Cliente FTP

Foi registrada conexão FTP ao host de laboratório e autenticação anônima aceita em uma etapa anterior. Também foi relatada validação manual com uma conta de laboratório. Os registros devem ser associados à configuração de rede vigente no momento de cada teste.

## SMB / smbclient

Foi utilizada a ferramenta `smbclient` para consultar compartilhamentos SMB. Uma listagem registrada apresentou compartilhamentos como `print$`, `tmp`, `opt`, `IPC$`, `ADMIN$` e `msfadmin`. Uma tentativa anterior retornou `NT_STATUS_LOGON_FAILURE`; esse resultado deve permanecer documentado como falha, sem generalizar o resultado de outras tentativas.

## Medusa 2.3

O Medusa foi utilizado em testes históricos de autenticação FTP e SMB no laboratório. O endereço do alvo nos comandos abaixo é o que constava no registro original, quando Metasploitable era identificado como `192.168.56.10`. A configuração posterior passou a identificar Metasploitable como `192.168.56.101`; portanto, não reutilize o IP histórico como endereço atual.

### Teste FTP — registro histórico

```bash
medusa -h 192.168.56.10 -u msfadmin -P ~/ftp_senhas.txt -M ftp -n 21 -t 1 -f
```

Parâmetros:
- `-h`: host que constava como alvo no momento do teste.
- `-u`: usuário único informado.
- `-P`: arquivo local de candidatos a senha.
- `-M ftp`: módulo FTP.
- `-n 21`: porta TCP 21.
- `-t 1`: uma tarefa simultânea.
- `-f`: interromper após encontrar uma conta válida.

Resultado reportado na saída compartilhada: `ACCOUNT FOUND: [ftp]` e `[SUCCESS]` para a conta de laboratório `msfadmin`. A senha foi omitida. A saída específica não está entre as cinco capturas atualmente versionadas.

### Teste SMB — registro histórico

```bash
medusa -h 192.168.56.10 -u msfadmin -P ~/ftp_senhas.txt -M smbnt -n 445 -t 1 -f
```

O comando utilizou o módulo `smbnt` na porta TCP 445, com um usuário e uma lista de senhas.

Resultado reportado na saída compartilhada: `ACCOUNT FOUND: [smbnt]` e `SUCCESS (ADMIN$ - Access Allowed)` para a conta de laboratório `msfadmin`. A senha foi omitida. A saída específica não está entre as cinco capturas atualmente versionadas.

**Classificação correta:** esse teste SMB com um usuário e várias senhas é uma tentativa de força bruta contra uma conta. Não demonstra, sozinho, password spraying, que normalmente aplica uma ou poucas senhas a vários usuários. A consulta de compartilhamentos com smbclient não comprova enumeração de usuários.

## DVWA — formulário web

O DVWA foi acessado no laboratório, com Security Level em Low. No módulo Brute Force, foi observado no Firefox DevTools/Network um pedido GET para o caminho `/dvwa/vulnerabilities/brute/`, com os campos `username`, `password` e `Login`.

Foram realizados testes manuais:
- `admin` com uma senha incorreta de teste: mensagem de credenciais incorretas.
- `admin` com a credencial padrão do laboratório: mensagem de boas-vindas.

Esses resultados validam o comportamento manual do formulário, mas não constituem um ataque automatizado.

### Limitação do módulo HTTP do Medusa

A consulta `medusa -M http -q` exibiu opções para User-Agent, diretório, método HTTP, autenticação BASIC/DIGEST/NTLM, domínio e cabeçalhos adicionais. Essa ajuda não demonstra suporte direto a parâmetros de formulário web e análise de mensagens de sucesso/erro do DVWA. Por isso, o projeto não afirma que o Medusa automatizou o formulário.

## Boas práticas

- Limitar tentativas e aplicar atrasos progressivos.
- Monitorar falhas e sucessos de autenticação.
- Exigir senhas fortes e MFA.
- Restringir serviços e compartilhamentos por rede e privilégio.
- Não publicar credenciais, cookies, tokens ou dados pessoais.
- Executar testes apenas em laboratório próprio ou com autorização explícita.
