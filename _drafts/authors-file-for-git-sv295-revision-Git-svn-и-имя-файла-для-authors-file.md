---
id: 296
title: Git-svn и имя файла для authors-file
date: 2012-02-13T12:28:27+03:00
author: h4
layout: revision
guid: http://mkhl.brnv.ru/295-revision/
permalink: /295-revision/
---
Так сложилось, что в Бегущем городе вся разработка ведётся через svn и на гит переходить никто не собирается. Ну а мне удобнее работать с локальным репозиторием и сливать пачку изменений вечером. Что же делать, как же быть?

Всё просто, давно есть интеграция **git-svn**, и можно [почитать вот эту статью](http://leonid.shevtsov.me/ru/perenos-svn-repozitariya-v-git), например.

Но, когда я сегодня вытаскивал очередной репозиторий, то получил такое вот сообщение об ошибке:

<pre>Can't open ~/Dropbox/runcity/svn-authors No such file or directory</pre>

Путь к файлу верный, естественно. Минутное замешательство и методом научного тыка выясняем, что путь к файлу с авторами коммитов должен быть **абсолютным**. Меняем на

<pre>svn clone -s --authors-file=/Volumes/Home/Dropbox/runcity/svn-authors http://svn-server.ner/our-repo</pre>

и вытягиваем нужный репозиторий.

&nbsp;