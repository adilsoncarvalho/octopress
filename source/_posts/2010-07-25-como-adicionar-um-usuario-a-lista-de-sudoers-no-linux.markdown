---
comments: true
date: 2010-07-25 15:59:11
layout: post
slug: como-adicionar-um-usuario-a-lista-de-sudoers-no-linux
title: Como adicionar um usuário a lista de sudoers no linux?
wordpress_id: 60
categories:
- HowTo
tags:
- Linux
- root
- sudoers
---

Para que o usuário possa iniciar processos como se fosse o root, ele precisa estar na lista de sudoers.

Para adicionar um usuário nesta lista utilizamos o comando **visudo**.

Em um prompt de comando digite o comando abixo:


> 

>     
>     sudo visudo
> 
> 



Isto abrirá um arquivo para edição, onde você deverá conceder este privilégio para o usuário procure pela seguinte linha:


> 

>     
>     root ALL=(ALL) ALL
> 
> 



Logo abaixo dela adicione o usuário com uma linha como esta:


> 

>     
>     usuário ALL=(ALL) ALL
> 
> 



Sendo que usuário é o nome do usuário que passa a contar com a permissão para dar sudo.

Aqui tem uma tela que mostra eu _me dando_ o privilégio de ser um sudoer:

[![](http://adilsoncarvalho.com.br/blog/wp-content/uploads/2010/07/visudo.png)](http://adilsoncarvalho.com.br/blog/wp-content/uploads/2010/07/visudo.png)

Para encerrar, após editar pressione ^X e então Y.

_Job done!_
