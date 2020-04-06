---
id: 430
title: Mime-тип для woff-шрифтов
date: 2013-07-15T18:08:31+03:00
author: h4
layout: revision
guid: http://mkhl.brnv.ru/428-autosave/
permalink: /428-autosave/
---
По умолчанию Nginx отдаёт woff-шрифты с mime-type: application/octet-stream. Chrome это дело замечает и начинает паниковать в консоли, а меня эта паника раздражает.

Всего-то и делов, казалось бы — исправить `/etc/nginx/mime.types` и рестартовать nginx. Но не тут-то было.

[Спецификация предлагает](http://www.w3.org/TR/WOFF/#appendix-b) указывать `application/font-woff`, однако Chrome продолжает паниковать и успокаивается только после указания `application/x-font-woff` в `/etc/nginx/mime.types`.

А мне уже надоело каждый раз рыскать по интернетам в поисках правильного значения.

**UPD:** проблема наблюдается только в стабильном Chrome. Ни в Яндекс.Браузере, ни в Opera 15, ни в Chrome Canary этой ошибки не видно.