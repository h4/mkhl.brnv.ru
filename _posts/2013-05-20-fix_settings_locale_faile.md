---
id: 433
title: 'Чиним ошибку «perl: warning: Setting locale failed.» в MacOS'
date: 2013-05-20T14:04:58+03:00
author: h4
layout: post
guid: http://mkhl.brnv.ru/?p=433
permalink: /fix_settings_locale_faile/
categories:
  - Записи
---
Внезапно на рабочем маке стала появляться вот такая ошибка при работе с `git` в терминале:

    perl: warning: Setting locale failed.
    perl: warning: Please check that your locale settings:
            LANGUAGE = "en_US:en",
            LC_ALL = (unset),
            LC_CTYPE = "ru_RU.UTF-8",
            LANG = "en_US.UTF-8"
        are supported and installed on your system.
    perl: warning: Falling back to the standard locale ("C").
    

В интернетах есть предложение выключить галку автодетекта локалей в настройках _Terminal.app_/_iTerm.app_. Это решение прекрасно работает для тех, кто пишет только латиницей. Но я пишу комментарии к коммитам на русском и при отключенном автодетекте локалей русские буквы превращаются в непонятно что.

Есть второе решение, и оно гораздо более правильное, на мой взгляд.

Добавляем в `~/.bash_profile` или в `~/.zshrc` эти две строчки:

    export LC_CTYPE=en_US.UTF-8
    export LC_ALL=en_US.UTF-8
    

**UPD:** в комментариях подсказали, что правильнее будет сделать так:

    export LC_CTYPE=en_US.UTF-8
    export LC_TELEPHONE=en_US.UTF-8
    

И перечитываем настройки:

    source ~/.bash_profile
    

или

    source ~/.zshrc