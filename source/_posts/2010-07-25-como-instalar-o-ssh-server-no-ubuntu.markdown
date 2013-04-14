---
comments: true
date: 2010-07-25 15:07:43
layout: post
slug: como-instalar-o-ssh-server-no-ubuntu
title: Como instalar o SSH server no Ubuntu?
wordpress_id: 48
categories:
- HowTo
tags:
- git
- Linux
- ssh
---

O serviço SSH permite que você efetue conexões seguras com uma máquina linux sem que exista o perigo de interceptação de informações como pode ocorrer quando usando um serviço telnet.

Instalar um servidor ssh é fácil. Basta digitar no prompt do console:


> 

>     
>     sudo apt-get install openssh-server openssh-client
> 
> 



Isto instalará ambos, o servidor e o cliente. Você pode ver qual versão está instalada digitando:


> 

>     
>     ssh -V
> 
> 



Algumas coisas importantes para se saber:


> Os arquivos de configuração ficam em /etc/ssh

> 
> 
	
>   * Arquivo de configuração do cliente:

>     
>     /etc/ssh/ssh_config
> 
> 

> 
	
>   * Arquivo de configuração do servidor:
> 

>     
>     /etc/ssh/sshd_config
> 
> 




E ainda...


> O script de serviço é o

>     
>      /etc/init.d/ssh
> 
> 

> 
> 
	
>   * Para iniciar o servidor:
> 

>     
>     sudo /etc/init.d/ssh start
> 
> 
	
>   * Para parar o servidor:
> 

>     
>     sudo /etc/init.d/ssh stop
> 
> 
	
>   * Para reiniciar o servidor:
> 

>     
>     sudo /etc/init.d/ssh restart
> 
> 
	
>   * Para verificar o estado do servidor:
> 

>     
>     /etc/init.d/ssh status
> 
> 




Um último comentário:

Sempre que quiser chamar o script de serviço, que interage como  sshd, utilize o caminho completo até ele, pois o cliente do serviço também se chama ssh e ele aparece no path antes, o que fará com que ele sempre seja chamado primeiro.

Me toquei disto depois de muitas vezes receber uma resposta não esprada para um comando ssh restart.
