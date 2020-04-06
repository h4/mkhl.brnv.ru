---
id: 794
title: Чиним Gitlab Pages при переименовании репозитория
date: 2020-02-03T14:12:18+03:00
author: h4
layout: post
guid: https://mkhl.brnv.ru/?p=794
permalink: '/%d1%87%d0%b8%d0%bd%d0%b8%d0%bc-gitlab-pages-%d0%bf%d1%80%d0%b8-%d0%bf%d0%b5%d1%80%d0%b5%d0%b8%d0%bc%d0%b5%d0%bd%d0%be%d0%b2%d0%b0%d0%bd%d0%b8%d0%b8-%d1%80%d0%b5%d0%bf%d0%be%d0%b7%d0%b8%d1%82%d0%be/'
categories:
  - Записи
---
Если в гитлабе переименовать репозиторий (или перенести его в другой неймспейс), то генератор GitLab Pages почему-то этого не замечает и делает сборку в неправильное место. Актуально для v12.6.3, как минимум. 

У меня получилось пофиксить проблему принудительным перезапуском генератора. Для этого записываем рандомное значение в `gitlab/gitlab-rails/shared/pages/.update:`

<pre class="wp-block-code"><code>head /dev/urandom | tr -dc A-Za-z0-9 | head -c 128 > /var/opt/gitlab/gitlab-rails/shared/pages/.update</code></pre>

После этого ещё раз запускаем пайплайн с Pages и проверяем, что всё работает.