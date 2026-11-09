# Ambiente de laboratório

Esta página registra a configuração do laboratório utilizado no desafio, separando informações confirmadas de detalhes que ainda precisam de evidência.

## Objetivo

Descrever as máquinas virtuais, a rede de laboratório e os serviços disponibilizados para os testes autorizados.

## Inventário confirmado

| Item | Informação |
|---|---|
| Plataforma de virtualização | Oracle VirtualBox |
| Máquina de análise | Kali Linux |
| IP do Kali | `192.168.56.20` |
| Máquina de destino | Metasploitable 2 |
| IP do alvo | `192.168.56.10` |
| Rede | Host-Only (rede privada do laboratório) |

Durante o trabalho, foram observadas as interfaces `eth0` ativas no Kali e no Metasploitable. No teste de conectividade registrado, o Kali recebeu 4 respostas de 4 pacotes enviados ao alvo, com 0% de perda. A preparação no VirtualBox utilizou os discos virtuais associados às duas máquinas. Esses detalhes fazem parte do histórico documentado do laboratório; nem todos possuem uma imagem entre as cinco capturas preservadas.

## Serviços identificados pelo Nmap

A saída do reconhecimento de serviços no host `192.168.56.10`, registrada durante o trabalho, identificou o host ativo e diversas portas abertas. Entre os serviços transcritos:

| Porta | Serviço | Identificação exibida |
|---|---|---|
| 21/tcp | FTP | vsftpd 2.3.4 |
| 22/tcp | SSH | OpenSSH 4.7p1 Debian 8ubuntu1 |
| 23/tcp | Telnet | Linux telnetd |
| 25/tcp | SMTP | Postfix smtpd |
| 53/tcp | DNS | ISC BIND 9.4.2 |
| 80/tcp | HTTP | Apache httpd 2.2.8 (Ubuntu) DAV/2 |
| 111/tcp | RPC | rpcbind 2 |
| 139/tcp | SMB | Samba smbd 3.X–4.X |
| 445/tcp | SMB | Samba smbd 3.X–4.X |
| 512/tcp | exec | netkit-rsh rexecd |
| 513/tcp | login | OpenBSD/Solaris rlogind |
| 514/tcp | shell | Netkit rshd |
| 1099/tcp | Java RMI | GNU Classpath grmiregistry |
| 1524/tcp | bindshell | Metasploitable root shell |
| 2049/tcp | NFS | nfs |
| 2121/tcp | FTP | ProFTPD 1.3.1 |
| 3306/tcp | MySQL | MySQL 5.0.51a-3ubuntu5 |
| 5432/tcp | PostgreSQL | PostgreSQL DB 8.3.0–8.3.7 |
| 5900/tcp | VNC | VNC protocol 3.3 |
| 6000/tcp | X11 | access denied |
| 6667/tcp | IRC | UnrealIRCd |
| 8009/tcp | AJP13 | Apache Jserv (Protocol v1.3) |
| 8180/tcp | HTTP | Apache Tomcat/Coyote JSP engine 1.1 |

Uma verificação específica da porta 21 também registrou `vsftpd 2.3.4`. Portanto, os registros de FTP devem distinguir o serviço da porta 21 (vsftpd) do serviço da porta 2121 (ProFTPD). Essa verificação é descrita no texto, mas sua imagem não está entre as cinco capturas preservadas.

## SMB e compartilhamentos

Foi executado `smbclient -L //192.168.56.10 -U msfadmin`. O resultado registrado lista os compartilhamentos `print$`, `tmp`, `opt`, `IPC$`, `ADMIN$` e `msfadmin`, além do grupo de trabalho `WORKGROUP` e do servidor `METASPLOITABLE`. Também foi registrada uma listagem de diretório no prompt do cliente SMB. Uma tentativa anterior apresentou `NT_STATUS_LOGON_FAILURE`; a documentação não deve tratar toda tentativa de autenticação como bem-sucedida.

## Procedimentos já realizados

- Máquinas virtuais preparadas no VirtualBox.
- Rede privada Host-Only configurada.
- Interfaces de rede `eth0` observadas como ativas.
- Comunicação entre as máquinas testada com ping (4 respostas, 0% de perda).
- Reconhecimento com Nmap realizado.
- Serviços FTP, SMB e outros serviços identificados.
- Consulta específica à porta 21 realizada com Nmap.
- Enumeração de compartilhamentos SMB realizada.
- Conexão ao serviço FTP estabelecida em etapa anterior.
- Login FTP anônimo aceito no laboratório em etapa anterior.

## Itens a confirmar ou complementar

- Captura detalhada das configurações da rede Host-Only no VirtualBox.
- Guardar a linha completa do comando Nmap usado no reconhecimento amplo; a saída registrada mostra os serviços identificados, mas não o comando inteiro.
- Registrar separadamente os comandos e resultados completos do cliente SMB.
- Anexar evidências específicas da sessão FTP e da autenticação anônima, se disponíveis.

## Observações de segurança

Todos os testes devem permanecer restritos ao laboratório próprio e isolado ou a sistemas com autorização explícita. Não publicar senhas, tokens ou dados pessoais nas evidências.
