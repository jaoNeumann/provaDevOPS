# Explicação dos Arquivos

## Dockerfiles

- products/Dockerfile:
  Utiliza a imagem Node.js, instala o Express e executa o app.js na porta 3001.

- orders/Dockerfile:
  Usa Python, instala Flask, Redis, MySQL Connector e Requests. Executa app.py na porta 3002.

- payments/Dockerfile:
  Usa PHP puro com servidor embutido (`php -S`) para servir o index.php na porta 3003.

## docker-compose.yml

- Define 5 serviços:
  - **products**: API Node.js rodando na porta 3001.
  - **orders**: API Python que usa Redis e MySQL, roda na porta 3002.
  - **payments**: API PHP puro que consome a orders, roda na porta 3003.
  - **db**: Instância MySQL com banco `ecommerce` e senha `example`.
  - **redis**: Serviço Redis para cache.

- Todos os serviços estão na mesma rede (`ecommerce-net`), o que permite que se comuniquem entre si usando os nomes dos serviços como hosts (ex: `http://orders:3002`).
