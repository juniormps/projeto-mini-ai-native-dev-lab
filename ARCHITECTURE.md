# Arquitetura do mini laboratório

Este projeto é um **aplicativo web em camadas** rodando na sua máquina com **Docker Compose**. A ideia é separar o que o usuário vê (interface) do que processa dados (API) e de onde os dados ficam guardados (banco).

## Visão em uma frase

O **navegador** carrega páginas estáticas em uma porta; o **JavaScript** chama a **API** em outra porta; a API lê e grava em um **SQLite** dentro de um volume Docker.

## Os três blocos

1. **Frontend (porta 8080)**  
   Arquivos HTML, CSS e JavaScript na pasta `frontend/`. Um container **Nginx** só entrega esses arquivos — não executa lógica de negócio. É o “mostrador” da aplicação.

2. **Backend (porta 8000)**  
   API em **Python** com **FastAPI** na pasta `backend/app/`. Ela expõe rotas HTTP (por exemplo `/projects` e `/health`), valida o que for necessário e devolve JSON. Na subida, inicializa o banco.

3. **Dados**  
   O banco é **SQLite** em um arquivo (`/data/lab.db` dentro do container). A pasta `/data` vem de um **volume Docker** (`lab_data`), para os dados sobreviverem a reinícios do container sem ficarem misturados com o código.

## Como o fluxo funciona

Quando você clica para carregar projetos, o **JavaScript no navegador** faz uma requisição HTTP para `http://localhost:8000/projects`. O **FastAPI** consulta o SQLite e devolve uma lista em JSON. O script monta a lista na página.

O **CORS** na API permite que a página servida em `http://localhost:8080` chame a API em outra origem (outra porta), o que o navegador exige por segurança.

## Por que Docker?

Um arquivo `docker-compose.yml` sobe os dois serviços com portas fixas e o volume de dados. Você não precisa instalar Python ou Nginx na máquina host para o laboratório funcionar — só o Docker.

## O que não está aqui (de propósito)

Não há autenticação, filas nem vários ambientes: o foco é **clareza** — front estático, API pequena e banco em arquivo — para estudar o encadeamento típico de um app full stack.
