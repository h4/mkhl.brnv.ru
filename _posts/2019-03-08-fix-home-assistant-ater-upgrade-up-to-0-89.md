---
id: 772
title: Исправление конфигурации Home Assistant после обновления до v0.89
date: 2019-03-08T15:32:14+03:00
author: h4
layout: post
guid: https://mkhl.brnv.ru/?p=772
permalink: /fix-home-assistant-ater-upgrade-up-to-0-89/
categories:
  - Записи
---
Всякие умные девайсы дома интегрированы в удобную штуку – [Home Assistant](https://www.home-assistant.io/), а само приложение крутится в докер-контейнере на моём домашнем Linux-сервере. Home Assistant релизится каждые две недели, я слежу за их обновлениями через RSS и обновляю всё дома простым перезапуском сервиса.

Обычно всё проходит гладко, но вот с при обновлении на v0.89 всё сломалось, о чём мне заботливо сообщил Uptime Robot. Пошёл смотреть логи, там было что-то странное:

<pre>INFO (MainThread) [homeassistant.core] Starting Home Assistant
ERROR (MainThread) [homeassistant.core] Error doing job: Task exception was never retrieved
 Traceback (most recent call last):
   File "/usr/src/app/homeassistant/core.py", line 1110, in async_call
     raise ServiceNotFound(domain, service) from None
 homeassistant.exceptions.ServiceNotFound: (ServiceNotFound(...), 'Service persistent_notification.create not found')
INFO (MainThread) [homeassistant.core] Timer:starting
</pre>

Погуглил ошибку `Service persistent_notification.create`, но решения не нашёл, такое случалось у других людей с месяц назад, по причине изменения требований к формату некоторых конфигов, но, повторюсь, для меня это оказалось не применимо.

Пошёл разбираться, как проверить конфиг.

Зашёл внутрь запущенного контейнера

<pre>docker exec -it home-assistant bash
</pre>

Там выполнил команду [check_config](https://www.home-assistant.io/docs/tools/check_config/):

<pre>python -m homeassistant --script check_config --config /config
</pre>

Получил такое сообщение:

<pre>Testing configuration at /config
WARNING:homeassistant.components.http:Configuring 
trusted_networks via the http component has been deprecated. 
Use the trusted networks auth provider instead. 
For instructions, see 
https://www.home-assistant.io/docs/authentication/providers/#trusted-networks
</pre>

Открыл настройки авторизации, исправил всё так, как нужно по документации – и всё починилось.

Странно конечно, что деприкейшн варнинг завалил старт для совсем другой части системы. Ну, теперь наверно буду чуть внимательнее читать Release Notes и выправлять конфиги не дожидаясь, кода там гром грянет.

**UPD:** Похоже, внимательно дочитал раздел Breaking Changes и обнаружил там упоминание, что вручную сконфигурированные `trusted_networks` всё сломают ;)