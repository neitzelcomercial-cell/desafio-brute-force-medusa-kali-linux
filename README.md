# Desafio DIO: auditoria de autenticação com Kali Linux e Medusa

Projeto educacional de cibersegurança desenvolvido em laboratório virtual controlado, como atividade prática da DIO. O objetivo é compreender tentativas de autenticação em serviços de rede, analisar respostas de aplicações e registrar medidas de prevenção.

> **Uso autorizado:** os testes descritos foram realizados em máquinas virtuais próprias, em rede Host-Only. Não execute técnicas de tentativa de senha em sistemas ou contas de terceiros sem autorização explícita.

## Objetivos

- Preparar um laboratório com Kali Linux e Metasploitable 2.
- Verificar conectividade e identificar serviços com Nmap.
- Estudar autenticação FTP e SMB com Medusa.
- Observar o comportamento de um formulário web vulnerável no DVWA.
- Distinguir brute force, password spraying e validação manual.
- Documentar resultados, limitações e recomendações defensivas.

## Ambiente utilizado

| Componente | Configuração registrada |
|---|---|
| Virtualização | Oracle VirtualBox |
| Estação de análise | Kali Linux — `192.168.56.10` |
| Alvo | Metasploitable 2 — `192.168.56.101` |
| Rede | Host-Only |
| Aplicação web | DVWA hospedado no ambiente de laboratório |
| Ferramentas | Medusa 2.3, Nmap, smbclient, Firefox/DevTools |

**Nota histórica sobre os endereços:** os primeiros registros e comandos de Medusa foram feitos quando a documentação identificava Kali como `192.168.56.20` e Metasploitable como `192.168.56.10`. Posteriormente, a configuração confirmada passou a ser Kali `192.168.56.10` e Metasploitable `192.168.56.101`. Por isso, os comandos históricos de FTP/SMB abaixo mantêm o endereço que constava no momento do teste; não se deve interpretar esse endereço como o IP atual do alvo.

## Resultados e escopo

### Ambiente e reconhecimento

- Conectividade entre as VMs confirmada por ping.
- Rede Host-Only utilizada para manter o laboratório isolado.
- Nmap utilizado para identificar serviços FTP e SMB no Metasploitable 2.
- Compartilhamentos SMB consultados com `smbclient`.

### Medusa — FTP e SMB

Os registros de execução compartilhados durante o desenvolvimento indicaram:

| Serviço | Módulo | Resultado registrado |
|---|---|---|
| FTP | `ftp` | Medusa reportou `ACCOUNT FOUND` e `SUCCESS` para a conta de laboratório `msfadmin`. |
| SMB | `smbnt` | Medusa reportou `ACCOUNT FOUND` e `SUCCESS (ADMIN$ - Access Allowed)` para a conta de laboratório `msfadmin`. |

Os comandos históricos e a interpretação dos resultados estão em [Ferramentas utilizadas](docs/ferramentas.md). As saídas originais continham credenciais em texto claro, omitidas desta documentação.

**Limite de classificação:** o teste SMB registrado utilizou um usuário e uma lista de senhas. Isso caracteriza tentativa de senhas contra uma conta, não demonstra por si só password spraying. A enumeração de compartilhamentos com `smbclient` também não equivale à enumeração de usuários. O projeto não afirma que essas duas etapas específicas do cenário corporativo foram concluídas.

### DVWA — formulário Brute Force

O módulo Brute Force do DVWA foi testado manualmente com a segurança configurada como Low:

| Usuário | Senha de teste | Resultado observado |
|---|---|---|
| `admin` | senha incorreta de teste | A aplicação informou credenciais incorretas. |
| `admin` | credencial padrão do laboratório | A aplicação exibiu a mensagem de boas-vindas. |

No DevTools/Network, a requisição do módulo Brute Force foi observada como **GET**, com os campos `username`, `password` e `Login`, e resposta HTTP `200 OK`. O código 200 indica que a página respondeu; a validação do login foi feita pela mensagem exibida pela aplicação.

**Importante:** esses foram testes manuais. Não foi concluída uma execução automatizada de brute force contra o formulário DVWA. A consulta `medusa -M http -q` mostrou que o módulo HTTP disponível documenta autenticação BASIC, DIGEST e NTLM, além de método e cabeçalhos; isso não comprova suporte direto ao formulário web do DVWA. A análise está em [DVWA — formulário web](docs/dvwa-formulario-web.md).

## Estrutura do repositório

| Caminho | Conteúdo |
|---|---|
| `README.md` | Visão geral, escopo e resultados |
| `docs/ambiente-laboratorio.md` | Máquinas virtuais, rede e serviços |
| `docs/ferramentas.md` | Ferramentas, comandos históricos e interpretação |
| `docs/dvwa-formulario-web.md` | Teste manual do DVWA e limitação do módulo HTTP |
| `docs/evidencias.md` | Inventário e limites das evidências |
| `evidencias/` | Capturas selecionadas e índice |

## Evidências

Cinco capturas foram preservadas para documentar conectividade, reconhecimento e enumeração FTP/SMB. Elas não incluem capturas específicas das execuções do Medusa nem do teste manual do DVWA. Os resultados dessas etapas são descritos como registros textuais compartilhados durante o desenvolvimento, não como imagens versionadas. Consulte [Evidências e resultados](docs/evidencias.md).

## Recomendações de mitigação

- Utilizar senhas longas, únicas e armazenadas em gerenciador de senhas.
- Implementar MFA para contas e serviços críticos.
- Aplicar limitação progressiva de tentativas, detecção de anomalias e alertas.
- Monitorar falhas de autenticação e correlacionar eventos em logs centralizados.
- Desabilitar FTP sem proteção e preferir SFTP ou FTPS.
- Desabilitar SMBv1, restringir compartilhamentos administrativos e limitar acesso por firewall e segmentação.
- Em aplicações web, aplicar rate limiting, proteção contra automação abusiva, MFA quando aplicável e controles de sessão adequados.

## Conclusão

O laboratório permitiu estudar reconhecimento de serviços, autenticação em FTP e SMB, interpretação de resultados do Medusa e comportamento de um formulário vulnerável no DVWA. Também evidenciou a importância de conhecer os limites de cada módulo: suporte HTTP genérico não significa suporte automático a qualquer formulário web. Os cenários não automatizados ou não comprovados foram identificados explicitamente, preservando a precisão técnica do relatório.

## Uso responsável

Todo o conteúdo é destinado a estudo em laboratório próprio e isolado ou a sistemas com autorização explícita. Não publique senhas, hashes, cookies, tokens ou dados pessoais.
