---
id: 466
title: Счётчик метрики в репозитории на гитхабе
date: 2013-08-07T23:29:50+03:00
author: h4
layout: post
guid: http://mkhl.brnv.ru/?p=466
permalink: /ya-metrika-on-github-repo/
categories:
  - Записи
---
В целях повышения ЧСВ решил вставить счётчик Яндекс.Метрики в [README.md](https://github.com/h4/git-tools). Решил — и вставил. Заодно узнал немного нового.

Прежде всего, решил вставить только гиф-счётчик. Чтобы не засорять код, да и, скорее всего, JS работать всё равно не будет. Не проверял.

Яндекс отдаёт код вида `<img src="//mc.yandex.ru/watch/12345678" alt="" />`. Он не работает. Обратите внимание на протокол адреса картинки — это не ошибка, а военная хитрость. Означает — бери тот же протокол, что и у основной страницы. Вот только у парсера markdown&#8217;а сносит крышу и показывается битая картинка.

Понимаем, что нужно указать протокол явно. Это просто — `http://mc.yandex.ru/watch/12345678`, и тут-то гитхаб совершает магию и заменяет адрес картинки на строку вида:

    https://github-camo.global.ssl.fastly.net/d93...458/687...832
    

Снова обратим внимание на протокол. На гитхабе всё (ну или почти всё) работает через `https`, поэтому внешние ресурсы, запрашиваемые по `http` проксируются. Если я всё правильно понимаю, это делается для того, чтобы браузеры не устраивали панику «на этой https странице есть ресурсы, загружаемые по http». В принципе, такой код работает, и на этом можно было бы остановиться. Но «явное лучше, чем неявное», поэтому идём дальше.

Попытка запросить счётчик по адресу `https://mc.yandex.ru/watch/12345678` завершилась кодом 200, а в панели метрики зарегистрирован хит. Ура, всё работает. Только код `<img src="https://mc.yandex.ru/watch/12345678" alt="" />` в markdown-файле выглядит странно (а у нас же публичный репозиторий, все дела). Так что пишем расово-верный код:

    !["Yandex.Metrika counter"](https://mc.yandex.ru/watch/22011982) 
    

и начинаем яростно рефрешить страницу дашборда в Метрике.

PS. Метрика ожидает, что код будет стоять на «сайте» и не даёт код для адреса вида `https://github.com/h4/git-tools`. Не проблема, ломаем систему указав `http://github.com` в качестве адреса сайта. И ничего, что «на главной странице сайта счётчик не обнаружен».