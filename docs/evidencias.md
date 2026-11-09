# Evidências e resultados

Este documento separa as capturas efetivamente versionadas dos resultados de execução registrados durante o desenvolvimento. A existência de um resultado descrito aqui não significa que sua captura específica esteja disponível no repositório.

## Inventário das capturas

Após a revisão visual das 17 imagens originais, foram mantidas **5 capturas relevantes**. Os nomes e números originais foram preservados para manter a rastreabilidade. Consulte o [índice das evidências](../evidencias/README.md).

As cinco imagens documentam:
- conectividade entre Kali e Metasploitable 2 e verificação inicial do FTP;
- consulta de compartilhamentos SMB;
- identificação das versões dos serviços FTP e SMB;
- verificação de FTP anônimo por Nmap e conexão manual.

## Resultados registrados durante o trabalho

### Preparação e conectividade

- [x] Kali Linux e Metasploitable 2 preparados no VirtualBox.
- [x] Rede privada Host-Only registrada.
- [x] Endereços registrados: Kali `192.168.56.20` e alvo `192.168.56.10`.
- [x] Teste de conectividade documentado: 4 pacotes enviados, 4 recebidos e 0% de perda.

### Reconhecimento e enumeração

- [x] Reconhecimento do host `192.168.56.10` com Nmap documentado.
- [x] FTP identificado na porta 21 (vsftpd 2.3.4, conforme saída registrada).
- [x] FTP identificado na porta 2121 (ProFTPD 1.3.1, conforme saída registrada).
- [x] SMB/Samba identificado nas portas 139 e 445.
- [x] Consulta de compartilhamentos com `smbclient` documentada.
- [x] Login FTP anônimo documentado como permitido nas verificações registradas.

### Testes controlados com Medusa

**FTP — resultado registrado**

O comando documentado em [Ferramentas utilizadas](ferramentas.md) direcionou o módulo FTP do Medusa ao host de laboratório na porta 21, usando uma lista local de candidatos, uma tarefa simultânea e interrupção após encontrar uma conta válida. A saída compartilhada reportou `ACCOUNT FOUND: [ftp]` e `[SUCCESS]` para o usuário de laboratório `msfadmin`.

- [x] Comando e parâmetros descritos.
- [x] Resultado reportado transcrito sem divulgar a senha.
- [ ] Captura específica da execução ainda não incluída.

**SMB — resultado registrado**

O comando documentado em [Ferramentas utilizadas](ferramentas.md) direcionou o módulo `smbnt` do Medusa ao host de laboratório na porta 445. A saída compartilhada reportou `ACCOUNT FOUND: [smbnt]` e `SUCCESS (ADMIN$ - Access Allowed)` para o usuário de laboratório `msfadmin`.

- [x] Comando e parâmetros descritos.
- [x] Resultado reportado transcrito sem divulgar a senha.
- [ ] Captura específica da execução ainda não incluída.

## Pendências antes da entrega

- [ ] Confirmar se as capturas específicas do Medusa FTP e SMB podem ser recuperadas.
- [ ] Conferir os requisitos exatos do desafio/plataforma de avaliação.
- [ ] Revisar ortografia, links internos e visualização do README no GitHub.

## Como registrar uma nova evidência

Para cada nova captura, registrar:

1. **Arquivo:** nome exato do arquivo versionado.
2. **Etapa:** fase do laboratório a que pertence.
3. **Objetivo:** o que se pretendia verificar.
4. **Observação:** o que a captura efetivamente demonstra.
5. **Resultado:** saída observada, sem inferências não comprovadas.
6. **Proteção:** confirmar que não há senhas, hashes, tokens ou dados pessoais expostos.

## Nota de segurança

As saídas originais do Medusa podem exibir senhas em texto claro. Não as reproduza em documentação, commits ou imagens públicas. Mantenha os testes restritos ao laboratório próprio e autorizado.
