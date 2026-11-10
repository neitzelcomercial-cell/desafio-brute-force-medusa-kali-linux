# DVWA — validação manual do formulário Brute Force

## Objetivo

Observar o comportamento do formulário Brute Force do Damn Vulnerable Web Application (DVWA) em ambiente de laboratório, sem confundir uma validação manual com um ataque automatizado.

## Preparação registrada

- DVWA acessível no Metasploitable 2.
- Login inicial da aplicação realizado.
- Security Level alterado de High para Low.
- Módulo **Brute Force** aberto pelo menu do DVWA.

## Observação da requisição

No Firefox, a aba Network registrou uma requisição para:

```text
GET /dvwa/vulnerabilities/brute/
```

Os parâmetros observados foram:
- `username`
- `password`
- `Login`

A requisição retornou HTTP `200 OK`. Esse status indica que a página foi entregue pelo servidor; não é, isoladamente, prova de autenticação bem-sucedida.

## Testes manuais realizados

| Usuário | Tipo de tentativa | Resultado observado |
|---|---|---|
| `admin` | Senha incorreta de teste | Mensagem de usuário e/ou senha incorretos |
| `admin` | Credencial padrão do laboratório | Mensagem de boas-vindas / acesso aceito |

As credenciais não são reproduzidas integralmente nesta página. O objetivo é registrar a diferença de comportamento entre uma tentativa inválida e uma válida.

## Limitação identificada no Medusa

A consulta `medusa -M http -q` mostrou opções de autenticação HTTP BASIC, DIGEST e NTLM, método, diretório e cabeçalhos adicionais. Isso não comprova que o módulo reconheça automaticamente campos de formulários web, mensagens de falha ou controles de sessão do DVWA.

Assim:
- O formulário foi validado manualmente.
- Não foi concluída automação de tentativas no DVWA com Medusa.
- Não se deve apresentar o teste manual como brute force automatizado.
- Uma ferramenta ou script específico para formulários web exigiria configuração e validação próprias, inclusive de sessão e dos parâmetros exatos.

## Aprendizado e mitigação

Formulários de autenticação devem implementar limitação de tentativas, monitoramento, MFA quando possível, proteção contra automação abusiva, gerenciamento seguro de sessão e mensagens de erro que não revelem informações desnecessárias.

## Escopo

Teste realizado somente no DVWA do laboratório próprio e isolado. Não aplicar os procedimentos a sistemas de terceiros sem autorização explícita.
