# Evidências e resultados

Este documento acompanha o que já foi realizado e o que ainda precisa de captura ou conferência.

## Evidências recebidas e analisadas

- [x] Tela do VirtualBox com discos virtuais do Kali e do Metasploitable.
- [x] Interface `eth0` do Metasploitable observada ativa.
- [x] Interface `eth0` do Kali observada ativa.
- [x] Teste de conectividade: 4 pacotes enviados, 4 recebidos e 0% de perda para `192.168.56.10`.
- [x] Nmap: verificação específica da porta 21 identificando FTP / vsftpd 2.3.4.
- [x] Nmap: reconhecimento amplo do alvo `192.168.56.10`, com múltiplos serviços e portas identificados.
- [x] Nmap: identificação de SMB/Samba nas portas 139 e 445.
- [x] Nmap: identificação de ProFTPD 1.3.1 na porta 2121, além de vsftpd 2.3.4 na porta 21.
- [x] Consulta de compartilhamentos SMB com `smbclient -L`.
- [x] Captura de listagem de diretório no prompt interativo SMB.

## Progresso anterior confirmado

- [x] Máquinas virtuais configuradas no VirtualBox.
- [x] Rede Host-Only preparada.
- [x] Comunicação entre Kali (`192.168.56.20`) e Metasploitable 2 (`192.168.56.10`) testada.
- [x] Conexão FTP estabelecida em etapa anterior.
- [x] Autenticação FTP anônima aceita em etapa anterior.
- [x] Ajuda do Medusa consultada com `medusa -h`.
- [x] Wordlist inicial para o cenário FTP preparada.

## Etapas ainda pendentes

- [ ] Anexar os arquivos de imagem ao repositório, se desejado, e referenciá-los neste documento.
- [ ] Capturar a configuração detalhada da rede Host-Only no VirtualBox.
- [ ] Registrar os comandos completos usados no reconhecimento amplo e na enumeração SMB.
- [ ] Registrar separadamente o contexto de cada tentativa SMB, incluindo a mensagem `NT_STATUS_LOGON_FAILURE`.
- [ ] Registrar a sessão FTP com captura própria, se disponível.
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
