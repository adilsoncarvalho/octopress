---
comments: true
date: 2011-08-09 13:05:11
layout: post
slug: war-muito-grande-para-fazer-deploy-no-tomcat7
title: War muito grande para fazer deploy no Tomcat7
wordpress_id: 365
categories:
- HowTo
tags:
- jruby
- rails
- tomcat7
---

Eu estou começando a efetuar o deploy de uma aplicação Rails com JRuby e Tomcat 7.

Após usar o [Warbler](http://kenai.com/projects/warbler/pages/Home) para criar um warfile para deploy, o manager do Tomcat disparou o seguinte erro:


**org.apache.tomcat.util.http.fileupload.FileUploadBase$SizeLimitExceededException**


Fácil, fácil. É só aumentar o tamanho máximo de upload no servidor. Mas a dúvida é, em qual xml obscuro tenho de mexer?


## Como resolver!





	
  * Procure pelo arquivo web.xml do manager (está em [tomcat7 directory]/webapps/manager/WEB-INF/web.xml)

	
  * Aumente os valores em max-file-size e max-request-size (o valor padrão é 50MB)




<multipart-config>




<!– 50MB max –>




<max-file-size>**52428800**</max-file-size>




<max-request-size>**52428800**</max-request-size>




<file-size-threshold>0</file-size-threshold>




</multipart-config>






	
  * Reinicie o Tomcat



