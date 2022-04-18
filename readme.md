# DOCKER PRESTASHOP

Este docker utiliza como base o docker oficial do Prestashop, apenas separando a pasta do plugin do Mercado Pago para mapeamento local do volume.

## Uso

1 - Crie um arquivo chamado .env usando de base o arquivo .env.sample  

2 - Defina o path dos arquivos de SSL neste arquivo

3 - No arquivo docker-compose, comente o bloco do mysql caso não precise do banco de dados rodando local

4 - `docker-compose up -d --build` para executar os containers