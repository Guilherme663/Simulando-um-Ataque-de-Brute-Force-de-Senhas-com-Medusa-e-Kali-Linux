# Laboratório de Testes de Força Bruta e Enumeração de Credenciais

## Sobre o projeto

Este projeto consiste na realização de atividades práticas de Cibersegurança em um ambiente de laboratório controlado, utilizando ferramentas do Kali Linux para explorar técnicas de autenticação, enumeração de usuários e identificação de possíveis vulnerabilidades em serviços de rede e aplicações web.

O objetivo foi compreender o funcionamento de ataques automatizados contra mecanismos de autenticação, analisar respostas dos serviços e identificar riscos relacionados ao uso de credenciais fracas.

## Atividades realizadas

Durante o laboratório, foram desenvolvidos os seguintes desafios:

- **Força bruta em FTP:** utilização do Medusa e de wordlists para realizar tentativas automatizadas de autenticação em um serviço FTP.
- **Ataques em formulário web (DVWA):** simulação de tentativas automatizadas de autenticação em uma aplicação web vulnerável, utilizando o Medusa.
- **Password Spraying em SMB:** realização de testes com credenciais e enumeração de usuários para investigar possibilidades de autenticação no serviço SMB.
- **Enumeração de usuários e compartilhamentos:** utilização do Enum4linux e SMBClient para identificar informações disponíveis no serviço SMB.
- **Criação de wordlists:** elaboração de listas personalizadas de usuários e senhas para utilização nos testes.

## Ferramentas utilizadas

- **Kali Linux:** sistema operacional utilizado para execução das ferramentas.
- **Medusa:** ferramenta para testes automatizados de autenticação.
- **Enum4linux:** ferramenta de enumeração de informações em serviços SMB.
- **SMBClient:** ferramenta para interação e verificação de compartilhamentos SMB.
- **DVWA:** aplicação web intencionalmente vulnerável utilizada no laboratório.
- **Metasploitable:** máquina virtual utilizada como ambiente de testes.

## Comandos e procedimentos utilizados

### 1. Criação de wordlists

```bash
echo -e "user\nmsfadmin\nservice" > smb_users.txt
```

Também foram criados arquivos de senhas para utilização nos testes de autenticação.

### 2. Verificação de compartilhamentos SMB

```bash
smbclient -L //IP -U usuario
```

### 3. Testes de autenticação com Medusa

Foram utilizados comandos do Medusa para os desafios envolvendo FTP e formulários web, utilizando listas personalizadas de usuários e senhas.

### 4. Enumeração SMB

```bash
enum4linux -a IP | tee enum4_output.txt
```

### 5. Consulta dos resultados

```bash
less enum4_output.txt
```

## Estrutura dos arquivos

```text
├── README.md
├── smb_users.txt
├── smb_passwords.txt
├── users.txt
├── pass.txt
├── enum4_output.txt
└── images/
    ├── ftp/
    ├── dvwa/
    └── smb/
```

*Os arquivos e diretórios representam a organização sugerida para os materiais utilizados e os registros dos testes.*

## Aprendizados

A realização das atividades proporcionou contato prático com ferramentas de segurança ofensiva, técnicas de enumeração, análise de autenticação e utilização de wordlists.

Também foram explorados conceitos relacionados a ataques de força bruta, Password Spraying e identificação de possíveis falhas em mecanismos de autenticação.

## Ambiente e autorização

Todas as atividades foram desenvolvidas com finalidade educacional, em ambiente de laboratório controlado, utilizando máquinas virtuais e aplicações destinadas ao estudo de Cibersegurança.