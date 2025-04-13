# 🍊 Orange Robot Selenium

[![Python](https://img.shields.io/badge/Python-3.12.3-blue.svg)](https://www.python.org/)
[![Robot Framework](https://img.shields.io/badge/Robot_Framework-7.2.2-green.svg)](https://robotframework.org/)
[![Selenium](https://img.shields.io/badge/Selenium-6.7.1-red.svg)](https://www.selenium.dev/)

Projeto de automação de testes WEB para o [OrangeHRM](https://opensource-demo.orangehrmlive.com/) utilizando Robot Framework com abordagem BDD.

## 📌 Índice

- [Visão Geral](#-visão-geral)
- [Pré-requisitos](#-pré-requisitos)
- [Instalação](#-instalação)
- [Estrutura do Projeto](#-estrutura-do-projeto)
- [Executando Testes](#-executando-testes)
- [Relatórios](#-relatórios)
- [Gherkin/BDD](#-gherkinbdd)
- [CI/CD](#-cicd)
- [Contribuição](#-contribuição)

## 🌟 Visão Geral

Automação de testes funcionais para o sistema OrangeHRM com:

✔️ Cenários escritos em Gherkin  
✔️ Geração de relatórios HTML detalhados  
✔️ Integração com pipelines CI/CD  
✔️ Padrão Page Objects  

**Tecnologias principais:**
- 🐍 Python 3.12.3
- 🤖 Robot Framework 7.2.2
- 🌐  SeleniumLibrary 6.7.1
- 🥒 Cucumber Reporting

## 🛠️ Pré-requisitos

Antes de começar, verifique se possui instalado:

- Python 3.12+
- Pip (gerenciador de pacotes)
- Navegador Chrome/Firefox (com drivers)
- Git (para controle de versão)

## 🔧 Instalação

1. Clone o repositório:
```bash
git clone https://github.com/seu-usuario/orange-robot-selenium.git
```

2. Acesse o diretório do projeto:
```
cd orange-robot-selenium
```

3. Instale as dependências:
```
pip install -r requirements.txt
```

## 📂 Estrutura do Projeto

```
orange-robot-selenium/
├── src/
│   ├── resources/
│   │   ├── features/       # Arquivos .feature
│   │   └── data/           # Dados de teste
│   ├── pages/              # Page Objects
│   └── steps/              # Definições de steps
├── reports/                # Relatórios gerados
├── requirements.txt        # Dependências
└── README.md               # Documentação
```

## ▶️ Executando Testes

Executar todos os testes:
```
robot -d ./reports -i smoke tests/
```
Executar por tag:
```
robot -d ./reports -i login tests/suites/login.robot
```

Executar em modo headless:
```
robot -v HEADLESS:True -d ./reports tests/
```

## 📊 Relatórios
Após execução, acesse:

```reports/log.html ```- Relatório detalhado

```reports/report.html``` - Sumário executivo

## Exemplo de Relatório

## 📝 Gherkin/BDD
Exemplo de cenário:

```
gherkin

Funcionalidade: Login no sistema

  Cenário: Login com credenciais válidas
    Dado que estou na página de login
    Quando preencho o usuário "Admin" e senha "admin123"
    E clico no botão de login
    Então devo ver o dashboard principal
```
|**Palavras-chave:** |  |  
|--------------------|--|  
|**Dado** | Pré-condições |  
|**Quando** | Ações do usuário|  
|**Então** | Verificações|  
|**E** | Continuidade de passos|  

## 🔄 CI/CD
Exemplo para .gitlab-ci.yml:
```
yaml
stages:
  - test

robot-tests:
  stage: test
  script:
    - pip install -r requirements.txt
    - robot -d reports -i regression tests/
  artifacts:
    paths:
      - reports/
    expire_in: 1 week
```

Variáveis de ambiente:
```
BASE_URL=https://opensource-demo.orangehrmlive.com/
BROWSER=chrome
```

## 🤝 Contribuição
1. Faça um Fork do projeto

2. Crie uma Branch (git checkout -b feature/nova-funcionalidade)

3. Commit suas mudanças (git commit -m 'Adiciona nova feature')

4. Push para a Branch (git push origin feature/nova-funcionalidade)

5. Abra um Pull Request
