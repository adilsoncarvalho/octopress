---
comments: true
date: 2011-07-03 01:07:02
layout: post
slug: loaderror-no-such-file-to-load-spec_helper
title: 'LoadError: no such file to load -- spec_helper'
wordpress_id: 308
categories:
- HowTo
tags:
- rails
- rspec
- ruby
- test
---

Eu estou trabalhando em uma aplicação bem simples, e precisava utilizar o RSpec para os testes já que ele é padrão na gem que estou usando.




Bem, tenho de admitir que [Test::Unit](http://en.wikibooks.org/wiki/Ruby_Programming/Unit_testing) e [minitest](http://www.bootspring.com/2010/09/22/minitest-rubys-test-framework/) eu já usei bastante, mas o [RSpec](http://rspec.info/) ainda é um ilustre desconhecido.




## O problema




Eu estou trabalhando em um projeto que utiliza algumas tecnologias diferentes, e que por sua vez ainda estão com a documentação meio ausente. Ao tentar rodar os specs eu recebi o seguinte erro:




![Onde está spec_helper.rb?](http://adilsoncarvalho.com.br/blog/wp-content/uploads/2011/07/rspec-error.png)




A resposta para ele é mais do que simples:




> 

> 
> é só criar o arquivo spec_helper.rb!
> 
> 





Ok, mas e como que é esse arquivo?




## A instalação do RSpec




A instalação dele foi bem tranquila. Você somente tem de instalar as gems no seu ruby.











Depois eu adicionei as dependências necessárias no arquivo Gemfile











O que eu não tinha visto na [documentação](https://github.com/rspec/rspec-rails) era que eu precisava no meu projeto em Rails _instalar_ o RSpec.











Na _instalação_ ele gerou os arquivos necessários, e então o RSpec funcionou sem problemas.




![RSpec working :)](http://adilsoncarvalho.com.br/blog/wp-content/uploads/2011/07/rspec-working-perfectly.png)




## O log da sessão




Se interessar, o log completo da sessão está nos meus [gists no github](https://gist.github.com/1061938).




 
