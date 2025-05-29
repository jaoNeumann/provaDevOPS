# Explicação dos Arquivos

## Dockerfiles

- products/Dockerfile;
  Utiliza a imagem Node.js, instala o Express e executa o app.js na porta 3001

- orders/Dockerfile:
  Usa Python, instala Flask, Redis, MySQL Connector e Requests. Executa app.py na porta 3002

- payments/Dockerfile:
  Usa PHP. roda index.php na porta 3003

## docker-compose.yml

- usando os serviços:
  - **products**: API Node.js | porta 3001
  - **orders**: API Python | Redis e MySQL porta 3002 
  - **payments**: API PHP consome orders porta 3003
  - **db**: MySQL banco `ecommerce` senha `example`
  - **redis**: Serviço Redis (COLOQUEI UMA IMAGEM LISTANDO AS KEYS DO REDIS CHAMADA redisKeys.png, só consegui evidenciar que estava usando cache do redis com esses comandos pelo terminal e colocando prints no app.py)

- Todos os serviços estão na rede (`ecommerce-net`), se comunicando entre si
