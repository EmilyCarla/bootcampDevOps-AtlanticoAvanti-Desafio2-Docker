# 🚀 Desafio 2: Dockerização do Gerador de Saudações  
### Bootcamp DevOps – Atlântico Avanti

Este repositório contém a solução do desafio do módulo de Docker do Bootcamp Atlântico Avanti.  
O objetivo foi construir imagens Docker otimizadas, publicá-las no Docker Hub e orquestrar uma arquitetura de microsserviços utilizando Docker Compose.

---

# 📋 Contexto do Desafio

A aplicação **Gerador de Saudações** é composta por três componentes que trabalham de forma integrada:

- **Frontend (Página Principal)** → Interface HTML que consome as APIs.
- **Microsserviço de Pessoas** → Fornece nomes aleatórios.
- **Microsserviço de Saudações** → Fornece frases aleatórias.

A missão incluiu:

- Criação de `Dockerfiles` otimizados
- Build das imagens
- Publicação no Docker Hub
- Orquestração completa com Docker Compose

---

# 🏗️ Arquitetura e Tecnologias

A aplicação segue uma arquitetura de microsserviços conectados por uma rede Docker interna chamada `backend`.

## 🔧 Tecnologias Utilizadas

| Componente | Tecnologia | Descrição |
|------------|------------|------------|
| Frontend | Nginx (Alpine) | Servidor web para ficheiros estáticos |
| MS Pessoas Aleatórias | Python (FastAPI) | API REST com SQLite |
| MS Saudações Aleatórias | Go (Gin) | API REST com SQLite |
| Orquestração | Docker Compose | Gerenciamento da stack |

---
### 📌 Descrição dos Diretórios

- `ms-pessoas-aleatorias/` → Código-fonte e Dockerfile do microserviço Python  
- `ms-saudacoes-aleatorias/` → Código-fonte e Dockerfile do microserviço Go  
- `site-gerador-saudacoes/` → Ficheiros estáticos e Dockerfile do frontend Nginx  
- `docker-compose.yaml` → Orquestração de todos os serviços  

---

# ⚙️ Pré-requisitos

- Docker Instalado
- Conta no Docker Hub

## 🚀 Passo a Passo para Execução
1. Navegue até a pasta raiz do projeto onde se encontra o ficheiro `docker-compose.yaml`.
2. Execute o comando abaixo no terminal para iniciar todos os serviços em segundo plano:
```bash
docker-compose up -d
```

## 🔗 Serviços e Portas
Após a execução bem-sucedida, os serviços estarão disponíveis nos seguintes endereços:

- Aplicação Web (Frontend): http://localhost:80 — Interface principal que exibe as saudações.

- API de Pessoas: http://localhost:8000 — Serviço FastAPI para sorteio de nomes (Documentação interativa em /docs).

- API de Saudações: http://localhost:8080 — Serviço Go para sorteio de frases (Endpoint principal em /api/saudacoes/aleatorio).
