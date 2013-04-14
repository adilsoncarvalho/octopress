---
comments: true
date: 2011-07-16 21:38:27
layout: post
slug: executando-um-script-ruby-no-contexto-de-uma-app-rails
title: Executando um script ruby no contexto de uma app rails
wordpress_id: 312
categories:
- HowTo
tags:
- rails
- ruby
---

Eu estou desenvolvendo uma aplicação que precisa executar um processo de atualização de dados diariamente.

Este processo será disparado via [cron](http://en.wikipedia.org/wiki/Cron), e para tanto eu preciso que ele rode no contexto da minha [aplicação em rails](http://guides.rubyonrails.org/getting_started.html) para consumir os models dela.


> Como diz a [canção](http://www.allthelikes.com/quotes.php?quoteId=4497082&app=140039) de Vinícius de Moraes, _...aos sábados em casa tomo um porre e sonho soluções fenomenais!.._. :)


OK! Nada disto necessário, na verdade logo após as _soluções fenomenais_ eu achei a mais simples e que funciona bem:

Dentro do diretório do projeto você pode executar o comando rails runner.


> rails my-directory/my-ruby-script.rb



