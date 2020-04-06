---
id: 189
title: Настройка Photoshop для работы со скриншотами
date: 2010-11-29T02:28:22+03:00
author: h4
layout: post
guid: http://mkhl.brnv.ru/?p=189
permalink: /setup-photoshop-for-work-wi/
categories:
  - Записи
---
При работе со скриншотами часто приходится масштабировать изображение целиком или отдельные его кусочки. Настройки масштабирования по умолчанию никуда не годятся, смотрите сами:

[<img class="alignnone size-full wp-image-198" title="Режимы масштабирования" src="http://mkhl.brnv.ru/wp-content/uploads/2010/11/2010-11-29_0109293.png" alt="" width="440" height="182" srcset="https://mkhl.brnv.ru/wp-content/uploads/2010/11/2010-11-29_0109293.png 440w, https://mkhl.brnv.ru/wp-content/uploads/2010/11/2010-11-29_0109293-300x124.png 300w" sizes="(max-width: 440px) 100vw, 440px" />](http://mkhl.brnv.ru/wp-content/uploads/2010/11/2010-11-29_0109293.png)

Причина замыливания — включённое сглаживание. Оно помогает при использовании Photoshop по прямому назначению, то есть для обработки фотографий. Но при работе с пиксельной графикой нужно всё взять и поменять.

Идём в настройки Photoshop (_Edit > Preferences > General_ или _Photoshop > Prefeneces > General_) и устанавливаем параметр **Image Interpolation** в значение «**Nearest Neighbor**». Нажимаем **Ok** и с этого момента Photoshop перестанет пытаться сглаживать пикселы при любом масштабировании, в том числе и при _Edit > Free Transform_. Стоит помнить, что нормальный результат возможен только при изменении масштаба в целое число раз (200%, 300% и т.д.).

Ну и естественно, никакого jpg при сохранении результата. Только png или gif.