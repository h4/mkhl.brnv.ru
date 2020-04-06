---
id: 297
title: Nginx на MacOS Lion
date: 2012-04-09T01:27:23+03:00
author: h4
layout: post
guid: http://mkhl.brnv.ru/?p=297
permalink: /nginx-o-macos-lion/
categories:
  - Записи
---
**Заметка устарела.** Читайте [обновлённую версию](http://mkhl.brnv.ru/nginx-on-macos-v2/).

Сегодня снова ставил nginx на ноутбук. Поскольку никто не даст гарантии, что это не придётся делать снова — оставлю это здесь, почти всё делается в терминале и при наличии XCode. Сначала ставим PCRE, без него никак.

    cd ~/Downloads
    curl ftp://ftp.csx.cam.ac.uk/pub/software/programming/pcre/pcre-8.30.tar.gz &gt; pcre.tar.gz
    tar xvf pcre.tar.gz
    ./configure
    make
    sudo make install 
    

А теперь, собственно NGinx:

    curl http://www.nginx.org/download/nginx-1.0.14.tar.gz &gt; nginx-1.0.14.tar.gz
    tar xvf nginx-1.0.14.tar.gz
    ./configure --prefix=/usr/local
    make
    sudo make install
    

Запуск:

    sudo /usr/local/sbin/nginx
    

Перезапуск:

    killall nginx