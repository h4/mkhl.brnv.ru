---
id: 418
title: Установка Nginx на MacOS. Версия вторая, исправленная
date: 2013-02-18T12:48:47+03:00
author: h4
layout: post
guid: http://mkhl.brnv.ru/?p=418
permalink: /nginx-on-macos-v2/
categories:
  - Записи
---
Я уже писал [про установку nginx на MacOS](http://mkhl.brnv.ru/nginx-o-macos-lion/). Однако, некоторые вещи я теперь делаю слегка иначе.

> Почему не HomeBrew|MacPorts?

Мне не нравятся эти прослойки. Если уж делать в консоли — делать по-настоящему. Порты за собой тащат кучу непонятно чего, а в Homebrew всё ставится в /etc/Celluar и об этом нужно постоянно помнить. Хочется, чтобы всё было одинаково, и на ноуте, и на удалённых серверах.

## Установка [PCRE](http://ru.wikipedia.org/wiki/PCRE)

Без этой библиотеки вообще мало что можно собрать, поэтому, если её ещё нет, ставим:

    $ cd ~/Downloads
    $ curl -O ftp://ftp.csx.cam.ac.uk/pub/software/programming/pcre/pcre-8.30.tar.gz
    $ tar xvf pcre-8.30.tar.gz
    $ cd pcre-8.30
    $ ./configure
    $ make
    $ sudo make install
    

## Ставим Nginx

Nginx регулярно обновляется, поэтому стоит зайти на [nginx.org](http://nginx.org) и узнать номер последней стабильной версии (нестабильные на MacOS лучше не ставить %).

    $ cd ~/Downloads
    $ curl -O http://www.nginx.org/download/nginx-1.2.7.tar.gz
    $ tar xvf nginx-1.2.7.tar.gz
    $ cd nginx-1.2.7
    $ ./configure
    $ make
    $ sudo make install
    

## Управление сервером

Запуск:

    sudo /usr/local/nginx/sbin/nginx
    

Проверка конфигурации:

    sudo /usr/local/nginx/sbin/nginx -t
    

Перезапуск и остановка:

    $ sudo /usr/local/nginx/sbin/nginx -s reload
    $ sudo /usr/local/nginx/sbin/nginx -s reopen
    $ sudo /usr/local/nginx/sbin/nginx -s stop
    

P.S.: это скорее заметка для самого себя, далеко не всегда стоит собирать веб-сервер из исходников.