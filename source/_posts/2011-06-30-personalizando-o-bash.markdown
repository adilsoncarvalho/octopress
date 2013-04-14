---
comments: true
date: 2011-06-30 21:06:31
layout: post
slug: personalizando-o-bash
title: Personalizando o bash
wordpress_id: 295
categories:
- HowTo
tags:
- bash
- Linux
- macos
---

Há dias eu ando criando coragem para modificar o prompt de comando do meu terminal.

O terminal, para quem não sabe, é aquela tela preta intimidadora, praticamente uma entidade do mundo antigo que faz piscar um cursor, aguardando por verbos arcanos. Sabendo conjuras apropriadas ele é dócil e prestativo.

Você poderá achar informações mais detalhadas no [Bash Reference Manual](http://www.gnu.org/software/bash/manual/bashref.html) e no [Prompt HOW-TO](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/).


## As variáveis do prompt


O prompt de comando possui quatro variáveis, uma para cada finalidade. São elas:



	
  * **PS1** é o prompt principal e tem como valor padrão '\s-\v\$ '

	
  * **PS2** é o prompt utilizado nos comandos multi-linha, e tem como valor padrão '> '

	
  * **PS3** é o prompt para o comando select, e tem como valor padrão '#? '

	
  * **PS4** é o prompt utilizado quando executando com a opção -x (debug). Ele será repetido várias vezes para indicar os níveis de identação do código em execução. Tem como padrão o valor '+'

	
  * **PROMPT_COMMAND** é interpretado como comando antes de cada exibição do seu prompt primário (sabe, o $PS1)




## Os parâmetros do prompt


Podemos colocar no prompt de comando uma série de valores para serem exibidos.

São eles:



	
  * **\a** aquele barulho irritante do terminal (quem usa meu Deus???) o caractere ASCII 7

	
  * **\d** a data no formato "dia da semana, mês e dia", algo como "_Tue May 26_"

	
  * **\D{format}** a data formatada no formato indicado (conforme strftime(3)). Caso não seja passado nada usa as configurações locais. Ambos { e } são obrigatórios

	
  * **\e** o caractere de escape ASCII (033)

	
  * **\h** o nome do host (até o primeiro .)

	
  * **\H** o nome completo do host

	
  * **\j** o número atual de tarefas sendo gerenciadas por este terminal

	
  * **\l** o nome do dispositivo do terminal do shell

	
  * **\n** nova linha

	
  * **\r** retorno de carro

	
  * **\s** o nome deste shell (o nome base em $0)

	
  * **\t** a hora atual no formato 24-hour HH:MM:SS

	
  * **\T** a hora atual no formato12-hour HH:MM:SS

	
  * **\@** a hora atual no formato12-hour am/pm

	
  * **\A** a hora atual no formato24-hour HH:MM

	
  * **\u** o nome do usuário atual

	
  * **\v** a versão do bash

	
  * **\V** o release do bash, incluindo a versão e o patch level

	
  * **\w** o diretório atualmente selecionado, com o $HOME abreviado com um ~

	
  * **\W** o nome base do diretório atualmente selecionado, com o $HOME abreviado com um ~

	
  * **\!** o número deste comando no histórico de comandos (a.k.a. .bash_history)

	
  * **\#** o número de comando deste comando

	
  * **\$** se o valor do UID é zero, um #, senão um $

	
  * **\nnn** o caractere respresentado pelo número octal nnn

	
  * **\\** a própria '\'

	
  * **\[** inicia uma seqüência de caracteres não imprimíveis (como cores e outros controles de terminal)

	
  * **\]** encerra uma seqüência de caracteres não imprimíveis




## Ser monocromático é chique (bem, foi, nos anos 50)


Para adicionar cores você precisa adicionar seqüências escapadas no seu prompt.

Para começar você deve iniciar com o marcador de início, que é **\e[** ou **\[\033[**, seguido pelo código da cor e encerrado com o caractere **m**.

Os códigos de cores são compostos por dois números. O primeiro indica se a cor será clara (**0**) ou escura (**1**) e o segundo é propriamente o código da cor.

São elas:



	
  * **Sem cor** 00m

	
  * **Black** 0;30

	
  * **Dark Gray** 1;30

	
  * **Blue** 0;34

	
  * **Light Blue** 1;34

	
  * **Green** 0;32

	
  * **Light Green** 1;32

	
  * **Cyan** 0;36

	
  * **Light Cyan** 1;36

	
  * **Red** 0;31

	
  * **Light Red** 1;31

	
  * **Purple** 0;35

	
  * **Light Purple** 1;35

	
  * **Brown** 0;33

	
  * **Yellow** 1;33

	
  * **Light Gray** 0;37

	
  * **White** 1;37


Para montar um código de cor é só fazer a composição. Digamos que estamos querendo o texto em verde escuro, a seqüência é **\e[0;32m**.


> Para remover a configuração de cor lembre-se de usar **\e[00m**




## Como testar o meu prompt até achar o ideal?




> Antes de mais nada, para você ver o código do seu prompt atual é só digitar echo $PS1


Para ir testando o seu prompt é só digitar **export PS1='my prompt escape codes here'**

O lado bom é que se você realmente estragar com ele, ele voltará ao normal quando você abrir um novo terminal.

Quando você encontrar o prompt dos seus sonhos, edite (ou crie) o arquivo ~/.bash_profile e adicione a linha acima dentro do arquivo.


## O meu terminal


Eu gosto de ter sempre à mão o caminho completo de onde estou no file system, com uma generosa linha para digitar meus comandos.

Para obter este efeito aqui ...

![Meu Terminal](http://adilsoncarvalho.com.br/blog/wp-content/uploads/2011/06/my-terminal.png)

... eu uso este prompt aqui ...


> export PS1='\n\[\033[0;36m\]\u@\h\[\033[00m\] :: \[\033[0;32m\]\w \[\033[01;33m\]\[\033[00m\]\n\$'




## Uma última coisa


Eu também uso [git](http://git-scm.com/) de monte, e é bom saber em qual _branch_ e se ele tem alterações pendentes ou não.

Mas isto mostro em outro post.
