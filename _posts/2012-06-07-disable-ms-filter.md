---
id: 324
title: Отмена действия фильтра в IE
date: 2012-06-07T21:18:37+03:00
author: h4
layout: post
guid: http://mkhl.brnv.ru/?p=324
permalink: /disable-ms-filter/
categories:
  - Записи
---
Баловался с css-градиентами для кнопок (все же хотят быть няшными, как твитер и гитхаб). Для IE тоже добавил градиент через фильтр:

<pre>-ms-filter: "progid:DXImageTransform.Microsoft.gradient(
             startColorstr='#CBCBCB',
             endColorstr='#A7A7A7')";</pre>

Это все знают и умеют, и я бы не стал об этом писать. Но внезапно возникла необходимость отменить действие градиента в некоторых специфеских случаях&#8230;

Сначала я по привычке написал _-ms-filter: none;_ не такое правило не работает и нужно делать вот так, [по-майкрософтовски](http://msdn.microsoft.com/en-us/library/ie/ms532876(v=vs.85).aspx):

<pre>-ms-filter: "progid:DXImageTransform.Microsoft.gradient(enabled=false)";</pre>

Или всё-таки есть более простой и лаконичный способ?