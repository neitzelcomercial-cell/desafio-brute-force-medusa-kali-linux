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

Os endereços acima foram registrados durante a configuração e os testes anteriores do laboratório. Recomenda-se anexar as capturas originais da configuração de rede como evidência final.

## Serviços identificados

Em uma saída de reconhecimento anteriormente registrada, foram observados:

| Porta | Serviço | Versão/identificação |
|---|---|---|
| 21/tcp | FTP | vsftpd 2.3.4 |
| 445/tcp | SMB (NetBIOS/SMB) | Samba smbd 3.X–4.X |

Também houve referência anterior a ProFTPD 1.3.1 durante a exploração das informações de FTP. A relação exata dessa versão com a saída principal precisa ser conferida na captura original antes de consolidar o inventário.

## Procedimentos já realizados

- Máquinas virtuais preparadas no VirtualBox.
- Rede privada Host-Only configurada.
- Comunicação entre as máquinas testada.
- Reconhecimento com Nmap realizado.
- Serviços FTP e SMB identificados.
- Conexão ao serviço FTP estabelecida.
- Login FTP anônimo aceito no laboratório.

## Itens a confirmar ou complementar

- Captura da configuração Host-Only no VirtualBox.
- Saída completa do Nmap, incluindo data e parâmetros utilizados.
- Confirmação da versão ProFTPD 1.3.1 e do contexto em que apareceu.
- Detalhes da configuração da máquina Metasploitable 2.

## Observações de segurança

Todos os testes devem permanecer restritos ao laboratório próprio e isolado ou a sistemas com autorização explícita. Não publicar senhas, tokens ou dados pessoais nas evidências.
