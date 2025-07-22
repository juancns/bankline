# Bankline API

API REST desenvolvida em Java com Spring Boot que simula operações bancárias básicas, como cadastro de correntistas e movimentações financeiras (receitas e despesas), mantendo o saldo atualizado automaticamente.

---

## 🚀 Funcionalidades

- Cadastro de correntistas com conta bancária associada
- Registro de movimentações financeiras (receitas e despesas)
- Atualização automática do saldo da conta vinculada
- Listagem de correntistas e movimentações via API REST
- Modelagem simples e eficiente utilizando DTOs e entidades JPA

---

## 🛠️ Tecnologias Utilizadas

- Java 11+
- Spring Boot
- Spring Data JPA (Hibernate)
- Banco de dados relacional (H2, PostgreSQL ou similar)
- Maven
- IDE recomendada: IntelliJ IDEA, Eclipse, VSCode

---

## 📁 Estrutura do Projeto

src/
└── main/
└── java/
└── com/
└── dio/
└── santander/
└── bankline/
└── api/
├── controller/ # Controladores REST
├── dto/ # Data Transfer Objects
├── model/ # Entidades JPA e Enums
├── repository/ # Repositórios Spring Data JPA
└── service/ # Lógica de negócio

---

## 📦 Modelos de Dados

### Correntista

| Campo  | Tipo    | Descrição                      |
|--------|---------|-------------------------------|
| id     | Integer | Identificador único            |
| nome   | String  | Nome completo do correntista  |
| cpf    | String  | CPF do correntista            |
| conta  | Conta   | Conta bancária embutida        |

### Conta (embutida em Correntista)

| Campo  | Tipo    | Descrição                      |
|--------|---------|-------------------------------|
| numero | Long    | Número da conta                |
| saldo  | Double  | Saldo atual da conta           |

### Movimentacao

| Campo     | Tipo             | Descrição                           |
|-----------|------------------|-----------------------------------|
| id        | Integer          | Identificador único                |
| dataHora  | LocalDateTime    | Data e hora da movimentação       |
| descricao | String           | Descrição da movimentação         |
| valor     | Double           | Valor (positivo para receita, negativo para despesa) |
| tipo      | MovimentacaoTipo | Tipo da movimentação (RECEITA ou DESPESAS) |
| idConta   | Integer          | ID da conta associada              |

### MovimentacaoTipo (Enum)

- `RECEITA` — entrada financeira
- `DESPESAS` — saída financeira

---

## 🔗 Endpoints da API

| Método | Endpoint         | Descrição                                  |
|--------|------------------|--------------------------------------------|
| `GET`  | /correntistas    | Lista todos os correntistas                |
| `POST` | /correntistas    | Cria um novo correntista                    |
| `GET`  | /movimentacoes   | Lista todas as movimentações                |
| `POST` | /movimentacoes   | Registra uma nova movimentação financeira   |

---

## 🧾 Exemplos de Requisições

### Criar um correntista

POST `/correntistas`

```json
{
  "nome": "João Silva",
  "cpf": "12345678901"
}
Registrar uma movimentação
POST /movimentacoes

json
Copiar
Editar
{
  "descricao": "Salário",
  "valor": 2500.00,
  "tipo": "RECEITA",
  "idConta": 1
}

⚙️ Como executar o projeto

Clone o repositório
git clone https://github.com/juancns/bankline.git
Importe o projeto em sua IDE favorita (IntelliJ, Eclipse, VSCode)

Configure o banco de dados (H2 em memória ou outro banco à sua escolha)

Execute a aplicação na classe principal:

com.dio.santander.bankline.api.BanklineApiApplication
Acesse os endpoints via Postman, curl ou seu cliente REST de preferência


🧠 Aprendizados
Desenvolvimento de API REST com Spring Boot

Modelagem de dados com JPA e entidades embutidas

Uso de DTOs para entrada de dados e validação simples

Implementação da lógica de negócio na camada de serviço

Manipulação de dados relacionais via Spring Data JPA

Atualização automática de saldo financeiro em movimentações


Desenvolvido por Juan Carlos do Nascimento da Silva
