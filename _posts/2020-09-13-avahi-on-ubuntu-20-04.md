---
id: 799
title: Avahi-daemon на Ubuntu 20.04
date: 2020-10-13T21:38:00+03:00
author: h4
layout: post
permalink: /avahi-on-ubuntu-20-04/
---

Обновил убунту на домашнем сервере до 20.04, основная фукнция сервера, конечно же, файлопомойка. Но нужно чтобы был нормальный доступ с MacOS. За это отвечет связка из Netatalk 3 и avahi-daemon. Оба просто конфигурируются, но тем не менее с ними регулярно случается что-то не то. Вот и в этот раз.

Симптомы такие — сервер не виден в сайдбаре в Finder, но виден в разделе Networks. Только почему-то иконка в виде знака вопроса. Подключение через клик по иконке работает через пень-колоду, но если пойти в _Go_ > _Connect to server_ (`Cmd+K`) и там руками ввести `afp://%SERVER_NAME%`, то всё работает.

При перезапуске `netatalk` в логи прилетали сообщение `"Failed to add service: Local name collision"`, а при перезапуске `avahi-daemon` — `*** WARNING: Detected another IPv4 mDNS stack running on this host. This makes mDNS unreliable and is thus not recommended. ***`.

Не уверен, что всё перечисленное необходимо, но после этих шагов подключение к файлопомойке стабилизировалось:

1. Отключаем сервис `systemd-resolved`:

   ```bash
   sudo systemctl stop systemd-resolved
   sudo systemctl disable systemd-resolved
   ```
2. В конфигурационном файл `cat /etc/avahi/avahi-daemon.conf` явно указываем имя сервера:

	```ini
	[server]
	host-name=fett
	```
3. Перезагружаем сервер
