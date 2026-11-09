# Índice de evidências do laboratório

Após a revisão visual das capturas originais, foram mantidas somente as **5 imagens que acrescentam evidência técnica direta** ao fluxo de reconhecimento e enumeração. Os números originais dos arquivos foram preservados para manter a rastreabilidade.

| Arquivo | Etapa documentada |
|---|---|
| [07-2026-11-05-180526.png](07-2026-11-05-180526.png) | Conectividade com o alvo, teste da porta FTP e identificação inicial do serviço. |
| [09-2026-11-05-231807.png](09-2026-11-05-231807.png) | Consulta de compartilhamentos SMB e registro da tentativa de autenticação malsucedida antes da listagem. |
| [14-2026-11-05-234354.png](14-2026-11-05-234354.png) | Detecção de versões dos serviços FTP e SMB nas portas avaliadas. |
| [16-2026-11-05-235152.png](16-2026-11-05-235152.png) | Verificação Nmap de permissão de FTP anônimo. |
| [17-2026-11-05-235422.png](17-2026-11-05-235422.png) | Conexão manual ao FTP com autenticação anônima e listagem de diretório. |

## Critério de seleção

Foram removidas capturas repetidas, telas de pesquisa/configuração sem valor comprobatório direto, comandos incompletos, saídas truncadas e tentativas com erro que não acrescentavam informação necessária à narrativa do laboratório.

## Limitação importante

- As cinco imagens preservadas documentam conectividade, reconhecimento e enumeração de FTP/SMB.
- **Nenhuma das cinco imagens é uma captura da execução do Medusa.** Os resultados positivos do Medusa FTP e SMB permanecem descritos como saídas textuais compartilhadas durante o desenvolvimento.
- Se as capturas originais do Medusa forem recuperadas, elas poderão ser adicionadas após ocultar credenciais e confirmar que o conteúdo corresponde ao resultado descrito.

## Cuidados antes de publicar

Não inclua senhas, hashes, tokens, chaves privadas ou dados pessoais. Não altere capturas de modo a modificar o sentido do resultado; quando for necessário ocultar informação sensível, preserve o contexto técnico relevante.
