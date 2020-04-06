---
id: 390
title: PIL на MacOS 10.8
date: 2013-01-13T19:36:20+03:00
author: h4
layout: revision
guid: http://mkhl.brnv.ru/387-revision-3/
permalink: /387-revision-3/
---
Мне пришлось переустановить ситсему на макбуке (никогда не ставьте систему на CaseSensetive раздел, если хотите работать с поделками от Adobe) и, естественно, при устновке вируальных окружений для Django-проектов я словил зависимость полей ImageField от PIL:

       raise CommandError("One or more models did 
    not validate:\n%s" % error_text)
    django.core.management.base.CommandError: 
    One or more models did not validate:
    conference.person: "photo": To use ImageFields, 
    you need to install the Python Imaging Library. 
    Get it at http://www.pythonware.com/products/pil/ .
    

Ок, ставим PIL командой `pip install pil`, но у нас всё равно всё работает не так, как нужно — нет поддержки JPEG:

* * *

    --- TKINTER support available
    *** JPEG support not available
    --- ZLIB (PNG/ZIP) support available
    *** FREETYPE2 support not available
    *** LITTLECMS support not available
    --------------------------------------------------------------------
    

Всё дело в том, что в изначальную поставку Mac OS 10.8 (и в более ранние — тоже) не входит библиотека libjpeg. Чтобы это исправить — нужно скачать исходники и собрать их. При этом нужно быть уверенным в том, что в системе уже стоит компилятор C. Если система свежая, то его не будет и собирать будет нечем.

Можно либо скачать много гигабайт XCode и поставить _Command Line Tools_ (Preferences > Downloads), либо зайти на [developer.apple.com/downloads/index.action](https://developer.apple.com/downloads/index.action) и скачать образ на 110 Мб (потребуется Apple Developer ID, бесплатно).

Теперь, будучи во всеоружии открываем в любимом браузере [www.ijg.org/files/](http://www.ijg.org/files/) и выбираем архив посвежее (сегодня я взял jpegsrc.v9.tar.gz). Дальше работаем в терминале:

    $ tar xvf jpegsrc.v9.tar.gz
    $ cd jpeg-9/
    $ ./configure
    $ sudo make
    $ sudo make install
    

Перевожу на человеческий язык: распаковываем архив и переходим в него; выполняем предварительные настройки и собираем библиотеку от лица суперпользователя.

Теперь, наконец-то, мы можем установить PIL в нужной нам конфигурации командой `pip install pil` (перед этим нужно удалить неудачную сборку командой `pip uninstall pil` и запустить Django.