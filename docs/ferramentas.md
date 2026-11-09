# Ferramentas utilizadas

## Kali Linux

Distribuição Linux utilizada como estação de análise no laboratório. O Kali foi configurado no VirtualBox com o endereço `192.168.56.20`.

## Nmap

Ferramenta de reconhecimento de rede usada para verificar o host de laboratório e identificar portas e serviços disponíveis.

### Resultado já observado

No alvo `192.168.56.10`, uma saída registrada indicou:

- `21/tcp`: FTP, vsftpd 2.3.4.
- `445/tcp`: serviço SMB/Samba (smbd 3.X–4.X).

A captura ou saída integral deverá ser anexada para preservar os parâmetros exatos do comando.

## Cliente FTP

Foi estabelecida uma conexão FTP com o host de laboratório. O serviço aceitou autenticação anônima (`anonymous`). A sessão foi encerrada com o comando `bye`.

Essa observação documenta o comportamento do serviço no laboratório; não representa uma recomendação de configuração para ambientes reais.

## Medusa

Medusa é uma ferramenta de auditoria de autenticação compatível com diferentes módulos de serviço.

### Progresso confirmado

- O comando de ajuda `medusa -h` foi executado para conhecer as opções disponíveis.
- Foi iniciada a exploração da documentação e dos módulos.
- Houve preparação inicial de uma wordlist para o cenário FTP.
- Não há registro confirmado de uma execução de tentativa de autenticação com Medusa contra o serviço. Portanto, nenhum resultado de brute force deve ser declarado como concluído.

### Próximos registros

Quando houver evidência, documentar o comando usado, o significado dos parâmetros, o serviço do laboratório, o resultado observado e as medidas de contenção. Os testes devem ser limitados ao ambiente autorizado.

## Padrão para documentar comandos

Para cada comando efetivamente executado, registrar:

1. Finalidade.
2. Significado dos parâmetros.
3. Host ou serviço de laboratório utilizado.
4. Resultado observado.
5. Evidência correspondente.
6. Cuidados e limites de uso.
