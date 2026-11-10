# Ambiente de laboratório

Esta página registra a configuração utilizada no desafio e diferencia a configuração final confirmada dos endereços que apareceram nos primeiros registros.

## Inventário atual confirmado

| Item | Informação |
|---|---|
| Plataforma de virtualização | Oracle VirtualBox |
| Máquina de análise | Kali Linux |
| IP atual do Kali | `192.168.56.10` |
| Máquina de destino | Metasploitable 2 |
| IP atual do alvo | `192.168.56.101` |
| Rede | Host-Only |
| Aplicação web | DVWA no ambiente de laboratório |

A comunicação entre Kali e Metasploitable foi confirmada por ping no ponto de retomada do projeto.

## Nota sobre registros anteriores

Em uma etapa anterior, a documentação e os comandos de teste identificavam Kali como `192.168.56.20` e Metasploitable como `192.168.56.10`. Posteriormente, após ajustes de rede, o inventário confirmado passou a Kali `192.168.56.10` e Metasploitable `192.168.56.101`.

Os comandos históricos de Medusa foram preservados com o endereço que constava no registro original. Essa diferença de configuração precisa ser considerada ao interpretar os resultados históricos; não se deve substituir automaticamente o IP antigo pelo atual sem repetir o teste.

## Serviços identificados

As saídas de Nmap registradas no desenvolvimento identificaram, entre outros:

| Porta | Serviço | Identificação registrada |
|---|---|---|
| 21/tcp | FTP | vsftpd 2.3.4 |
| 22/tcp | SSH | OpenSSH |
| 80/tcp | HTTP | Apache |
| 139/tcp | SMB | Samba |
| 445/tcp | SMB | Samba |
| 2121/tcp | FTP | ProFTPD 1.3.1 |

A porta 21 e a porta 2121 foram identificadas como serviços FTP distintos. Não presumir que o resultado de um teste em uma porta vale para a outra.

## SMB e compartilhamentos

Foi registrada uma consulta com `smbclient` ao host que, naquele momento, era identificado como Metasploitable. A listagem apresentou compartilhamentos como `print$`, `tmp`, `opt`, `IPC$`, `ADMIN$` e `msfadmin`. Também houve registro de `NT_STATUS_LOGON_FAILURE` em uma tentativa anterior; portanto, não se deve afirmar que todas as tentativas de autenticação foram bem-sucedidas.

## Procedimentos realizados

- Preparação das máquinas virtuais no VirtualBox.
- Configuração de rede Host-Only.
- Verificação de conectividade entre as VMs.
- Reconhecimento de serviços com Nmap.
- Consulta de compartilhamentos SMB com smbclient.
- Testes históricos de autenticação com Medusa em FTP e SMB.
- Acesso ao DVWA, configuração de segurança Low e validação manual do módulo Brute Force.

## Observações de segurança

Mantenha o laboratório isolado. Não publique senhas, cookies, tokens, hashes ou dados pessoais. Os endereços IP devem ser conferidos novamente se o laboratório for reconfigurado.
