---
id: 298
title: Nginx на MacOS Lion
date: 2012-04-09T01:26:53+03:00
author: h4
layout: revision
guid: http://mkhl.brnv.ru/297-revision/
permalink: /297-revision/
---
Сегодня снова ставил nginx на ноутбук. Поскольку никто не даст гарантии, что это не придётся делать снова — оставлю это здесь, почти всё делается в терминале и при наличии XCode.

Сначала ставим PCRE, без него никак.

<pre>cd ~/Downloads
curl ftp://ftp.csx.cam.ac.uk/pub/software/programming/pcre/pcre-8.30.tar.gz &gt; pcre.tar.gz
tar xvf pcre.tar.gz
./configure
make
sudo make install</pre>

А теперь, собственно NGinx:

<pre>curl http://www.nginx.org/download/nginx-1.0.14.tar.gz &gt; nginx-1.0.14.tar.gz
tar xvf nginx-1.0.14.tar.gz
./configure --prefix=/usr/local
make
sudo make install</pre>

Запуск:

<pre>sudo /usr/local/sbin/nginx</pre>

Перезапуск:

<pre>killall nginx</pre>