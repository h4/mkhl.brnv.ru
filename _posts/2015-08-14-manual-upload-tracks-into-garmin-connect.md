---
id: 676
title: «Ручная» загрузка треков в Garmin Connect
date: 2015-08-14T12:00:26+03:00
author: h4
layout: post
guid: http://mkhl.brnv.ru/?p=676
permalink: /manual-upload-tracks-into-garmin-connect/
categories:
  - Записи
---
Сегодня утром у меня «моргнул» WiFi как раз во время синхронизации треков из моего Garmin Forerunner в Garmin Express на MacOS. Вроде бы ничего страшного, но софт у Гармина сильно хуже железок, поэтому треки с часов списались, а в «облако» не улетели. И при повторной синхронизации с работающим WiFi ничего не произошло. В общем, зажал Express мои треки.

Но меня так просто не проведёшь. Открываем Finder и переходим в каталог \`~/Library/Application Support/Garmin/Express/Registered Devices/\`. Там будет столько каталогов, сколько устройств у вас подключено в Garmin Express. У меня их два, а имена каталогов — это серийный номер железки, поэтому я ориентировался по картинке \`device_image.png\` внутри папки.

Переходим в каталог \`PendingSyncUploads\`, а в ней — в \`FIT\_TYPE\_4\` (или в \`FIT\_TYPE\_9\`, или в ту, которая соответствует типу активности, трек от которой мы ищем. И не спрашивайте меня, какой номер чему соответствует. Не знаю). Ищем нужный файл по его имени, имя — дата и время тренировки.

Теперь копируем этот файл и у копии добавляем расширение \`.fit\`, в моём случае \`2015-08-14 07/09/14 +0000\_360\` переименовался в \`2015-08-14 07/09/14 +0000\_360.fit\`. Файлы без расширения не получится залить на http://connect.garmin.com/

Теперь открываем http://connect.garmin.com/ и нажимаем кнопку загрузки активностей. Вот эту

[<img class="aligncenter wp-image-677 size-full" src="http://mkhl.brnv.ru/wp-content/uploads/2015/08/2015-08-14-10-55-22-Garmin-Connect.png" alt="2015-08-14 10-55-22 Garmin Connect" width="594" height="426" srcset="https://mkhl.brnv.ru/wp-content/uploads/2015/08/2015-08-14-10-55-22-Garmin-Connect.png 594w, https://mkhl.brnv.ru/wp-content/uploads/2015/08/2015-08-14-10-55-22-Garmin-Connect-300x215.png 300w" sizes="(max-width: 594px) 100vw, 594px" />](http://mkhl.brnv.ru/wp-content/uploads/2015/08/2015-08-14-10-55-22-Garmin-Connect.png)

В выпавшем списке выбираем «Upload Your Activity» и переходим на вкладку «Manual Upload». Ну а уже там выбираем наш *.fit файл и загружаем его.

Возможно, стоит почистить каталог \`PendingSyncUploads\`, чтобы не было дубликатов в будущем. Но что-то мне подсказывает, что Garmin Express не особо смотрит в эту папку.

&nbsp;