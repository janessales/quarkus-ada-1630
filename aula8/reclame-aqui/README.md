# 📢 Reclame Aqui API

API REST desenvolvida com Java + Quarkus para gerenciamento de reclamações de consumidores, inspirada no modelo do Reclame Aqui.

O sistema permite cadastrar, listar, buscar, atualizar e remover reclamações, além de contar com geração automática de títulos utilizando integração com um client externo.

---

# 🚀 Tecnologias Utilizadas

* Java
* Quarkus
* Hibernate ORM com Panache
* RESTEasy Reactive
* PostgreSQL
* Maven
* JUnit 5
* Mockito
* Quarkus Test
* PanacheMock
* InjectMock

---

# 📂 Estrutura do Projeto

O projeto foi organizado seguindo boas práticas de separação de responsabilidades:

* `Resource` → camada de exposição da API REST
* `Service` → regras de negócio
* `Entity` → representação da entidade no banco
* `Infrastructure Client` → integração com API externa para geração de títulos

---

# ⚙️ Funcionalidades

## 📌 CRUD de Reclamações

A aplicação permite:

### ➕ Criar reclamação

Cadastro de uma nova reclamação contendo:

* título
* descrição
* empresa
* localidade
* demais informações necessárias

Caso o título não seja informado, o sistema gera automaticamente um título utilizando integração com API externa.

---

### 📋 Listar reclamações

Permite:

* listar todas as reclamações
* paginação dos resultados
* filtro por título ou descrição

---

### 🔎 Buscar reclamação por ID

Consulta uma reclamação específica através do ID.

---

### ✏️ Atualizar reclamação

Permite alterar os dados de uma reclamação já cadastrada.

---

### 🗑 Remover reclamação

Exclusão de uma reclamação pelo ID.

---

# 🔗 Integração Externa

## TitleGeneratorClient

Quando uma reclamação é criada sem título, a aplicação realiza uma chamada para um client externo responsável por gerar automaticamente um título.

Essa integração foi implementada utilizando:

* MicroProfile Rest Client
* `@RestClient`
* `@InjectMock` nos testes

Isso simula um cenário real de mercado com consumo de APIs externas.

---

# 🧪 Testes Automatizados

O projeto possui testes automatizados para a camada de serviço (`ReclamacaoService`), garantindo o correto funcionamento das principais regras de negócio da aplicação.

Os testes foram desenvolvidos utilizando:

* JUnit 5
* Mockito
* Quarkus Test
* PanacheMock
* InjectMock

---

# 📌 Classe de Teste

```java
ReclamacaoServiceTest
```

Essa classe valida os principais comportamentos dos métodos CRUD e também a integração com o `TitleGeneratorClient`.

---

# ✅ Cenários Testados

---

## 🔍 listar()

Valida o comportamento da listagem de reclamações com e sem filtros.

### Casos cobertos:

* retorna todas as reclamações quando o filtro é `null`
* retorna todas as reclamações quando o filtro é vazio (`""`)
* filtra corretamente por título ou descrição quando o filtro é informado
* retorna lista vazia quando não há resultados

---

## 🔎 buscar()

Valida a busca de uma reclamação por ID.

### Casos cobertos:

* retorna a reclamação quando o ID existe
* retorna `null` quando o ID não existe

---

## ➕ criar()

Valida a criação de uma nova reclamação e a geração automática de título.

### Casos cobertos:

* persiste normalmente quando o título já está preenchido
* gera título automaticamente quando o título é `null`
* gera título automaticamente quando o título está em branco
* persiste sem título quando o client retorna lista vazia
* persiste sem título quando o client retorna `null`

### Integração validada:

```java
TitleGeneratorClient
```

Foi utilizado `@InjectMock` para mockar o client externo e validar o comportamento sem depender da API real.

---

## ✏️ atualizar()

Valida a atualização de uma reclamação existente.

### Casos cobertos:

* atualiza corretamente todos os campos quando o ID existe
* retorna `null` quando a reclamação não é encontrada

---

## 🗑 deletar()

Valida a exclusão de reclamações.

### Casos cobertos:

* chama `deleteById()` com o ID correto
* não lança erro mesmo quando o ID não existe

---

# ▶️ Como Executar o Projeto

## Rodar a aplicação

```bash
./mvnw quarkus:dev
```

No Windows:

```bash
mvn quarkus:dev
```

A aplicação ficará disponível em:

```bash
http://localhost:8080
```

---

# ▶️ Como Executar os Testes

Para rodar todos os testes:

```bash
./mvnw test
```

No Windows:

```bash
mvn test
```

---

# 🎯 Objetivo dos Testes

Esses testes garantem:

* segurança para futuras alterações
* prevenção de regressões
* validação das regras de negócio
* maior confiabilidade da aplicação
* cobertura da lógica de CRUD e integração externa

Isso torna o projeto mais robusto e mais próximo de um cenário real de mercado.

---

# 💡 Diferenciais do Projeto

Este projeto demonstra:

* boas práticas com Quarkus
* uso de Panache ORM
* testes unitários robustos
* integração com API externa
* mock de dependências externas
* cobertura de cenários reais de negócio
* estrutura profissional para portfólio GitHub

---

# 👨‍💻 Projeto para Portfólio

Este projeto foi desenvolvido com foco em aprendizado prático e fortalecimento de portfólio para oportunidades na área de desenvolvimento Java Backend.

Ele demonstra conhecimentos importantes exigidos pelo mercado como:

* Java moderno
* APIs REST
* testes automatizados
* integração entre serviços
* persistência com banco de dados
* organização de código em camadas
