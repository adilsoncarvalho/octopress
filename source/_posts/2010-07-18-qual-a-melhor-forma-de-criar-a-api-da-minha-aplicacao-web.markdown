---
comments: true
date: 2010-07-18 22:31:01
layout: post
slug: qual-a-melhor-forma-de-criar-a-api-da-minha-aplicacao-web
title: Qual a melhor forma de criar a API da minha aplicação web?
wordpress_id: 39
categories:
- /I write code in .*?/gi
tags:
- API
- cUrl
- Linux
- Shell
- Twitter
---

[![](http://adilsoncarvalho.com.br/blog/wp-content/uploads/2010/07/the-web.png)](http://adilsoncarvalho.com.br/blog/wp-content/uploads/2010/07/the-web.png)É usar ao máximo os padrões. Você pode inventar, mas quanto mais comum for a tecnologia escolhida, mais _conectável_ você vai ser,

Uma das características que eu mais acho fascinante no _mundo web_ é a possibilidade de aplicações criadas em qualquer ambiente se comunicar com quaisquer outras. Isto é fantástico.

Tem muita gente que acha que para ser um aplicativo _web_ só precisa estar na nevem e rodar em um _browser_. Ledo engano.

Tem muito site por ai que para mim ainda está na era do _stand alone_, sendo que ao invés de estar sendo executado local, roda em um servidor remoto, mas só isso.


> A facilidade de conectividade do e para o aplicativo está na lista das maiores qualidades de um software da era da web.


É algo lindo de ver, e que eu sequer sonhava que existiriam enquanto ficava lá esperando 30 minutos até meu compilador Clipper Summer'86 gerar minhas _poderosas aplicações_... tadinhas delas.

Um bom aplicativo tem de permitir que qualquer outro possa se conectar nele e interagir com suas regras de negócio, mais ainda, as regras internas do aplicativo podem inclusive _chamar_ um convidado externo para resolver algo que elas não vão resolver.

Recentemente vi um tweet do [Fred](http://twitter.com/frdrcchvs0) indicando um post meio antigo, de 2008, chamado [Brincando com a API do twitter](http://elcio.com.br/brincando-com-a-api-do-twitter/). Nele o Élcio mostra como você pode criar um _script_ em _shell_ no linux para twittar da linha de comando.

Com o [cURL](http://curl.haxx.se/download.html) para Windows e um pouco de criatividade, dá para fazer o mesmo em arquivo de lote.

Não só o Twitter tem uma boa [API](http://apiwiki.twitter.com/), mas quase todos os serviços _maiores_ da web também possuem.

Porque você acha que eles crescem tanto? Porque são _acessíveis_ para quaisquer consumidores, e deixam que muitos façam softwares para ele.

Eu sou um exemplo. Nunca usei o [Twiter](http://twitter.com/), até que encontrei o [Chromed Bird](https://chrome.google.com/extensions/detail/encaiiljifbdbjlphpgpiimidegddhic). Agora como o Twitter está sempre à mão ali na barra de ferramentas do meu [Google Chrome](http://www.google.com/chrome), acabo twittando o dia todo, e ele verdadeiramente me serve como meio dinâmico de comunicação.

Agora falando sobre a arquitetura destas API's, a grande maioria delas utiliza somente _requisições http_, podendo sobre elas criar um padrão _[RESTfull](http://pt.wikipedia.org/wiki/REST)_. É a reinveção do _PUT/GET/POST/DELETE_ :)

O bacana seguir um padrão que é realmente web é que você ao prover o serviço sabe que se você enviar uma resposta [307](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) o cliente irá entender e fazer nova consulta no endereço que você indicou.

Praticamente tudo dos meios já existe e é amplamente suportado. Cabe a você criar a aplicação :)

**Importante: a API do Twitter em 16 de agosto de 2010 passará a exigir outra forma de autenticação, data da qual os exemplos do post do Élcio vão parar de fucionar.**
