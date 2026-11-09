# Evidências e resultados

Este documento acompanha o que já foi realizado e o que ainda precisa de captura ou conferência.

## Progresso confirmado

- [x] Máquinas virtuais configuradas no VirtualBox.
- [x] Rede Host-Only preparada.
- [x] Comunicação entre Kali (`192.168.56.20`) e Metasploitable 2 (`192.168.56.10`) testada.
- [x] Reconhecimento com Nmap realizado.
- [x] FTP (porta 21) e SMB (porta 445) identificados.
- [x] Conexão FTP estabelecida.
- [x] Autenticação FTP anônima aceita.
- [x] Ajuda do Medusa consultada com `medusa -h`.
- [x] Wordlist inicial para o cenário FTP preparada.

## Etapas ainda pendentes

- [ ] Anexar captura da configuração de rede no VirtualBox.
- [ ] Anexar a saída completa do Nmap.
- [ ] Conferir a referência a ProFTPD 1.3.1 na evidência original.
- [ ] Registrar a inspeção dos módulos do Medusa, se concluída.
- [ ] Registrar eventual teste controlado do Medusa somente após sua execução e validação.
- [ ] Escrever a análise final e as recomendações defensivas.

## Padrão de registro

Para cada evidência, incluir:

- **Arquivo:** nome da captura ou registro.
- **Etapa:** fase do procedimento.
- **Descrição:** o que a imagem ou saída demonstra.
- **Resultado:** observação objetiva, sem expor credenciais reais.

## Privacidade e segurança

Antes de publicar capturas, ocultar senhas, tokens, chaves e quaisquer dados pessoais que não sejam necessários para demonstrar o aprendizado.

Não incluir credenciais válidas ou dados de terceiros no repositório.
