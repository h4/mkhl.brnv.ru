---
id: 704
title: Клонирование из GitHub в WebStorm
date: 2015-12-24T10:44:31+03:00
author: h4
layout: revision
guid: http://mkhl.brnv.ru/702-revision-v1/
permalink: /702-revision-v1/
---
В WebStorm и все прочие IDE от JetBrains встроена интеграция с гитхабом. Например, можно клонировать репозиторий и создать проект не вводя лишних данных. Но, к сожалению, по умолчанию используется клонирование через https  – этот способ более универсален, но очень неудобен, если для работы с VCS используется не только gui, но и консоль. В этом случае терминал на каждый чих будет просить ввести пароль (в WS пароль от GH не спрашивается, если вы его сохранили в кейчейн или используете API Token).

Однако, это очень легко исправить: заходим в _Preferences > Version Control > GitHub_ и отмечаем галочкой «Clone git repositories using ssh». Всё, теперь новые репозитории будут клонироваться правильно.

[<img class="aligncenter size-full wp-image-703" src="http://mkhl.brnv.ru/wp-content/uploads/2015/12/2015-12-24-09-34-54-Default-Preferences.png" alt="2015-12-24 09-34-54 Default Preferences" width="789" height="542" srcset="https://mkhl.brnv.ru/wp-content/uploads/2015/12/2015-12-24-09-34-54-Default-Preferences.png 789w, https://mkhl.brnv.ru/wp-content/uploads/2015/12/2015-12-24-09-34-54-Default-Preferences-300x206.png 300w" sizes="(max-width: 789px) 100vw, 789px" />](http://mkhl.brnv.ru/wp-content/uploads/2015/12/2015-12-24-09-34-54-Default-Preferences.png)