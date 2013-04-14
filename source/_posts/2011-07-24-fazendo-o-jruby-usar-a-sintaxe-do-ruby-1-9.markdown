---
comments: true
date: 2011-07-24 00:30:07
layout: post
slug: fazendo-o-jruby-usar-a-sintaxe-do-ruby-1-9
title: Fazendo o JRuby usar a sintaxe do Ruby 1.9
wordpress_id: 353
categories:
- HowTo
tags:
- '1.9'
- jruby
- ruby
---

Sinceramente, nunca fui fã dos hashes no modelo { :chave => 'valor' }. Eu acho esta sintaxe terrívelmente feia, ainda mais quando comparada com a nova, que lembra o jeitão do javascript { chave: 'valor' }

Claro que não mudou somente isto. Entre as mudanças mais importantes podemos destacar:



	
  * Ruby 1.9 agora deixa de ser interpretada para ser bytecode-compiled (usando YARV VM)

	
  * A classe String foi refeita para agora estar ciente que existe uma coisa chamada encoding

	
  * Expressões regulares agora rodam na engine Oniguruma, que traz novos recursos

	
  * A biblioteca `enumerator` da stdlib foi adicionada ao core e a grande maioria dos métodos em `Enumerable` agora retornam uma instância de `Enumerator` quando chamados sem um bloco

	
  * `Symbol#to_proc` foi criada

	
  * Foi criada uma nova sintaxe para os lambdas, `->` que permite parâmetros com valores padrão, entre outras novidades


Tem uma apresentação antiga chamada [Ruby 1.9: What to expect](http://intertwingly.net/slides/2008/oscon/ruby19/1) que fala em mais detalhes o que mudou.


## Mas afinal, #comofaz?


A melhor forma é criando uma variável de ambiente JRUB_OPTS e atribuir o valor --1.9 nela.

Você pode passar isso para o jruby como parâmetro, mas algumas operações iriam ainda usar o sintaxe do 1.8.

No MacOS e no Linux:


> export JRUBY_OPTS='--1.9'


No Windows:


> SET JRUBY_OPTS='--1.9'



