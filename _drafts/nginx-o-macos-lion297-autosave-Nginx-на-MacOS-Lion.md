---
id: 421
title: Nginx на MacOS Lion
date: 2013-02-18T12:51:19+03:00
author: h4
layout: revision
guid: http://mkhl.brnv.ru/297-autosave/
permalink: /297-autosave/
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
    

./configure &#8212;prefix=/usr/local  
make  
sudo make install Запуск:

<pre>sudo /usr/local/sbin/nginx</pre>

Перезапуск:

<pre>killall nginx</pre>