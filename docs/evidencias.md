# Evidências e resultados

Este documento diferencia capturas efetivamente versionadas de observações e saídas textuais registradas durante o desenvolvimento.

## Capturas preservadas

Foram mantidas cinco capturas relevantes. Consulte o [índice de evidências](../evidencias/README.md).

Elas documentam:
- conectividade e verificação inicial do FTP;
- consulta de compartilhamentos SMB;
- identificação de serviços FTP e SMB;
- verificação de FTP anônimo;
- conexão manual ao FTP.

## Resultados textuais registrados

### Ambiente e reconhecimento

- [x] Kali Linux e Metasploitable 2 preparados no VirtualBox.
- [x] Rede Host-Only utilizada.
- [x] Comunicação entre as VMs confirmada.
- [x] Reconhecimento de serviços com Nmap realizado.
- [x] Consulta de compartilhamentos SMB realizada.

### Medusa FTP e SMB

As saídas compartilhadas durante o desenvolvimento reportaram resultados positivos para FTP e SMB. Os comandos históricos estão descritos em [Ferramentas utilizadas](ferramentas.md).

- [x] Comandos e parâmetros históricos documentados.
- [x] Resultados reportados transcritos sem divulgar senhas.
- [ ] Capturas específicas das execuções do Medusa não estão no repositório.

**Nota sobre endereços:** os comandos históricos apontam para `192.168.56.10`, endereço que na configuração inicial correspondia ao Metasploitable. Na configuração posterior confirmada, Kali passou a usar `192.168.56.10` e Metasploitable `192.168.56.101`. A diferença está explicitada para não confundir o endereço histórico com o atual.

**Nota sobre SMB:** o teste registrado com Medusa utilizou um usuário e uma lista de senhas. Portanto, ele não deve ser chamado de password spraying. A enumeração de compartilhamentos via smbclient também não é enumeração de usuários.

### DVWA

- [x] Login inicial e acesso ao DVWA realizados.
- [x] Security Level configurado como Low.
- [x] Teste manual com credencial inválida observado.
- [x] Teste manual com credencial padrão observado como válido.
- [x] Requisição GET e nomes dos parâmetros observados no DevTools/Network.
- [ ] Automação de brute force no formulário web não foi concluída.
- [ ] Capturas específicas do DVWA não estão no repositório.

Consulte [DVWA — formulário Brute Force](dvwa-formulario-web.md) para detalhes e limitações.

## Limites das evidências

A documentação descreve somente o que foi observado ou reportado durante o desenvolvimento. Uma saída textual relatada não é equivalente a uma captura de tela versionada. Não foram criadas evidências fictícias nem atribuídos resultados não observados.

## Cuidados antes de publicar

Não incluir senhas, hashes, cookies, tokens, chaves privadas ou dados pessoais. Se novas capturas forem adicionadas, ocultar segredos sem alterar o significado técnico do resultado.
