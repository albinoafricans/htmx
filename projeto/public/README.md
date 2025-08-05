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

## atributos hx-get - GET

<body>
    <!--hx-get - trabalhando com o verbo - GET -->
    <!--hx-trigger -->
    <!--hx-target -->
    <button hx-get="/carregar-conteudo">carregar conteúdo via botão</button>
    <p hx-get="/carregar-conteudo" hx-trigger="click[ctrlKey]">carregar conteúdo via trigger</p>
    <button hx-get="/carregar-conteudo" hx-target="#conteudo-get">carregar conteúdo via botão</button>
    <div id="conteudo-get"></div>
</body>


## atributos tx-post - POST


frontend
    <form hx-post="/enviar-formulario" hx-trigger="submit">
        <label for="nome">Nome:</label>
        <input type="text" name="nome" >  
        <!-- o conteúdo do atributo NAME do input que sera enviado ao backend, devidamente configurado, como exemplificado abaixo -->
        <button>enviar</button>
    </form>

backend
    app.post("/enviar-formulario", (req, res) => {
    const { nome } = req.body;

    // processamento com o dado

    res.send(`<p>Formulário enviado. Nome: ${nome}</p>`);
    });


## referências

https://htmx.org/
