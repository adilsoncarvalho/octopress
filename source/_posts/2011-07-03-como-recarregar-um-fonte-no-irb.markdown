---
comments: true
date: 2011-07-03 00:16:38
layout: post
slug: como-recarregar-um-fonte-no-irb
title: Como recarregar um fonte no irb
wordpress_id: 304
categories:
- note.to :self
tags:
- irb
- ruby
---

Quando estou testando algo em Ruby, o irb é imprescindível, mas e quando a gente precisa recarregar um fonte que já foi carregado com um **require**?




Fácil, é só usar o comando **load**.




> 

> 
> Lembre-se que com load você precisa inclusive colocar a extensão do arquido (geralemente o .rb)
> 
> 





![Precisa informar a extensão com load](http://adilsoncarvalho.com.br/blog/wp-content/uploads/2011/07/irb-load-must-inform-rb.png)
