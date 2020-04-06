---
id: 197
title: Настройка Photoshop для работы со скриншотами
date: 2010-11-29T02:30:15+03:00
author: h4
layout: revision
guid: http://mkhl.brnv.ru/189-revision-4/
permalink: /189-revision-4/
---
При работе со скриншотами часто приходится масштабировать изображение целиком или отдельные его кусочки. Настройки масштабирования по умолчанию никуда не годятся, смотрите сами:

<div class="mceTemp">
  <dl id="attachment_192" class="wp-caption alignnone" style="width: 450px;">
    <dt class="wp-caption-dt">
      <a href="http://mkhl.brnv.ru/wp-content/uploads/2010/11/2010-11-29_0109292.png"><img class="size-full wp-image-192" title="Масштабирование графики" src="http://mkhl.brnv.ru/wp-content/uploads/2010/11/2010-11-29_0109292.png" alt="Масштабирование графики" width="440" height="182" srcset="https://mkhl.brnv.ru/wp-content/uploads/2010/11/2010-11-29_0109292.png 440w, https://mkhl.brnv.ru/wp-content/uploads/2010/11/2010-11-29_0109292-300x124.png 300w" sizes="(max-width: 440px) 100vw, 440px" /></a>
    </dt>
  </dl>
</div>

Причина замыливания — включённое сглаживание. Оно помогает при использовании Photoshop по прямому назначению, то есть для обработки фотографий. Но при работе с пиксельной графикой нужно всё взять и поменять.

Идём в настройки Photoshop (_Edit > Preferences > General_ или _Photoshop > Prefeneces > General_) и устанавливаем параметр **Image Interpolation** в значение «**Nearest Neighbor**». Нажимаем **Ok** и с этого момента Photoshop перестанет пытаться сглаживать пикселы при любом масштабировании, в том числе и при Free Transform. Стоит помнить, что нормальный результат возможен только при изменении масштаба в целое число раз (200%, 300% и т.д.).

Ну и естественно, никакого jpg при сохранении результата. Только png или gif.