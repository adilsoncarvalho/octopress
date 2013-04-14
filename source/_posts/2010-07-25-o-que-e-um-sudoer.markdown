---
comments: true
date: 2010-07-25 16:10:47
layout: post
slug: o-que-e-um-sudoer
title: O que é um sudoer?
wordpress_id: 58
categories:
- TechInfo
tags:
- Linux
- root
- sudoers
---

Antigamente (leia-se muito antigamente) a gente logava em nossas caixas linux diretamente como root para as tarefas administrativas (alguns sequer tinham outro usuário além do root).

Esse comportamento expunha o sistema a uma série de riscos, visto que o root não conhece limites de poder e autoridade.

Tem uma história (verídica) de um rapaz que administrava um sistema linux e veio correndo perguntar para uns colegas como que fazia para restaurar o diretório /bin que ele _acidentalmente_ apagou com um rm -f.

Não preciso nem falar que o rapaz estava no modo _camaleão psicodélico_, pois o rosto de trocava de cor a cada 15 segundos. Quando falaram que só restaurando o backup, àquele que por sinal ele não tinha, ele finalmente assumiu uma cor cadavérica.

Deve ser de situações como esta que surgiu a grande máxima do linux na atualidade


> Amigos não deixam amigos entrarem como root.


OK, mas as tarefas administrativas estão ai. Como resolver então? Dando ao usuário uma forma de rodar um processo momentâneamente com todo o esplendor e glória do root.

Mas para isto o usuário precisa ser um sudoer.

Um sudoer é um usuário que pode momentâneamente ganhar privilégios administrativos para efetuar algumas tarefas.

É o mesmo conceito adotado desde o Windows Vista, quando ele abre aquela janela pedindo sua confirmação para efetuar algo com privilégios administrativos. É o linux doando bons conceitos para todos.

Mas [como adicionar um usuário à lista de sudoers?](http://adilsoncarvalho.com.br/blog/como-adicionar-um-usuario-a-lista-de-sudoers-no-linux) É só clicar e ver.
