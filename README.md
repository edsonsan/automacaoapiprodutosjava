# 🚀 Automação de Testes REST com Java

[![Java](https://img.shields.io/badge/java-21-orange.svg)](https://www.oracle.org/)
[![RestAssured](https://img.shields.io/badge/RestAssured-5.4.0-brightgreen.svg)](https://rest-assured.io/)
[![JUnit](https://img.shields.io/badge/JUnit-5.9.3-blue.svg)](https://junit.org/junit5/)
[![Maven](https://img.shields.io/badge/Maven-3.9.6-red.svg)](https://maven.apache.org/)
[![GitHub License](https://img.shields.io/badge/license-MIT-lightgrey.svg)](LICENSE)

Projeto de automação de testes para APIs REST utilizando Java e bibliotecas modernas como RestAssured e JUnit 5.

## 📌 Features

- Testes de API REST automatizados
- Suporte a autenticação (OAuth2, JWT, Basic Auth)
- Validação de schemas JSON com JsonSchemaValidator
- Geração de relatórios Allure
- Integração contínua (CI) com GitHub Actions
- Design Pattern: Page Objects para APIs

## 🛠️ Tecnologias

- **Java 21** (LTS)
- **RestAssured** (Para chamadas HTTP)
- **JUnit 5** (Framework de testes)
- **Maven** (Gerenciamento de dependências)
- **Allure Report** (Relatórios de testes)
- **Lombok** (Redução de boilerplate code)
- **Faker** (Geração de dados fictícios)

## ⚙️ Pré-requisitos

- JDK 21 ([Download](https://www.oracle.com/java/technologies/downloads/))
- Maven 3.9.6+
- IDE (IntelliJ, Eclipse ou VS Code)

## 🚀 Como Executar

### Clonar o projeto
```bash
git clone https://github.com/seu-usuario/automacao-java-rest.git
cd automacao-java-rest
```
## Executar testes
```mvn test```

## Gerar relatório Allure
```mvn allure:report```  
```mvn allure:serve```  

## 📦 Estrutura do Projeto
```plaintext
src/
├── main/
│   └── java/
│       └── core/
│           ├── config/       # Configurações do RestAssured
│           ├── utils/        # Utilitários (Helpers, Faker)
│           └── models/       # POJOs para requisições/respostas
└── test/
    └── java/
        ├── specs/            # Especificações de API (Endpoints)
        ├── tests/            # Classes de teste
        └── resources/
            ├── schemas/      # JSON Schemas para validação
            └── testdata/     # Dados de teste (JSON, YAML)
```

## 📝 Exemplo de Teste
```java	
import static io.restassured.RestAssured.*;  
import static org.hamcrest.Matchers.*;  

@Test
@DisplayName("GET /users - Deve retornar lista de usuários")
void testGetUsers() {
    given()
        .baseUri("https://api.example.com")
        .auth().basic("user", "pass")
    .when()
        .get("/users")
    .then()
        .statusCode(200)
        .body("size()", greaterThan(0))
        .body("[0].email", containsString("@"));
}
```	
### 🔧 Configuração Avançada
rest-config.properties

```properties
base.url=https://api.example.com
base.path=/api/v1
timeout=5000
```
### pom.xml (Dependências principais)

```xml
<dependencies>
    <dependency>
        <groupId>io.rest-assured</groupId>
        <artifactId>rest-assured</artifactId>
        <version>5.4.0</version>
    </dependency>
    <dependency>
        <groupId>org.junit.jupiter</groupId>
        <artifactId>junit-jupiter</artifactId>
        <version>5.9.3</version>
    </dependency>
    <dependency>
        <groupId>io.qameta.allure</groupId>
        <artifactId>allure-junit5</artifactId>
        <version>2.24.0</version>
    </dependency>
</dependencies>
```





