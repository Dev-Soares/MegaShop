# MegaShop

Plataforma de e-commerce full-stack com catálogo de produtos, filtro por categoria, carrinho global e seed automático do banco de dados.

Arquitetura separada com `frontend/` (React SPA) e `backend/` (Express REST API), orquestrados com **Docker Compose**.

---

## Sumário

- [Estrutura do projeto](#estrutura-do-projeto)
- [Tecnologias](#tecnologias)
- [Pré-requisitos](#pré-requisitos)
- [Rodando com Docker (recomendado)](#rodando-com-docker-recomendado)
- [Rodando sem Docker](#rodando-sem-docker)
- [Variáveis de ambiente](#variáveis-de-ambiente)
- [Banco de dados](#banco-de-dados)
- [Endpoints da API](#endpoints-da-api)
  - [Produtos](#produtos)
  - [Carrinho](#carrinho)
- [Funcionalidades](#funcionalidades)

---

## Estrutura do projeto

```
MegaShop/
├── backend/                         # API Node/Express
│   ├── app.js                       # Express app (rotas, middlewares)
│   ├── server.js                    # Ponto de entrada
│   ├── config/prisma.js             # Instância do Prisma Client
│   ├── controllers/                 # Lógica das rotas
│   ├── services/                    # Regras de negócio
│   ├── routes/                      # Definição das rotas
│   └── prisma/
│       ├── schema.prisma
│       ├── seed.js                  # Seed de produtos iniciais
│       └── migrations/
│
├── frontend/                        # React SPA
│   └── src/
│       ├── components/              # UI components + seções da página
│       ├── hooks/                   # useCart, useProducts
│       ├── pages/                   # MainPage, ProductPage, CartPage, ListProductPage
│       ├── state/
│       │   ├── store.js             # Redux store
│       │   └── cart/cartSlice.js    # Cart state (Redux Toolkit)
│       └── contexts/
│           └── AlertContext.jsx     # Feedbacks globais
│
├── docker-compose.yml               # Sobe db + backend + frontend
└── .env.example
```

---

## Tecnologias

### Frontend

| Tecnologia | Uso |
|---|---|
| React 19 | UI |
| Vite 7 | Bundler |
| React Router v7 | Roteamento |
| Redux Toolkit | Estado global do carrinho |
| Tailwind CSS v4 | Estilização |
| Axios | HTTP client |
| React Hot Toast | Notificações |
| Heroicons | Ícones |

### Backend

| Tecnologia | Uso |
|---|---|
| Node.js | Runtime |
| Express v5 | Framework HTTP |
| PostgreSQL | Banco de dados |
| Prisma | ORM e migrations |
| CORS | Política de origens |
| dotenv | Variáveis de ambiente |

---

## Pré-requisitos

**Com Docker:**
- Docker Desktop rodando

**Sem Docker:**
- Node.js >= 18
- PostgreSQL rodando localmente

---

## Rodando com Docker (recomendado)

O `docker-compose.yml` sobe **PostgreSQL + backend + frontend** juntos. O backend executa as migrations e o seed automaticamente na inicialização.

```bash
# Clone e entre na pasta
git clone <url-do-repositorio>
cd MegaShop

# Crie o .env com as credenciais
cp .env.example .env

# Sobe tudo em background
docker compose up --build -d
```

Após o build:

| Serviço | URL |
|---|---|
| Frontend | http://localhost:5173 |
| API | http://localhost:3000 |

```bash
# Parar tudo
docker compose down

# Parar e remover volumes (banco zerado)
docker compose down -v
```

> Na primeira subida o banco é populado automaticamente com produtos de exemplo via `prisma db seed`.

---

## Rodando sem Docker

### Backend

```bash
cd backend
npm install
cp .env.example .env   # preencha DATABASE_URL com seu PostgreSQL local

npx prisma migrate deploy
npx prisma db seed

npm start              # ou: npm run dev (nodemon)
```

### Frontend

```bash
cd frontend
npm install
cp .env.example .env   # preencha VITE_API_URL

npm run dev
```

---

## Variáveis de ambiente

**Raiz (`.env`)** — usado pelo Docker Compose:

```env
DB_USER=docker_user
DB_PASSWORD=docker_password_secure
DB_NAME=ecommerce_local

PORT=3000
NODE_ENV=development

VITE_API_URL=http://localhost:3000/api
```

**`backend/.env`** — para rodar sem Docker:

```env
DATABASE_URL="postgresql://usuario:senha@localhost:5432/ecommerce_local?schema=public"
PORT=3000
NODE_ENV=development
```

**`frontend/.env`** — para rodar sem Docker:

```env
VITE_API_URL=http://localhost:3000/api
```

---

## Banco de dados

### Modelos

```
Product  → id, title?, description?, category?, price
Cart     → id, productId (unique), quantity
```

> O carrinho é persistido no banco de dados — não é apenas estado de sessão.

### Comandos úteis

```bash
# Aplicar migrations
npx prisma migrate deploy

# Popular banco com produtos de exemplo
node prisma/seed.js

# Criar nova migration
npx prisma migrate dev --name nome_da_migration
```

---

## Endpoints da API

Base: `http://localhost:3000/api`

### Produtos

| Método | Rota | Descrição |
|---|---|---|
| `GET` | `/products` | Lista produtos (suporta `?page=X&limit=Y`) |
| `GET` | `/products/:id` | Busca produto por ID |
| `GET` | `/products/category/:category` | Filtra por categoria |
| `POST` | `/products/create-product` | Cria um novo produto |
| `DELETE` | `/products/:id` | Remove um produto |

**Body criar produto:**
```json
{
  "title": "Notebook Pro",
  "description": "Descrição do produto",
  "category": "Tecnologia",
  "price": 4999.99
}
```

### Carrinho

| Método | Rota | Descrição |
|---|---|---|
| `GET` | `/cart` | Lista itens do carrinho |
| `POST` | `/cart/:id` | Adiciona produto ao carrinho |
| `PUT` | `/cart/quantity/:id` | Atualiza quantidade do item |
| `DELETE` | `/cart/:id` | Remove item do carrinho |
| `GET` | `/cart/total-price` | Retorna o preço total |

---

## Funcionalidades

- **Catálogo** com paginação automática e busca por categoria
- **Categorias** — Tecnologia, Esportes, Móveis, e mais (via seed)
- **Carrinho global** gerenciado com Redux Toolkit — adicionar, remover e ajustar quantidade
- **Cadastro de produto** — formulário para adicionar novos itens ao catálogo
- **Persistência do carrinho** — estado salvo no PostgreSQL, não apenas na sessão
- **Seed automático** — banco populado com produtos de exemplo no primeiro `docker compose up`
- **Responsivo** — layout mobile-first com Tailwind CSS v4
