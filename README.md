<h1 align="center">
  <br>
  🛍️ <br>
  MegaShop
  <br>
</h1>

<h4 align="center">A tua loja única para tudo o que é fantástico.</h4>

<p align="center">
  <a href="#-sobre">Sobre</a> •
  <a href="#-funcionalidades">Funcionalidades</a> •
  <a href="#-tech-stack">Tech Stack</a> •
  <a href="#-como-executar">Como Executar</a> •
  <a href="#-autor">Autor</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/status-active-success.svg?style=flat-square&color=orange" alt="Status">
  <img src="https://img.shields.io/badge/react-v19-blue?style=flat-square&logo=react" alt="React">
  <img src="https://img.shields.io/badge/vite-v7-purple?style=flat-square&logo=vite" alt="Vite">
  <img src="https://img.shields.io/badge/docker-enabled-blue?style=flat-square&logo=docker" alt="Docker">
  <img src="https://img.shields.io/badge/license-ISC-green?style=flat-square" alt="License">
</p>

<br>

## 🔖 Sobre

O **MegaShop** é um projeto Fullstack robusto que simula uma plataforma de E-commerce completa.

O objetivo é oferecer uma experiência de compra fluida ("Your one-stop shop for all things awesome!"), com uma interface moderna e um backend eficiente, demonstrando competências avançadas em desenvolvimento web e orquestração de contentores.

---

## ✨ Funcionalidades

O sistema foi desenhado para cobrir os principais requisitos de um comércio eletrónico real:

* **📦 Catálogo Dinâmico:** Navegação intuitiva por categorias como Tecnologia, Desporto, Mobiliário e Ferramentas.
* **🔍 Filtragem e Paginação:** Ferramentas avançadas para encontrar produtos rapidamente.
* **🛒 Gestão de Estado:** Carrinho de compras e fluxo de dados geridos globalmente.
* **🐳 Ambiente Dockerizado:** Configuração completa para desenvolvimento e deploy facilitado.

---

## 🚀 Tech Stack

Utilizámos uma stack moderna focada em performance e escalabilidade.

### Frontend
* **Core:** `React 19`, `Vite`, `React Router DOM`
* **Gestão de Estado:** `Redux Toolkit`, `React Redux`
* **Estilização:** `Tailwind CSS v4`, `Heroicons`
* **Comunicação:** `Axios`
* **UX:** `React Hot Toast`

### Backend
* **Runtime:** `Node.js`
* **Framework:** `Express.js`
* **ORM:** `Prisma`
* **Utilitários:** `Dotenv`, `Cors`, `Nodemon`

### DevOps
* **Containerização:** `Docker`, `Docker Compose`

---

## 💻 Como Executar

Este projeto está totalmente configurado com Docker para uma inicialização rápida e sem conflitos de ambiente.

### Pré-requisitos

* **Docker Desktop** (deve estar em execução)

### Instalação e Execução

1.  **Clone o repositório e navegue até à pasta raiz.**

2.  **Inicie os contentores:**
    Execute o seguinte comando no terminal:
    ```bash
    docker compose up --build -d
    ```

3.  **Aceda à Aplicação:**
    * 🖥️ **Frontend:** `http://localhost:5173/`
    * ⚙️ **Backend:** `http://localhost:3000/`

4.  **Parar a Aplicação:**
    Para encerrar o ambiente, utilize:
    ```bash
    docker compose down
    ```
   

---

## 📂 Estrutura do Repositório

```text
MegaShop/
├── backend/            # API Server (Node/Express/Prisma)
├── frontend/           # Client Application (React/Vite/Redux)
├── docker-compose.yml  # Orquestração dos serviços
└── README.md           # Documentação do projeto
