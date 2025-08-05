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


## utiliando o swap

<body>
    <!-- swap - ele substitui a div #conteudo-swap para o retorno -->
    <!-- dessa forma podemos incluir o html sem ficarmos refem do html que ja esta na pagina -->
     <button
      hx-get="/trocar-conteudo"
      hx-target="#conteudo-swap"
      hx-swap="outerHTML"
     >carregar conteúdo</button>
     <div id="conteudo-swap"></div>
</body>


## utilizando o vals 

- frontend

<body>
     <!-- hx-vals - quando precisarmos enviar valores extra
     adicionar mais valores ao req.body 
     - enviado via {chave:valor} o conteúdo adicional 
     -->
    <form 
        hx-post="/valores-adicionais" 
        hx-trigger="submit" 
        hx-target="#valores-adicionais"
        hx-vals='{"valorExtra": "Este é um valor adicional"}'
        >
        <label for="nome">Nome:</label>
        <input type="text" name="nome" >
        <button>enviar</button>
    </form>
    <div id="valores-adicionais"></div>
</body>

- backend

app.post("/valores-adicionais", (req, res) => {
  const { valorExtra } = req.body;
  res.send(`<p>Valor adicional recebido: ${valorExtra}</p>`);
});


## polling

<body>
    <!-- Polling - programar requests a cada x tempo no  backend -->
    <div 
        hx-get="/tempo-servidor" 
        hx-trigger="every 5s" 
        hx-target="#tempo-servidor"
    >
    <p>carregando hora do servidor ...</p>
    </div>
    <div id="tempo-servidor"></div>
</body>


## validações




## referências

https://htmx.org/

[CURSO DE HTMX COM PROJETO - APRENDA HTMX EM 1 HORA](https://www.youtube.com/watch?v=hsZzlmPdrIU&list=PLnDvRpP8BnexcN1wwjFfPNGyLiRKrTlwm)

https://github.com/matheusbattisti/curso_htmx_yt
