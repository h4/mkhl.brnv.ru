---
id: 502
title: 'Чиним ошибку «perl: warning: Setting locale failed.» в MacOS'
date: 2013-10-25T13:23:48+03:00
author: h4
layout: revision
guid: http://mkhl.brnv.ru/433-autosave-v1/
permalink: /433-autosave-v1/
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
    

**UPD:** в комментариях подсказали, что правильнее будет сделать

И перечитываем настройки:

    source ~/.bash_profile
    

или

    source ~/.zshrc