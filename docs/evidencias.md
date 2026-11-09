# Evidências e resultados

Este documento acompanha o que já foi realizado e o que ainda precisa de captura ou conferência. Os resultados abaixo foram transcritos das saídas compartilhadas durante o trabalho; isso não significa que imagens dessas execuções já estejam anexadas ao repositório.

## Evidências recebidas e analisadas

- [x] Tela do VirtualBox com discos virtuais do Kali e do Metasploitable.
- [x] Interface `eth0` do Metasploitable observada ativa.
- [x] Interface `eth0` do Kali observada ativa.
- [x] Teste de conectividade: 4 pacotes enviados, 4 recebidos e 0% de perda para `192.168.56.10`.
- [x] Nmap: reconhecimento amplo do alvo `192.168.56.10`, com múltiplos serviços e portas identificados.
- [x] Nmap: FTP nas portas 21 e 2121 abertas; identificação anterior de vsftpd 2.3.4 na porta 21 e ProFTPD 1.3.1 na porta 2121.
- [x] Nmap: identificação de Samba `smbd 3.X - 4.X` nas portas 139 e 445, grupo `WORKGROUP`.
- [x] Consulta de compartilhamentos SMB com `smbclient -L`.
- [x] Captura de listagem de diretório no prompt interativo SMB.

## Testes de autenticação com Medusa

### FTP — concluído

- [x] Medusa 2.3 e módulo FTP consultados.
- [x] Wordlist de laboratório conferida (três entradas).
- [x] Validação manual de autenticação FTP do usuário de laboratório `msfadmin`.
- [x] Execução controlada do módulo FTP contra `192.168.56.10:21`, com uma tarefa simultânea.
- [x] Saída reportou `ACCOUNT FOUND: [ftp]` e `SUCCESS` para o usuário de laboratório `msfadmin`.
- [ ] Anexar uma captura sanitizada da execução FTP, se disponível.

### SMB — concluído

- [x] Módulo `smbnt` identificado (versão 3.0).
- [x] Nmap confirmou Samba nas portas 139 e 445.
- [x] Execução controlada do módulo SMBNT contra `192.168.56.10:445`, com uma tarefa simultânea.
- [x] Saída reportou `ACCOUNT FOUND: [smbnt]` e `SUCCESS (ADMIN$ - Access Allowed)` para o usuário de laboratório `msfadmin`.
- [ ] Anexar uma captura sanitizada da execução SMB, se disponível.

## Outros pontos de progresso confirmados

- [x] Máquinas virtuais configuradas no VirtualBox.
- [x] Rede Host-Only preparada.
- [x] Comunicação entre Kali (`192.168.56.20`) e Metasploitable 2 (`192.168.56.10`) testada.
- [x] Ajuda do Medusa consultada com `medusa -h`.
- [x] Módulos FTP e SMBNT consultados.
- [x] Resultados dos testes FTP e SMB interpretados e registrados neste documento.

## Pendências de documentação

- [ ] Capturar a configuração detalhada da rede Host-Only no VirtualBox.
- [ ] Registrar separadamente o contexto da tentativa SMB anterior que exibiu `NT_STATUS_LOGON_FAILURE`.
- [ ] Revisar as 19 imagens existentes e associar cada uma a uma etapa, sem inventar descrições.
- [ ] Adicionar capturas sanitizadas das execuções Medusa FTP e SMB, se disponíveis.
- [ ] Escrever a conclusão final e as recomendações defensivas.

## Padrão de registro

Para cada evidência, incluir:

- **Arquivo:** nome da captura ou registro.
- **Etapa:** fase do procedimento.
- **Descrição:** o que a imagem ou saída demonstra.
- **Resultado:** observação objetiva, sem expor credenciais.

## Privacidade e segurança

As saídas originais do Medusa exibiram senhas em texto claro. Não reproduzir essas senhas no repositório. Antes de publicar capturas, ocultar senhas, hashes, tokens, chaves e quaisquer dados pessoais que não sejam necessários para demonstrar o aprendizado.

Não incluir credenciais válidas ou dados de terceiros no repositório. Os procedimentos descritos se limitam ao laboratório próprio e autorizado.
