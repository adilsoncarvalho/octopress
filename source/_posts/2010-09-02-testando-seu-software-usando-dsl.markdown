---
comments: true
date: 2010-09-02 01:39:37
layout: post
slug: testando-seu-software-usando-dsl
title: Testando seu software usando DSL
wordpress_id: 141
categories:
- /I write code in .*?/gi
tags:
- BOO
- DSL
- Testes
---

A mais ou menos um ano, eu comecei a estudar formas de automatizar o teste de software. Seguindo indicações de amigos, acabei esbarrando nas UnitTests.


> Nesse momento eu vi a luz!


<!-- more -->Neste ano que se passou, fiz em teste muita coisa, usei [NUnit](http://www.nunit.org/), a TestUnit do VS, code coverage e assumi o papel _"da voz que clama no deserto"_ chamando os programadores com STD para a remissão dos seus fontes pela automação de testes.

Quem trabalha comigo bem sabe como os testes me deixaram um pouco paranóico, mas definitivamente muito mais feliz com os softwares que entrego.

Tivemos em Curitiba (acho que no mês passado) o [Café Ágil](http://adilsoncarvalho.com.br/blog/cafe-agil-em-curitiba-em-07-de-agosto-de-2010-sabado), um evento em que se falou de testes. Eu estava lá com o pessoal da [EBS](http://www.ebs.com.br/) (O Ivo e sua equipe), meu amigo [Binhara](http://twitter.com/binhara) e a [Mari](http://twitter.com/marileize) (uma GP que nasceu para ser ágil).

Eu e ela, parecendo nerds, sentamos onde? Na primeira fila claro, mas só para manter a fama, e eis que no meio da apresentação do [Klaus](http://twitter.com/klauswuestefeld) sobre as camadas de automação de teste que ele adotou no [Sneer](http://sovereigncomputing.net/), aconteceu algo diferente:


> Eu vi alguém acenando dentro da luz!


O Klaus estava demonstrando os testes para sua aplicação de computação soberana, quando ele chegou até os testes para um jogo que roda nela chamado [GO](http://pt.wikipedia.org/wiki/Go). GO é um jogo que se baseia em conquista territorial. Tem regras relativamente simples, mas que geram cenários interessantes para teste.

Imaginando um tabuleiro de 6 x 6, ele exibiu um código de teste que criava o tabuleiro, começava a por pedras brancas e pretas até que em um momento ele verificava se uma pedra tinha sumido por ter sido cercada pelas rivais.

Ao mostrar o código ele perguntou quem que achava fácil de entender. Eu e a Mari acenamos com a cabeça que sim. E ele falou que "para os que estão dizendo que sim, vocês não sabem o que estão falando!"

Ele logo em seguida mostrou outra forma de fazer o mesmo teste, usando somente tabuleiros montados em texto, algo como:

    
    . . . . . .   * pedra preta
    . . . . . .   + pedra branca
    . . * * . .
    . + . * . .
    . . + . . .
    . . . . . .


Ok que o primeiro, com o código eu já tinha achado fácil de entender, mas não tem como negar que essa representação visual é muito melhor. O que ele usou? Uma DSL. Uma camada que convertia os tabuleiros desenhados em texto nos testes codificados, assim quem definia os testes não precisava lidar com nada do código para poder se expressar no que ele queria.

Eu vi pela primeira vez, de forma muito prática o porque de usar uma DSL (domain specific language, ou, linguagem específica de domínio).

Ao invés de escrever os testes diretamente usando unit, eu posso criar (ou pegar uma ferramenta pronta) para trazer alguns dos meus testes para um nível mais elevado, e que sejam menos dependente do código fonte.

[![](http://adilsoncarvalho.com.br/blog/wp-content/uploads/2010/09/boo.png)](http://adilsoncarvalho.com.br/blog/wp-content/uploads/2010/09/boo.png)Eu me lembrei dos comentários do Binhara sobre a linguagem [BOO](http://boo.codehaus.org/) que foi desenvolvida pelo Rodrigo Oliveira, que tem uma série de [características](http://ayende.com/blog/archive/2007/12/17/the-boo-language.aspx) interessantes, dentre elas: gerar binário em .Net e permitir a extensão do seu compilador, ou seja, posso usá-la como base para escrever a minha linguagem.

[![](http://adilsoncarvalho.com.br/blog/wp-content/uploads/2010/09/rahien_cover150.jpg)![](http://www.assoc-amazon.com/e/ir?t=greycoast-20&l=as2&o=1&a=1933988606)](http://www.amazon.com/gp/product/1933988606?ie=UTF8&tag=greycoast-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=1933988606)Para dar uma acelerada na curva de aprendizado, acabei comprando agora a pouco da Manning o livro [DSLs in Boo: Domain Specific Languages in .NET](http://www.amazon.com/gp/product/1933988606?ie=UTF8&tag=greycoast-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=1933988606)![](http://www.assoc-amazon.com/e/ir?t=greycoast-20&l=as2&o=1&a=1933988606).

Lá se vão R$100,... mas citando um texto que li recentemente do próprio Klaus, o que só custa dinheiro é barato.

Mesmo que leve um ano para aprender, vai valer a pena.


> A cada dia que passa eu acredito menos em pessoas testando sistemas. Pessoas pensam, máquinas repetem, repetem rápido e exato. Não há lucro na troca de atribuição entre eles.


Preciso achar agora um projeto onde fazer meus estudos. Vai se divertido.
