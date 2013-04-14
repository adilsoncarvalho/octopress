---
comments: true
date: 2011-07-08 23:12:26
layout: post
slug: usando-o-afconvert-para-converter-arquivos-caf-em-mp3
title: Usando o afconvert para converter arquivos CAF em MP3
wordpress_id: 317
categories:
- HowTo
tags:
- caf
- Conversão
- macos
- mp3
---

Como sou bem noob em Mac, ao ver essa extensão [CAF](http://www.fileinfo.com/extension/caf), o que é isso??? Eu preciso compartilhar o áudio da reunião com uma colega e acredito que MP3 é uma escolha melhor.

Após dar uma _googlada_ para ver se tem como fazer isto sem usar outras ferramentas, eu descobri que existe o _afconvert_ que faz o trabalho.

Eu achei este [post](http://www.devdaily.com/mac-os-x/convert-caf-sound-file-aif-aiff-mp3-format) que mostra como converter CAF para AIF. Bacana, boa parte do caminho já estava andado. Contudo ele converte para AIF.

Mais uma _googlada_ e encontrei neste outro [post](http://pt.w3support.net/index.php?db=so&id=435349) os formatos para criar um MP3.

{% gist 1073217 to-mp3.sh %}

Eu aproveitei e alterei o outro script que faz estas conversões em lote para trocar de AIF para MP3.

{% gist 1073217 all-to-mp3.sh %}

Rápido e prático! :)
