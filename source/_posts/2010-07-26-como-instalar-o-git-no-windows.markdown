---
comments: true
date: 2010-07-26 13:28:46
layout: post
slug: como-instalar-o-git-no-windows
title: Como instalar o git no windows?
wordpress_id: 75
categories:
- HowTo
tags:
- git.instalação
- Linux
- windows
---

[![](http://git-scm.com/images/header.gif)](http://git-scm.com/)

Há coisas que poderiam ser simples em todos os lugares, e não só no [linux](http://code.google.com/p/msysgit/).

Mas instalar o git no windows não é um bicho de sete cabeças (tem no máximo umas três) :)

Para windows você tem basicamente duas opções (outras para outros sistemas operacionais você pode pegar [aqui](http://git-scm.com/download)):



	
  * [msysGit](http://code.google.com/p/msysgit/)

	
  * [Cygwin](http://www.cygwin.com/)


Eu aqui vou utilizar o msysGit, que eu uso e gosto muito. Não que o Cygwin não seja bom. É meramente uma opção pessoal.

![](http://adilsoncarvalho.com.br/blog/wp-content/uploads/2010/07/msysgit-download.png)


# O primeiro passo


Como não podia deixar de ser, é fazer o download do git. Ele pode ser encontrado na [página de downloads](http://code.google.com/p/msysgit/downloads/list).

Eu recomendo a instalação do [Git-1.7.0.2-preview20100309.exe](http://code.google.com/p/msysgit/downloads/detail?name=Git-1.7.0.2-preview20100309.exe&can=2&q=) por ser (até o presente momento) a versão estável mais atualizada.

Cuidado com as versões fullinstall que são para desenvolvimento e que para o uso do dia-a-dia trazem algumas complicações extras que talvez você não queira ter.

Uma delas é a necessidade do [Perl](http://www.perl.org/get.html) estar instalado na máquina. Nada de mais, se você está interessado em ir além do arroz-com-feijão, vá fundo.

Após baixá-lo, vamos partir para a instalação.











# A instalação do msysgit


O instalador, à boa moda windows, é basicamente _next, next, finish_, contudo você deve atentar para os seguintes detalhes:


## As opções a serem instaladas


![](http://adilsoncarvalho.com.br/blog/wp-content/uploads/2010/07/msysgit-install-options.png)

Aqui são dois pontos importantes a serem vistos:

**Deixe ambos, o Bash e o GUI disponíveis no menu de contexto do explorer do windows.**

Com o bash você poderá interagir com o git em linha de comando, podendo usar alguns comandos do linux como grep, ls, entre outros.

Deixando o GUI disponível, com um clique você poderá invocar a interface gráfica para te proteger da tão temida linha de comando. :)









## A escolha do SSH


[![](http://adilsoncarvalho.com.br/blog/wp-content/uploads/2010/07/msysgit-install-sshoptions.png)](http://adilsoncarvalho.com.br/blog/wp-content/uploads/2010/07/msysgit-install-sshoptions.png)Utilize de preferência o SSH que vem junto com o msysGit.

Ele é mais compatível com o SSH do linux, e na hora que algo der errado, a documentação disponível para consulta é muito maior.

Tive algumas experiências frustradas com as chaves e o SSH do puTTY. Se você sabe usá-lo bem, estou aceitando uma aula.









## Escolhendo como vai ser a linha de comando


[![](http://adilsoncarvalho.com.br/blog/wp-content/uploads/2010/07/msysgit-install-bashoptions-300x231.png)](http://adilsoncarvalho.com.br/blog/wp-content/uploads/2010/07/msysgit-install-bashoptions.png)O git traz consigo uma série de aplicativos do mundo unix, que são importantes para o seu correto funcionamento.

Eu prefiro optar por deixar o git somente disponível no seu shell para evitar que coisas do mundo windows e coisas do mundo linux começem a se misturar.









## Convenção das quebras de linha


[![](http://adilsoncarvalho.com.br/blog/wp-content/uploads/2010/07/msysgit-install-checkoutoptions-300x231.png)](http://adilsoncarvalho.com.br/blog/wp-content/uploads/2010/07/msysgit-install-checkoutoptions.png)Malditos sejam, não os padrões, mas a miríade deles.

O git pode servir de _conversor_ trocando sempre as quebras de linha pelo padrão que você escolheu e outro qualquer.

Por mim, ele que somente se atenha a versionar, e bem, para isso deixo selecionado que ele não deve interferir nas quebras de linha.









# Após tudo instalado, onde acho meu git?




![](http://adilsoncarvalho.com.br/blog/wp-content/uploads/2010/07/msysgit-install-context.png)
Selecione qualquer pasta e clique com o botão direito e devem aparecer as opções de consumo do git (bash ou gui)







