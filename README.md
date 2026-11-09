# Laboratório de Testes de Força Bruta e Enumeração de Credenciais

## 1. Sobre o projeto

Este projeto reúne atividades práticas de Cibersegurança realizadas em
um ambiente de laboratório controlado, com foco no estudo de mecanismos
de autenticação, enumeração de usuários e análise de possíveis
vulnerabilidades relacionadas ao uso de credenciais.

Durante os desafios, foram utilizadas ferramentas de linha de comando do
Kali Linux para executar testes simulados contra serviços de rede e uma
aplicação web vulnerável disponibilizada para fins educacionais.

O objetivo foi compreender, na prática, como determinadas técnicas de
tentativa de credenciais funcionam, observar as respostas dos serviços e
registrar os resultados obtidos durante os exercícios.

> **Aviso:** todas as atividades descritas foram destinadas
> exclusivamente a um ambiente de laboratório autorizado. Os comandos e
> procedimentos não devem ser utilizados contra sistemas, contas ou
> serviços de terceiros sem autorização explícita.

## 2. Atividades realizadas

As atividades foram organizadas em três frentes principais:

-   **Testes simulados de força bruta em FTP:** realização de tentativas
    automatizadas de autenticação para observar o comportamento do
    serviço diante de diferentes combinações de usuário e senha.
-   **Testes em formulário web (DVWA):** automação de tentativas de
    autenticação em um formulário da aplicação vulnerável DVWA,
    utilizando parâmetros específicos para identificar respostas de
    falha.
-   **Password spraying em SMB e enumeração de usuários:** criação de
    uma wordlist de possíveis usuários, execução de verificações no
    serviço SMB e coleta de informações disponíveis no ambiente.

## 3. Ferramentas utilizadas

-   **Kali Linux:** sistema operacional utilizado como ambiente de
    trabalho.
-   **Medusa:** ferramenta utilizada para automatizar testes de
    autenticação nos desafios.
-   **smbclient:** ferramenta utilizada para consultar compartilhamentos
    SMB e verificar o acesso disponibilizado pelas credenciais testadas.
-   **enum4linux:** ferramenta utilizada para coletar informações e
    realizar enumeração de serviços SMB.
-   **DVWA (Damn Vulnerable Web Application):** aplicação web vulnerável
    utilizada no desafio de autenticação via formulário.
-   **Wordlists:** arquivos de texto utilizados como listas de possíveis
    nomes de usuários e senhas durante os testes.

## 4. Comandos utilizados

A seguir estão registrados os principais comandos utilizados durante a
execução dos desafios. Os endereços IP, nomes de arquivos e demais
parâmetros entre colchetes devem ser substituídos pelos valores
correspondentes ao laboratório.

### 4.1. Criação de wordlist

Foi criada uma lista de possíveis nomes de usuários para utilização no
desafio de enumeração e teste de credenciais em SMB:

``` bash
echo -e "user\nmsfadmin\nservice" > smb_users.txt
```
![Descrição da imagem](imagens/criando-wordlists.png)

Arquivo gerado: `smb_users.txt`.

### 4.2. Consulta ao serviço SMB

Foi utilizado o `smbclient` para consultar os compartilhamentos SMB
disponíveis e verificar o comportamento do acesso com as credenciais
testadas:

``` bash
smbclient -L //[IP_DO_ALVO] -U [USUARIO]
```

### 4.3. Testes automatizados com Medusa

A ferramenta Medusa foi utilizada nos desafios de autenticação, com
parâmetros adequados ao serviço ou aplicação testada.

Estrutura geral utilizada:

``` bash
medusa -h [IP_DO_ALVO] -U [ARQUIVO_DE_USUARIOS] -P [ARQUIVO_DE_SENHAS] -M [MODULO]
```

No desafio com formulário web (DVWA), também foram utilizados parâmetros
para indicar a página, os campos enviados pelo formulário, a resposta
que identificava uma tentativa malsucedida e a quantidade de threads:

``` bash
-m PAGE:'/site/pagina' \
-m FORM:'username=^USER^&password=^PASS^&Login=Login' \
-m 'FAIL=Login failed' \
-t 6
```

### 4.4. Enumeração SMB com enum4linux

Foi realizada a enumeração do serviço SMB e o resultado foi salvo em um
arquivo para consulta posterior:

``` bash
enum4linux -a [IP_DO_ALVO] | tee enum4_output.txt
```

Para consultar o conteúdo registrado:

``` bash
less enum4_output.txt
```

Arquivo gerado: `enum4_output.txt`.

## 5. Arquivos e evidências do projeto

A entrega pode ser organizada com a seguinte estrutura:

``` text
projeto/
├── README.md
├── enum4_output.txt
├── smb_password.txt
├── smb_users.txt
└── images/
    └── [capturas-de-tela-dos-desafios]
```

-   `README.md`: documentação das atividades, ferramentas e
    procedimentos realizados.
-   `smb_users.txt`: wordlist criada para o desafio de enumeração e
    testes em SMB.
-   `smb_password.txt`: wordlist criada para o desafio de enumeração e
    testes em SMB.
-   `enum4_output.txt`: saída registrada durante a enumeração com
    enum4linux.
-   `images/`: diretório opcional para capturas de tela que comprovem a
    execução dos desafios.

Inclua somente arquivos que tenham sido efetivamente utilizados ou
produzidos. Caso não tenham sido desenvolvidos scripts adicionais, não é
necessário criar a pasta `scripts/`.

## 6. Competências praticadas

Durante os exercícios, foram praticados:

-   Utilização de ferramentas de linha de comando em ambiente Linux.
-   Criação e organização de wordlists.
-   Enumeração de usuários e informações de serviços SMB.
-   Testes controlados de autenticação em FTP, SMB e aplicações web.
-   Configuração de parâmetros para automação de tentativas de
    autenticação.
-   Registro e análise de saídas de ferramentas.
-   Organização de evidências e documentação técnica.

## 7. Considerações finais

A realização dos desafios permitiu colocar em prática conceitos de
enumeração e segurança de autenticação, além de desenvolver
familiaridade com ferramentas utilizadas em atividades de análise de
segurança.

Os exercícios também reforçaram a importância de políticas de senhas
robustas, mecanismos de bloqueio ou limitação de tentativas,
monitoramento de autenticações e exposição controlada de serviços de
rede.

**Todos os testes foram realizados em ambiente de laboratório, com
finalidade educacional.**
