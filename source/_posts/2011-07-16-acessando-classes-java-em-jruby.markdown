---
comments: true
date: 2011-07-16 22:13:54
layout: post
slug: acessando-classes-java-em-jruby
title: Acessando classes java em jruby
wordpress_id: 325
categories:
- /I write code in .*?/gi
- HowTo
tags:
- integration
- java
- jruby
- ruby
---

[caption id="attachment_339" align="alignleft" width="235" caption="Java and Ruby"][![Java and Ruby](http://adilsoncarvalho.com.br/blog/wp-content/uploads/2011/07/jruby1.png)](http://adilsoncarvalho.com.br/blog/wp-content/uploads/2011/07/jruby1.png)[/caption]

Integrar é preciso.

Em um ambiente de produção moderno não há muito espaço para a uniformidade tecnológica. É quase certo que você terá _de tudo um pouco_ ao entregar uma solução.

Por uma necessidade destas eu estou precisando integrar umas aplicações em java com ruby. Está sendo _pra lá_ de divertido!


## Minha classe java


Para poder mostrar como fazer, vamos antes criar uma classe bem simples em java para ser consumida em [jruby](http://www.jruby.org/).

[gist id=1077172 file=Calculator.java]

É uma calculadora muito simples. Na verdade ela somente adiciona dois valores.

Para compilar e gerar o jar basta seguir os passos abaixo:

[gist id=1077172 file=smallest-jar-creation.sh]

Eu não tinha nem idéia de como criar um jar até ler o post [Creating an executable jar file](http://www.skylit.com/javamethods/faqs/createjar.html).

Mais fácil impossível!


## Preparando o script jruby


Basicamente você pode consumir uma classe java de três formas:



	
  * Diretamente (nomes completos de pacotes a cada uso)

	
  * Incluindo a classe no object

	
  * Incluindo um pacote dentro de um módulo ruby




### Ganhando "super-poderes"




Existe um passo comum a todas elas para permitir o acesso às classes java no ruby:




> 

> 
> require 'java'




Ao efetuar este require você terá uma série de métodos auxiliares que deixarão a sua vida muito mais simples para efetuar a integração.




### Chamando um jar


OK! Efetuamos o require do java, e temos tudo o que precisamos para consumir uma classe, agora precisamos indicar o jar onde nossa classe está.

Isto é feito pelo comando **require**. Você não precisa colocar a extensão .jar, ele automáticamente procurará tanto arquivos .rb quanto .jar, sendo que o seu jar deve ou estar no CLASSPATH ou na árvore de diretórios do consumidor.

Logo, requires como  'lib/SimplestJar' ou '../../SimplestJar' são válidos.


> Importante, você somente precisa dar require nos jars que contém classes que você consome diretamente. As dependências serão automaticamente carregadas!




## Consumindo a classe




### Diretamente (nomes completos de pacotes a cada uso)


É a forma favorita dos masoquistas de plantão.

Para acessar uma classe java, você precisa iniciar a chamada com o módulo Java:: seguido do caminho completo nos pacotes até a classe.

Como desenvolvedores java tem punhos de aço (principalmente os da [ASF](http://www.apache.org/)) você pode se preparar para usar namespaces muuuito longos.


### Incluindo a classe no object


Mesmo quando no irb, estamos em um contexto de uma classe. (É só digitar self.class para descobrir de quem).

Assim, você pode uma única vez fazer esta inclusão e em diante a classe estará disponível diretamente pelo nome dela.

Para fazer a inclusão utilize o comando include_class usando o Java:: seguido do caminho completo até a classe.


### Incluindo o pacote em um módulo ruby


Sempre é bom poder organizar as coisas.

Neste projeto que estou fazendo, eu quero simplificar os trezentos mil pacotes em uns quatro ou cinco módulos. Não há razão alguma justificável para termos mais.

Para isso dentro do módulo você pode usar o método import_package para vincular as classes java ao seu módulo ruby.


## O fonte completo


[gist id=1077172 file=calculator.rb]


## Conclusão


Poder consumir classes java dentro do jruby somente fazem crescer as possibilidade de ter a um lado uma linguagem moderna, flexível e produtiva com toda a estabilidade e escalabilidade do java.

Preciso fazer uns testes destes usando [ironruby](http://ironruby.net/).
