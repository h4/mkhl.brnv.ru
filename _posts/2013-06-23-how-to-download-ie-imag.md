---
id: 442
title: Как скачать образ виртуалки с Modern.ie если не качается
date: 2013-06-23T23:34:56+03:00
author: h4
layout: post
guid: http://mkhl.brnv.ru/?p=442
permalink: /how-to-download-ie-imag/
categories:
  - Записи
---
Microsoft – большие молодцы, запустили сервис [modern.ie](http://modern.ie/) с которого можно скачать разнообразнейшие образы виртуалок с IE. Вот только уже больше недели образ Win7+IE 10 для VirtualBox под Windows не качается. Вообще никак.

Наверно, нужно написать письмо в Microsoft, чтобы они починили свой CDN, но мне насктолько лень, что я нашёл обходной путь.

Есть у меня виртуалочка в [digitalocean](http://digitalocean.com/), физически расположенная в Амстердаме. И так оказалось, что европейский сектор CDN у Microsoft работает на ура и у меня получилось скачать нужные мне файлы wfget&#8217;ом.

Хочется научиться скачивать файлы напрямую с удалённой машины, наверняка какое-нибудь ssh-туннелирование это умеет, но мне снова лень.

**UPD:** Утро вечера мудренее, поэтому нашёл более простое решение — прописал в `/etc/hosts` ip-адрес сервера с образами, который резолвится на амстердамской машинке:

    94.245.70.112   az412801.vo.msecnd.net
    

Естественно, из-за разных сетевых задержек файлы качаются медленнее, чем это было бы с российской подсетью. Но зато качаются.