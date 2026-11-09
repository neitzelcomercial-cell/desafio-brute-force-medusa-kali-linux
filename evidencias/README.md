# Evidências do laboratório

As capturas abaixo foram revisadas visualmente e organizadas em ordem cronológica. As descrições registram apenas o que é possível confirmar nas imagens.

| Ordem | Arquivo | O que a captura demonstra |
|---:|---|---|
| 01 | [01-2026-11-05-154604.png](01-2026-11-05-154604.png) | Pesquisa no Windows por arquivos e pastas relacionados ao Metasploitable. |
| 02 | [02-2026-11-05-160147.png](02-2026-11-05-160147.png) | Relação de discos virtuais disponíveis no ambiente VirtualBox, incluindo arquivos associados ao Kali e ao Metasploitable. |
| 03 | [03-2026-11-05-160258.png](03-2026-11-05-160258.png) | Tela de configuração de um disco virtual no VirtualBox. |
| 04 | [04-2026-11-05-165954.png](04-2026-11-05-165954.png) | Verificação de interfaces e endereços de rede no Kali Linux com comandos como `ip link` e `ip addr`. |
| 05 | [05-2026-11-05-172032.png](05-2026-11-05-172032.png) | Consulta das interfaces de rede do Kali Linux com `ip link`. |
| 06 | [06-2026-11-05-173016.png](06-2026-11-05-173016.png) | Varredura Nmap do Metasploitable, identificando serviços e portas expostas no laboratório. |
| 07 | [07-2026-11-05-180526.png](07-2026-11-05-180526.png) | Teste de conectividade com ping, tentativa de resolução de nome e identificação do serviço FTP na porta 21. |
| 08 | [08-2026-11-05-231004.png](08-2026-11-05-231004.png) | Resultado de varredura Nmap com identificação de diversos serviços, incluindo SMB nas portas 139/445 e FTP na porta 2121. |
| 09 | [09-2026-11-05-231807.png](09-2026-11-05-231807.png) | Enumeração SMB com `smbclient`: uma tentativa de autenticação falha e, em seguida, listagem de compartilhamentos disponíveis. |
| 10 | [10-2026-11-05-232751.png](10-2026-11-05-232751.png) | Exploração de listagem de conteúdo em um compartilhamento SMB; a saída também registra uma resposta de erro do serviço. |
| 11 | [11-2026-11-05-233409.png](11-2026-11-05-233409.png) | Resultado de script Nmap relacionado à configuração de segurança SMB, incluindo informações sobre autenticação e assinatura de mensagens. |
| 12 | [12-2026-11-05-233630.png](12-2026-11-05-233630.png) | Enumeração dos protocolos SMB suportados pelo serviço na porta 445. |
| 13 | [13-2026-11-05-233859.png](13-2026-11-05-233859.png) | Descoberta de informações do sistema e do nome da máquina por meio do script Nmap `smb-os-discovery`. |
| 14 | [14-2026-11-05-234354.png](14-2026-11-05-234354.png) | Detecção de versão dos serviços FTP e SMB com Nmap. |
| 15 | [15-2026-11-05-234412.png](15-2026-11-05-234412.png) | Registro de uma tentativa com nome de script Nmap inválido e, depois, execução da detecção de versão dos serviços. |
| 16 | [16-2026-11-05-235152.png](16-2026-11-05-235152.png) | Verificação Nmap do FTP anônimo, indicando que o servidor permite login anônimo. |
| 17 | [17-2026-11-05-235422.png](17-2026-11-05-235422.png) | Conexão manual ao FTP e autenticação anônima, seguida de listagem do diretório. |

## Observações sobre as evidências

- As imagens 18 e 19 foram retiradas desta pasta por não documentarem o laboratório: uma pertence a outro projeto e a outra mostra uma tela de entrega da plataforma.
- As capturas atuais documentam preparação do ambiente, reconhecimento, enumeração SMB e verificações FTP.
- **Ainda é necessário adicionar capturas específicas dos resultados do Medusa nos testes FTP e SMB**, com qualquer senha ou dado sensível ocultado.
- Não publique senhas, hashes, tokens ou dados pessoais. Os testes devem permanecer restritos ao laboratório autorizado.
