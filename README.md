# React + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh


# bingo-driven
Sistema para a administração de jogos de bingo.

![demonstração do bingo](demo-bingo.gif)

## Funcionalidades
- Criação de jogos de bingo.
- Geração de números para um jogo (sorteio).
- Finalização de jogos.
- Armazenamento dos jogos e seus números sorteados.

## Links de Deploy
- Front-end: https://bingo-frontend-pi.vercel.app/
- Back-end: https://bingo-backend-pipeline.onrender.com/

## Tecnologias
- Back-end: Node.js, Express, Typescript, Jest e Prisma.
- Banco de dados: Postgres.
- Front-end: React e Vite.

## Desenvolvimento
- O projeto é fullstack e é necessário subir ambos front-end e back-end separadamente.
- Para o back-end:
  - Instalar as dependências com o `npm i`;
  - Criar o arquivo `.env` com base no exemplo do `.env.example`;
  - Preparar o banco de dados usando o prisma (`prisma migrate dev`);
  - Executar o comando `npm run dev`.
- Para executar os testes do back-end:
  - Criar o arquivo `.env.test` com base no exemplo do `.env.example`;
  - Preparar o banco de dados usando o Prisma (`npm run test:migration`);
  - Executar o comando `npm run test`.
- Para o front-end:
  - Instalar as dependências com o `npm i`;
  - Criar o arquivo `.env` com base no exemplo do `.env.example`;
  - Executar o comando `npm run test`. 

## Uso com Docker
- Para o Back-end:
  - Construir a imagem `docker build -t bingo-backend .`.
  - Subir o banco de dados Postgres `docker network create bingo-network`.
  - Rodar o banco de dados em um container docker `docker run -d --name bingo-postgres --network bingo-network -p 5433:5432 -e POSTGRES_PASSWORD=postgres postgres`.
  - Subir o back-end em um container docker `docker run -d --name bingo-backend --network bingo-network -e DATABASE_URL=postgresql://postgres:postgres@bingo-postgres:5432/mydb?schema=public -p 5000:5000 bingo-backend`.

- Para o Front-end:
  - Construir a imagem `docker build -t bingo-frontend .`.
  - Rodar o front-end em um container docker `docker run -d --name bingo-frontend -p 8080:80 bingo-frontend`.

## Uso com Docker Compose
- Para o Back-end e para o Front-end:  
  - Subir os containers juntos com `docker compose up -d`.
  