---
comments: true
date: 2010-10-21 13:07:09
layout: post
slug: usando-dsl-para-simplificar-os-testes-unitarios
title: Usando DSL para simplificar os testes unitários
wordpress_id: 210
categories:
- /I write code in .*?/gi
- Just on my mind
tags:
- C#
- DSL
---

A primeira vez que vi em ação uma DSL for no Café Ágil que teve aqui em Curitiba, quando o Klaus demonstrou como eles testavam um jogo para o Sneer chamado Go. Eu comentei sobre isso no meu post [Testando seu software usando DLS](http://adilsoncarvalho.com.br/blog/testando-seu-software-usando-dsl).

Naqueles dias eu estava na _mais absoluta ignorância_ sobre o assunto. Agora eu já progredi e estou na _ligeira ignorância_ sobre o assunto, tanto é que estou começando a poder aplicar as idéias nos cenários de teste que faço.

Eu quero compartilhar um teste que simplifiquei ao utilizar (algo que acho que é) uma DSL.<!-- more -->

A idéia é que ao invés de ficar codificando um monte de linhas para validar se o aplicativo estava fazendo o que se espera dele, você troca isso por uma linguagem que seja específica para o problema.

No meu cenário, eu tenho de validar uma condição de repasse. Ou seja: imagine o seguinte encadeiamento:

    
    aaa
     ^
     |
     |
    bbb
     ^
     |
     |
    ccc


**Qual a idéia?**

Sempre que ccc for solicitado e não estiver disponível, eu verifico bbb, mas se bbb também não estiver eu tento aaa, e assim por diante, até achar um que esteja disponível ou chegue em um para o qual eu não tenha mais como redirecionar.

**Como que eu testo esse mecanismo?**

Com uma série de asserts baseando-se nos possíveis cenários, com códigos como este abaixo:

    
    [TestMethod]
    public void ObterCanalDisponivel_CentralCanalOfflineMasNaoDeveUsarRepasse_NãoEfetuaRepasse()
    {
    	var centralcanal = new CentralCanal();
    	var fila = new Fila();
    	var canaldisponivel = new CanalDisponivel();
    
    	mock.Setup(foo => foo.CentralCanal2CanalDisponivel(centralcanal)).Returns(canaldisponivel);
    	mock.Setup(foo => foo.GerenciadorChat.Filas.ObterAtiva(canaldisponivel)).Returns(fila);
    	mock.Setup(foo => foo.ObterSituacaoCanal(fila)).Returns(CanalDisponivel.SituacaoEnum.Offline);
    
    	var expected = canaldisponivel;
    	var actual = target.ObterCanalDisponivel(centralcanal, false);
    
    	Assert.AreEqual(expected, actual);
    }


Ok, ele faz o trabalho, mas eu mesmo que o escrevi terei dificuldades em amanhã explicar a regra que ele está validando, e o mais importante:


> em um arquivo com uma dúzia deles, quais regras estou validando?


**A solução**

Criar algo que me proteja dos detalhes do teste e me deixe focar no que a classe precisa verdadeiramente fazer.

Para isso criei este fragmento aqui:

    
    # Script da DSL de Testes para ObterCanalDisponivel
    # Finalidade: Validar a execução das regras de repasse entre centrais
    #
    # ID          - Número do caso de teste
    #
    # Solicitada  - a situação da central/canal que se deseja acessar
    #               Valores possíveis: online/offline
    #
    # Alternativa - a situação da central/canal que vai atender quando a solicitada
    #               estiver offline
    #               Valores possíveis: online/offline ou deixe vazio se não tiver
    #                                  uma central alternativa disponível
    #
    # Selecionada - a central/canal que deve ser escolhida neste cenário
    #               Valores possíveis: Selecionada/Alternativa
    #
    #  ID  Solicitada  Alternativa  Selecionada
    #  --  ----------  -----------  -----------
    	1  online                   Solicitada
    	2  online      online       Solicitada
    	3  online      offline      Solicitada
    	4  offline                  Solicitada
    	5  offline     online       Alternativa
    	6  offline     offline      Solicitada


Esse script me explica o que entra e o que sai, permitindo ver de forma fácil e centrada os comportamentos que espero da minha classe.

Para testar todos ele eu agora somente preciso usar algo assim:

    
    [TestMethod]
    public void ObterCanalDisponivel_CasosDeTeste()
    {
    	var script =
    		@"
    		# Script da DSL de Testes para ObterCanalDisponivel
    		# Finalidade: Validar a execução das regras de repasse entre centrais
    
                    (... a mesma coisa do quadro acima...)
    
    		";
    
    	foreach (var teste in TesteRedirecionamentoDSL.Parse(script))
    	{
    		TesteRedirecionamentoDSL.ExecutarTeste(teste);
    	}
    }




> A classe _TesteRedirecionamentoDSL_ tem somente umas 100 linhas, é super simples, e usa uma expressão regular para interpretar o script inteiro.





Internamente ela repete o primeiro código que eu mostrei, mas como todo o trabalho de setup e verificação dos asserts fica escondido de mim, eu só me preocupo com os detalhes da regra.

Eu ainda escrevi alguns testes complementares para questões mais específicas, mas todos os testes de regra são centrados neste script.

![](http://adilsoncarvalho.com.br/blog/wp-content/uploads/2010/10/teste-com-dsl.png)
