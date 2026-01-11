<h1 align="center">
  <br>
   <br>
  MegaShop
  <br>
</h1>

<h4 align="center">Your one-stop shop for all things awesome.</h4>

<p align="center">
  <a href="#-about">About</a> •
  <a href="#-features">Features</a> •
  <a href="#-tech-stack">Tech Stack</a> •
  <a href="#-getting-started">Getting Started</a> •
  <a href="#-api-endpoints">API Endpoints</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/status-active-success.svg?style=flat-square&color=orange" alt="Status">
  <img src="https://img.shields.io/badge/react-v19-blue?style=flat-square&logo=react" alt="React">
  <img src="https://img.shields.io/badge/vite-v7-purple?style=flat-square&logo=vite" alt="Vite">
  <img src="https://img.shields.io/badge/tailwind-v4-38B2AC?style=flat-square&logo=tailwind-css" alt="Tailwind">
  <img src="https://img.shields.io/badge/docker-enabled-blue?style=flat-square&logo=docker" alt="Docker">
  <img src="https://img.shields.io/badge/license-ISC-green?style=flat-square" alt="License">
</p>

<br>

##  About

**MegaShop** is a robust Fullstack E-commerce simulation platform. 

It provides a seamless shopping experience with a modern UI and a high-performance backend. The project demonstrates advanced web development architectures, separating the client (SPA) and server (REST API), all orchestrated via **Docker** for a consistent development and deployment environment.

---

##  Features

* ** Dynamic Catalog:** Browse products with automatic pagination and fetching.
* ** Categories & Filtering:** Intuitive navigation through Technology, Sports, Furniture, and more.
* ** Global State Management:** Full shopping cart functionality (Add, Remove, Adjust Quantity) powered by **Redux Toolkit**.
* ** Product Management:** "Sell your product" feature allowing users to add new items to the database.
* ** Fully Dockerized:** Zero-config setup using Docker Compose.
* ** Responsive Design:** Built with **Tailwind CSS v4** for mobile-first compatibility.

---

##  Tech Stack

### Frontend
* **Core:** `React 19`, `Vite v7`
* **Routing:** `React Router DOM v7`
* **State Management:** `Redux Toolkit`, `React Redux`
* **Styling:** `Tailwind CSS v4`, `Heroicons`
* **HTTP Client:** `Axios`
* **Feedback/UI:** `React Hot Toast`

### Backend
* **Runtime:** `Node.js v20`
* **Framework:** `Express.js v5`
* **Database:** `PostgreSQL`
* **ORM:** `Prisma`
* **Utilities:** `Cors`, `Dotenv`, `Nodemon`

### DevOps
* **Containerization:** `Docker`, `Docker Compose`

---

##  Getting Started

This project is configured with Docker to ensure a quick start without local environment conflicts.

### Prerequisites

* **Docker Desktop** (Must be running)
* **Git**

### Installation & Execution

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/megashop.git](https://github.com/your-username/megashop.git)
    cd MegaShop
    ```

2.  **Environment Configuration:**
    The project comes with a `.env.example` file. Docker Compose will automatically handle the environment variables defined in the `docker-compose.yml`, but you can create a `.env` file in the root if you wish to customize ports or credentials.

3.  **Start the Application:**
    Run the following command in the root terminal:
    ```bash
    docker compose up --build -d
    ```
    *Note: The first build might take a few moments.*

4.  **Access the App:**
    *  **Frontend:** [http://localhost:5173/](http://localhost:5173/)
    *  **Backend API:** [http://localhost:3000/](http://localhost:3000/)

5.  **Stop the Application:**
    To stop the containers:
    ```bash
    docker compose down
    ```

> **Note:** The database is automatically seeded with sample products upon the first launch via the `prisma db seed` command defined in the container startup script.

---

##  API Endpoints

The backend exposes a RESTful API. Below are the main resources:

### Products
* `GET /api/products` - Get all products (supports pagination `?page=X&limit=Y`).
* `GET /api/products/:id` - Get a specific product by ID.
* `GET /api/products/category/:category` - Get products filtered by category.
* `POST /api/products/create-product` - Create a new product.
* `DELETE /api/products/:id` - Delete a product.

### Cart
* `GET /api/cart` - Get current cart items.
* `POST /api/cart/:id` - Add a product to the cart.
* `PUT /api/cart/quantity/:id` - Update item quantity.
* `DELETE /api/cart/:id` - Remove item from cart.
* `GET /api/cart/total-price` - Get the total calculated price.

---

##  Project Structure

```text
MegaShop/
├── backend/                # API Server (Node/Express/Prisma)
│   ├── config/             # DB Configuration
│   ├── controllers/        # Route Logic
│   ├── prisma/             # Schema & Migrations
│   ├── routes/             # API Routes
│   └── services/           # Business Logic
├── frontend/               # Client Application (React/Vite)
│   ├── src/
│   │   ├── components/     # UI Components
│   │   ├── hooks/          # Custom Hooks (useCart, useProducts)
│   │   ├── pages/          # App Pages
│   │   └── state/          # Redux Store
└── docker-compose.yml      # Service Orchestration
