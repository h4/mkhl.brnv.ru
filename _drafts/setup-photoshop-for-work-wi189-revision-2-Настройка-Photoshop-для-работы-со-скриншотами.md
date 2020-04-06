---
id: 194
title: Настройка Photoshop для работы со скриншотами
date: 2010-11-29T02:28:22+03:00
author: h4
layout: revision
guid: http://mkhl.brnv.ru/189-revision-2/
permalink: /189-revision-2/
---
При работе со скриншотами часто приходится масштабировать изображение целиком или отдельные его кусочки. Настройки масштабирования по умолчанию никуда не годятся, смотрите сами:

<div id="attachment_192" style="width: 450px" class="wp-caption alignnone">
  <a href="http://mkhl.brnv.ru/wp-content/uploads/2010/11/2010-11-29_0109292.png"><img aria-describedby="caption-attachment-192" class="size-full wp-image-192" title="Масштабирование графики" src="http://mkhl.brnv.ru/wp-content/uploads/2010/11/2010-11-29_0109292.png" alt="Масштабирование графики" width="440" height="182" srcset="https://mkhl.brnv.ru/wp-content/uploads/2010/11/2010-11-29_0109292.png 440w, https://mkhl.brnv.ru/wp-content/uploads/2010/11/2010-11-29_0109292-300x124.png 300w" sizes="(max-width: 440px) 100vw, 440px" /></a>
  
  <p id="caption-attachment-192" class="wp-caption-text">
    Режимы масштабирования графики
  </p>
</div>

Причина замыливания — включённое сглаживание. Оно помогает при использовании Photoshop по прямому назначению, то есть для обработки фотографий. Но при работе с пиксельной графикой нужно всё взять и поменять.

Идём в настройки Photoshop (Edit > Preferences > General или Photoshop > Prefeneces > General) и устанавливаем параметр Image Interpolation в значение «Nearest Neighbor». Нажимаем Ok и с этого момента Photoshop перестанет пытаться сглаживать пикселы при любом масштабировании, в том числе и при Free Transform. Стоит помнить, что нормальный результат возможен только при изменении масштаба в целое число раз (200%, 300% и т.д.).

Ну и естественно, никакого jpg при сохранении результата. Только png или gif.