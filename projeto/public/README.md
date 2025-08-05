# passo a passo de como criar um HTMX consumindo uma API em NodeJS

## passo 1

estando na pasta BASE, criamos a estrutura inicial do nosso projeto em NodeJS

    npm init -y

## passo 2

instalaçao do framework web express para NodeJS

    npm i express

## passo 3

criação de nosso app.js onde definimos :

- inicialização do express / porta
- definição da porta
- configura uma pasta como publica para o usuario pode acessa-la, public no nosso caso
- define as rotas
- monta o servidor web

## passo 4

- criação da pasta PUBLIC 
- criação do arquivo index.html

## passo 5

referenciamos o script do HTMX via CDN em 

    https://htmx.org/docs/

## inicializando o express

- alteramos o arquivo package.json

  "scripts": {
    "start": "node --watch app.js"

- rodamos o servidor 

    npm start



## referências

https://htmx.org/
