---
id: 451
title: Mime-тип для woff-шрифтов
date: 2013-03-26T18:45:50+03:00
author: h4
layout: revision
guid: http://mkhl.brnv.ru/428-revision-2/
permalink: /428-revision-2/
---
По умолчанию Nginx отдаёт woff-шрифты с mime-type: application/octet-stream. Chrome это дело замечает и начинает паниковать в консоли, а меня эта паника раздражает.

Всего-то и делов, казалось бы — исправить `/etc/nginx/mime.types` и рестартовать nginx. Но не тут-то было.

[Спецификация предлагает](http://www.w3.org/TR/WOFF/#appendix-b) указывать `application/font-woff`, однако Chrome продолжает паниковать и успокаивается только после указания `application/x-font-woff` в `/etc/nginx/mime.types`.

А мне уже надоело каждый раз рыскать по интернетам в поисках правильного значения.