# Desafio: Brute Force com Medusa no Kali Linux

Projeto prático de cibersegurança desenvolvido para documentar, de forma didática e reproduzível, o estudo de autenticação e auditoria de senhas com Kali Linux e Medusa.

> **Uso autorizado:** todas as atividades práticas devem ocorrer exclusivamente em laboratório próprio ou em sistemas para os quais exista autorização explícita. Não utilize estas técnicas contra serviços ou contas de terceiros.

## Objetivos

- Compreender os conceitos de autenticação, serviços de rede e auditoria de senhas.
- Registrar a preparação do laboratório e as ferramentas utilizadas.
- Documentar os procedimentos, resultados e aprendizados com evidências.
- Apresentar o desafio de forma organizada para avaliação e consulta futura.

## Ferramentas e ambiente

- Kali Linux
- Medusa 2.3
- Nmap
- Metasploitable 2 em rede Host-Only

## Resultados práticos

Os testes realizados no laboratório reportaram autenticação válida para o usuário de laboratório `msfadmin` nos seguintes serviços:

| Serviço | Alvo | Resultado reportado |
|---|---|---|
| FTP | `192.168.56.10:21` | Medusa reportou `ACCOUNT FOUND` / `SUCCESS` |
| SMB | `192.168.56.10:445` | Medusa reportou `ACCOUNT FOUND` / `ADMIN$ - Access Allowed` |

As senhas foram omitidas da documentação. Consulte `docs/ferramentas.md` para os comandos, explicação dos parâmetros e interpretação dos resultados, e `docs/evidencias.md` para o acompanhamento das evidências e pendências.

## Estrutura da documentação

| Caminho | Conteúdo |
|---|---|
| `docs/ambiente-laboratorio.md` | Topologia, máquinas, endereços e configuração do laboratório |
| `docs/ferramentas.md` | Conceitos, comandos e resultados das ferramentas |
| `docs/evidencias.md` | Capturas, resultados e observações |
| `evidencias/` | Capturas preservadas e organizadas cronologicamente |

## Estado do projeto

- [x] Repositório e estrutura inicial criados.
- [x] Ambiente de laboratório e conectividade documentados.
- [x] Reconhecimento de serviços FTP e SMB realizado.
- [x] Teste controlado do Medusa no FTP concluído.
- [x] Teste controlado do Medusa no SMB concluído.
- [x] Resultados documentados sem reproduzir senhas.
- [ ] Anexar capturas sanitizadas das execuções, se disponíveis.
- [ ] Revisar e legendar as evidências existentes.
- [ ] Revisar a documentação final para entrega.

## Contexto acadêmico

Projeto de estudo associado ao desafio prático de cibersegurança da DIO.
