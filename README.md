<h1 align="center">
  <br>
  🛍️ <br>
  MegaShop E-commerce
  <br>
</h1>

<h4 align="center">Uma plataforma Fullstack robusta para comércio eletrônico escalável.</h4>

<p align="center">
  <a href="#-sobre">Sobre</a> •
  <a href="#-arquitetura">Arquitetura</a> •
  <a href="#-funcionalidades">Features</a> •
  <a href="#-api-endpoints">API</a> •
  <a href="#-instalação-e-docker">Instalação & Docker</a> •
  <a href="#-stack">Stack</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/status-active-success.svg?style=flat-square&color=2E8B57" alt="Status">
  <img src="https://img.shields.io/badge/docker-enabled-blue?style=flat-square&logo=docker" alt="Docker">
  <img src="https://img.shields.io/badge/react-v19-blue?style=flat-square&logo=react" alt="React">
  <img src="https://img.shields.io/badge/node-v20-green?style=flat-square&logo=nodedotjs" alt="Node">
  <img src="https://img.shields.io/badge/prisma-orm-blueviolet?style=flat-square&logo=prisma" alt="Prisma">
  <img src="https://img.shields.io/badge/license-ISC-lightgrey?style=flat-square" alt="License">
</p>

<br>

## 🔖 Sobre

O **MegaShop** é uma solução completa de E-commerce desenvolvida para simular cenários reais de venda online. O projeto foi construído focando em performance, escalabilidade e uma experiência de usuário (UX) fluida.

Diferente de projetos básicos, o MegaShop implementa uma arquitetura separada (Client-Server), utiliza **Docker** para orquestração de ambiente e **Redux Toolkit** para gerenciamento de estado global complexo, garantindo que o carrinho de compras e os dados do usuário persistam e fluam corretamente pela aplicação.

---

## 🏗 Arquitetura

O sistema segue o padrão MVC (Model-View-Controller) no backend e uma arquitetura baseada em Componentes e Hooks no frontend.

```mermaid
graph TD;
  Client[Frontend (React/Vite)] -->|HTTP/Axios| API[Backend (Express)];
  API -->|Query| DB[(PostgreSQL/Prisma)];
  API -->|Response| Client;
  Client -->|Action| Redux[Redux Store];
Destaques da EstruturaBackend: Camadas de Controller e Service bem definidas para isolar a regra de negócio do roteamento HTTP.Database: Uso do Prisma ORM para migrações seguras e tipagem forte no acesso ao banco de dados.Frontend: Uso de Tailwind CSS v4 para estilização moderna e React Router v7 para navegação SPA (Single Page Application).✨ Funcionalidades📦 Catálogo de Produtos: Listagem dinâmica com filtragem por categorias (Tecnologia, Esportes, Móveis, etc.).🛒 Carrinho Inteligente: Adição, remoção e cálculo de total em tempo real gerenciado via Redux.📄 Paginação: Navegação eficiente entre grandes volumes de produtos.🔔 Sistema de Notificações: Feedback visual imediato para ações do usuário (Sucesso/Erro) usando react-hot-toast.🔌 API EndpointsA API RESTful expõe recursos para manipulação de produtos e carrinho.MétodoRotaDescriçãoControllerGET/productsLista todos os produtos (com paginação)ProductListControllerGET/products/:idDetalhes de um produto específicoProductListControllerGET/cartRecupera o carrinho atualCartListControllerPOST/cartAdiciona item ao carrinhoCartListControllerDELETE/cart/:idRemove item do carrinhoCartListControllerA documentação completa da API pode ser encontrada nos arquivos de rota.🐳 Instalação e DockerO projeto está totalmente "Dockerizado" para garantir que funcione em qualquer máquina sem conflitos de dependência.Pré-requisitosDocker Desktop instalado e rodando.GitPasso a PassoClone o repositório:Bashgit clone [https://github.com/dev-soares/megashop.git](https://github.com/dev-soares/megashop.git)
cd megashop
Suba os containers:Este comando irá construir as imagens do Frontend e Backend e iniciar o banco de dados.Bashdocker compose up --build -d
Acesse a aplicação:Frontend: http://localhost:5173API: http://localhost:3000Parar o ambiente:Bashdocker compose down
Nota: As migrações do Prisma são executadas automaticamente via scripts definidos no package.json.💻 Tech StackFrontendReact 19 & Vite (Core)Redux Toolkit (State Management)Tailwind CSS v4 (Styling)Axios (HTTP Client)Heroicons (Icons)BackendNode.js & ExpressPrisma ORM (Database Interface)PostgreSQL (Database - via Docker)Dotenv & Cors (Security/Config)🤝 ContribuiçãoFaça um Fork do projeto.Crie uma Branch para sua Feature (git checkout -b feature/AmazingFeature).Faça o Commit (git commit -m 'Add: AmazingFeature').Faça o Push (git push origin feature/AmazingFeature).Abra um Pull Request.<table align="center"><tr><td align="center"><a href="https://github.com/dev-soares"><img src="https://www.google.com/search?q=https://github.com/dev-soares.png" width="100px;" alt="Foto de Perfil"/><sub><b>Dev Soares</b></sub></a><span title="Fullstack Developer">🚀 Fullstack Developer</span></td></tr></table><p align="center">Feito com ❤️ por Dev Soares</p>
