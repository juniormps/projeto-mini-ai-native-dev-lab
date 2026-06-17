# Arquitetura da Gestão Comunitária Condominial

## Visão Geral

A Gestão Comunitária Condominial é uma aplicação web full stack desenvolvida para fins educacionais na disciplina de Projeto de Extensão em Software Full Stack.

O sistema permite registrar e acompanhar demandas da comunidade condominial, receber eventos externos e apresentar indicadores resumidos para apoio à gestão.

A solução foi construída utilizando frontend em HTML, CSS e JavaScript, backend em FastAPI, banco de dados SQLite e conteinerização com Docker.

---

## Arquitetura Geral

A aplicação é dividida em quatro camadas principais:

```text
Frontend (HTML, CSS, JavaScript)
            │
            ▼
      API REST (FastAPI)
            │
            ▼
     Banco de Dados (SQLite)
            │
            ▼
      Volume Docker (/data)
```

---

## Frontend

O frontend é responsável pela interface utilizada pelos moradores, administradores ou responsáveis pela gestão comunitária.

### Funcionalidades

* Cadastro de demandas
* Listagem de demandas
* Exclusão de demandas
* Visualização de resumo por status
* Listagem de eventos recebidos
* Integração com a API através de requisições HTTP (Fetch API)

### Tecnologias

* HTML5
* CSS3
* JavaScript (Vanilla JS)

---

## Backend

O backend foi desenvolvido utilizando FastAPI.

Ele é responsável por:

* Receber requisições do frontend
* Processar regras de negócio
* Manipular o banco de dados
* Registrar eventos
* Converter eventos em demandas
* Disponibilizar dados através de uma API REST

### Principais Rotas

#### Saúde da aplicação

```http
GET /health
```

Retorna o status da API.

---

#### Demandas

```http
GET /demands
POST /demands
PUT /demands/{id}
DELETE /demands/{id}
```

Permitem consultar e gerenciar demandas.

---

#### Resumo

```http
GET /summary
```

Retorna indicadores resumidos das demandas cadastradas.

---

#### Eventos

```http
GET /events
POST /event
```

Permitem registrar e consultar eventos recebidos pelo sistema.

Ao receber um evento, o sistema cria automaticamente uma nova demanda relacionada.

---

## Banco de Dados

O banco de dados utilizado é o SQLite.

Os dados são armazenados em:

```text
/data/lab.db
```

### Tabela demands

Armazena as demandas cadastradas.

Campos:

* id
* title
* category
* description
* status
* owner
* created_at

### Tabela events

Armazena os eventos recebidos.

Campos:

* id
* source
* type
* value
* created_at

---

## Fluxo Evento → Demanda

Um dos objetivos pedagógicos do projeto é demonstrar uma arquitetura comum em sistemas reais.

Fluxo:

```text
Evento Recebido
       │
       ▼
Processamento
       │
       ▼
Criação Automática de Demanda
       │
       ▼
Persistência no Banco
```

Exemplo:

Evento recebido:

```json
{
  "source": "portaria",
  "type": "segurança",
  "value": "portão aberto"
}
```

Demanda gerada:

```json
{
  "title": "Verificar evento recebido",
  "category": "segurança",
  "description": "Evento recebido de portaria",
  "status": "pendente"
}
```

---

## Infraestrutura

O ambiente é executado localmente através do Docker Compose.

### Containers

#### Backend

* FastAPI
* Uvicorn
* Porta 8000

#### Frontend

* Nginx
* Porta 8080

#### Volume Persistente

```text
lab_data
```

Responsável por armazenar o banco SQLite mesmo após reinicializações dos containers.

---

## Estrutura do Projeto

```text
backend/
├── app/
│   ├── database.py
│   ├── main.py
│   ├── schemas.py
│   └── services.py

frontend/
├── index.html
├── style.css
└── app.js

docker-compose.yml
README.md
ARCHITECTURE.md
AGENTS.md
```

---

## Tecnologias Utilizadas

* Python
* FastAPI
* SQLite
* HTML5
* CSS3
* JavaScript
* Docker
* Docker Compose
* Git
* GitHub

---

## Papel da Inteligência Artificial

A IA é utilizada como ferramenta de apoio ao desenvolvimento e aprendizado.

Ela auxilia em atividades como:

* Explicação de conceitos
* Revisão de código
* Sugestões de melhorias
* Documentação
* Apoio na resolução de problemas

Todas as decisões de implementação permanecem sob responsabilidade do desenvolvedor.

---

## Objetivo Acadêmico

Este projeto tem como finalidade consolidar conhecimentos em:

* Desenvolvimento Full Stack
* APIs REST
* Banco de Dados
* Docker
* Git e GitHub
* Arquitetura de Software
* Integração entre sistemas
* Uso de Inteligência Artificial no desenvolvimento de software

```
```
