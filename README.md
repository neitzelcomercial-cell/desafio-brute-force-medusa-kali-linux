# Desafio: Auditoria de autenticação com Medusa no Kali Linux

Projeto prático de cibersegurança que documenta um laboratório controlado para estudar autenticação de serviços de rede e auditoria de senhas com Kali Linux, Medusa e Metasploitable 2.

> **Escopo autorizado:** todos os procedimentos descritos foram direcionados ao laboratório privado do projeto. Não execute testes de autenticação contra sistemas, serviços ou contas de terceiros sem autorização explícita.

## Objetivos

- Preparar e descrever um laboratório isolado.
- Identificar serviços de rede com Nmap.
- Compreender a enumeração básica de FTP e SMB.
- Registrar testes controlados de autenticação com Medusa.
- Interpretar resultados e propor medidas defensivas.
- Manter evidências organizadas sem publicar senhas ou outros segredos.

## Ambiente e ferramentas

| Componente | Registro do projeto |
|---|---|
| Virtualização | Oracle VirtualBox |
| Estação de análise | Kali Linux — `192.168.56.20` |
| Alvo de laboratório | Metasploitable 2 — `192.168.56.10` |
| Rede | Host-Only |
| Auditoria de serviços | Nmap |
| Testes controlados de autenticação | Medusa 2.3 |
| Clientes de serviço | smbclient e cliente FTP |

## Resultados registrados

Os registros de execução compartilhados durante o desenvolvimento indicam resultados positivos do Medusa para a conta de laboratório `msfadmin`:

| Serviço | Destino | Resultado registrado |
|---|---|---|
| FTP | `192.168.56.10:21` | Medusa reportou `ACCOUNT FOUND` e `SUCCESS` |
| SMB/SMBNT | `192.168.56.10:445` | Medusa reportou `ACCOUNT FOUND` e `ADMIN$ - Access Allowed` |

Esses resultados descrevem as saídas observadas no laboratório. Não representam validação em outros ambientes. Senhas foram deliberadamente omitidas.

## Estrutura do repositório

| Caminho | Descrição |
|---|---|
| `README.md` | Visão geral, escopo e estado do projeto |
| `docs/ambiente-laboratorio.md` | Máquinas virtuais, rede e serviços identificados |
| `docs/ferramentas.md` | Ferramentas, comandos, parâmetros e interpretação |
| `docs/evidencias.md` | Matriz de evidências, resultados e pendências |
| `evidencias/` | Capturas de tela numeradas e índice |

## Estado da documentação

- [x] Repositório e documentação inicial criados.
- [x] Ambiente Kali/Metasploitable e endereços registrados.
- [x] Conectividade entre as máquinas documentada.
- [x] Reconhecimento de serviços com Nmap documentado.
- [x] Enumeração FTP e SMB documentada.
- [x] Resultados reportados dos testes Medusa FTP e SMB registrados.
- [x] 17 capturas preservadas e listadas no índice de evidências.
- [ ] Anexar capturas específicas das execuções Medusa FTP e SMB, se ainda disponíveis.
- [ ] Conferir visualmente cada imagem e remover qualquer dado sensível que eventualmente apareça.
- [ ] Fazer a revisão final das exigências específicas da plataforma/atividade antes da submissão.

## Documentação complementar

Comece por [Ambiente de laboratório](docs/ambiente-laboratorio.md), consulte [Ferramentas utilizadas](docs/ferramentas.md) e depois [Evidências e resultados](docs/evidencias.md). O índice das capturas está em [evidencias/README.md](evidencias/README.md).

## Conclusão

O projeto registra um fluxo de laboratório que vai da preparação da rede e identificação de serviços à análise controlada de autenticação em FTP e SMB. A principal lição defensiva é que serviços expostos, credenciais fracas e compartilhamentos administrativos acessíveis ampliam a superfície de ataque. Em ambientes reais, devem ser adotadas senhas fortes e únicas, limitação e monitoramento de tentativas, segmentação de rede, controle de privilégios e desativação de serviços legados desnecessários.

## Uso responsável

Use estas técnicas somente em laboratório próprio ou em sistemas com autorização explícita. Não publique senhas, hashes, tokens, chaves privadas ou dados pessoais nas evidências.
