# Gestão Comunitária Condominial

Sistema Full Stack para gestão comunitária de condomínios, desenvolvido com foco educacional utilizando FastAPI, SQLite, Docker, HTML, CSS e JavaScript.

## Sobre o Projeto

O sistema foi desenvolvido para auxiliar no gerenciamento de demandas e eventos de um condomínio, permitindo o cadastro, acompanhamento e monitoramento das atividades da comunidade condominial.

Além do controle de demandas, o sistema também recebe eventos externos e os converte automaticamente em novas demandas, simulando o comportamento de sistemas corporativos que processam informações recebidas de sensores, usuários ou serviços externos.

### Exemplo de fluxo

Evento recebido:

```json
{
  "source": "portaria",
  "type": "seguranca",
  "value": "portao_aberto",
  "created_at": "2026-06-01"
}
```

Processamento:

```text
Evento
↓
Processamento
↓
Demanda
```

Demanda gerada:

```json
{
  "title": "Verificar evento recebido",
  "category": "seguranca",
  "description": "Evento recebido de portaria",
  "status": "pendente"
}
```

---

## Funcionalidades

### Gestão de Demandas

* Cadastro de demandas
* Listagem de demandas
* Atualização de demandas
* Exclusão de demandas
* Controle de status
* Resumo estatístico

### Gestão de Eventos

* Recebimento de eventos externos
* Armazenamento em banco de dados
* Consulta de eventos recebidos
* Conversão automática de eventos em demandas

### Dashboard Web

* Interface web responsiva
* Visualização das demandas
* Visualização dos eventos
* Resumo geral das atividades

---

## Tecnologias Utilizadas

### Backend

* Python 3
* FastAPI
* SQLite
* Uvicorn

### Frontend

* HTML5
* CSS3
* JavaScript (Vanilla JS)

### Infraestrutura

* Docker
* Docker Compose
* Nginx

### Controle de Versão

* Git
* GitHub

---

## Estrutura do Projeto

```text
mini-ai-native-dev-lab/
│
├── backend/
│   ├── app/
│   │   ├── database.py
│   │   ├── main.py
│   │   ├── schemas.py
│   │   └── services.py
│   │
│   ├── Dockerfile
│   └── requirements.txt
│
├── frontend/
│   ├── index.html
│   ├── style.css
│   └── app.js
│
├── docker-compose.yml
├── AGENTS.md
├── README.md
├── .editorconfig
└── .gitignore
```

---

## Pré-requisitos

Antes de executar o projeto, instale:

* Docker
* Docker Compose

Verifique a instalação:

```bash
docker --version
docker compose version
```

---

## Como Executar

Clone o repositório:

```bash
git clone https://github.com/juniormps/projeto-mini-ai-native-dev-lab.git
```

Entre na pasta:

```bash
cd projeto-mini-ai-native-dev-lab
```

Suba os containers:

```bash
docker compose up --build
```

---

## Endereços da Aplicação

| Serviço      | URL                           |
| ------------ | ----------------------------- |
| Frontend     | http://localhost:8080         |
| API          | http://localhost:8000         |
| Demandas     | http://localhost:8000/demands |
| Eventos      | http://localhost:8000/events  |
| Resumo       | http://localhost:8000/summary |
| Swagger      | http://localhost:8000/docs    |
| Health Check | http://localhost:8000/health  |

---

## Categorias Utilizadas

O sistema foi especializado para o contexto de gestão condominial.

Categorias disponíveis:

* Manutenção
* Segurança
* Limpeza
* Administração
* Áreas Comuns
* Eventos
* Infraestrutura
* Comunidade
* Outros Assuntos

---

## API de Eventos

Exemplo de envio de evento:

```http
POST /event
```

Body:

```json
{
  "source": "portaria",
  "type": "seguranca",
  "value": "portao_aberto",
  "created_at": "2026-06-01"
}
```

Ao receber um evento, o sistema:

1. Registra o evento.
2. Armazena no banco SQLite.
3. Gera automaticamente uma nova demanda.
4. Disponibiliza os dados na interface web.

---

## Objetivos de Aprendizagem

Este projeto foi desenvolvido para praticar conceitos de:

* Desenvolvimento Full Stack
* APIs REST
* FastAPI
* Docker e Containers
* Docker Compose
* SQLite
* Integração Frontend e Backend
* Manipulação de dados com JavaScript
* Arquitetura básica de aplicações web
* Controle de versão com Git e GitHub

---

## Autor

**Márcio Pereira da Silva Junior**

Estudante de Análise e Desenvolvimento de Sistemas.

GitHub:
https://github.com/juniormps
