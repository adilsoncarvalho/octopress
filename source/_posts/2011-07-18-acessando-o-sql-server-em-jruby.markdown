---
comments: true
date: 2011-07-18 09:08:41
layout: post
slug: acessando-o-sql-server-em-jruby
title: Acessando o SQL Server em JRuby
wordpress_id: 348
categories:
- HowTo
tags:
- jdbc
- jruby
- sql server
---

Na verdade eu vou acessar o banco via java. Em ruby MRI eu não tenho idéia de como fazer isto.


## Let's do it!


Primeiramente você vai precisar do [driver jdbc da Microsoft para o SQL Server](http://msdn.microsoft.com/en-us/sqlserver/aa937724).

Descompactando o arquivo, o jar que você está procurando é o **sqljdbc4.jar**. Ele deve ficar no seu CLASSPATH ou em algum lugar onde você possa dar require.

Caso você, como eu, não tenha a menor idéia de como montar uma string de conexão jdbc, é bom dar uma olhada em [Building the Connection URL](http://msdn.microsoft.com/en-us/library/ms378428.aspx).

{% gist 1089337 access-sql-server.rb %}
