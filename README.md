# Mini AI-Native Dev Lab

Laboratório educacional **full stack** na sua máquina: página web, API REST, banco de dados e tudo orquestrado com Docker.

## O que você precisa

- [Docker](https://docs.docker.com/get-docker/) instalado (inclui `docker compose`).

## Como rodar

No terminal, na pasta do projeto:

```bash
docker compose up --build
```

Na primeira vez o build pode levar alguns minutos. Quando aparecer que os serviços subiram, use os endereços abaixo.

## Onde abrir no navegador

| O quê | Endereço |
|--------|----------|
| Interface (frontend) | http://localhost:8080 |
| Lista de projetos (JSON da API) | http://localhost:8000/projects |
| Documentação interativa da API (Swagger) | http://localhost:8000/docs |

## Pastas principais

- `frontend/` — HTML, CSS e JavaScript servidos pelo Nginx.
- `backend/` — API em Python (FastAPI); dados em volume Docker em `/data`.

Para parar: `Ctrl+C` no terminal onde o `docker compose` está rodando.
