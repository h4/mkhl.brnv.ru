---
id: 766
title: Восстанавливаем работу USB-UART CH340G после апгрейда до Mojave
date: 2018-11-03T00:31:45+03:00
author: h4
layout: post
guid: https://mkhl.brnv.ru/?p=766
permalink: /repair-ch340g-on-mojave/
categories:
  - Записи
---
Так вышло, что я немного увлёкся разного рода микроконтроллерами и для прошивки пока использую простейший _[USB-UART](https://ru.wikipedia.org/wiki/%D0%A3%D0%BD%D0%B8%D0%B2%D0%B5%D1%80%D1%81%D0%B0%D0%BB%D1%8C%D0%BD%D1%8B%D0%B9_%D0%B0%D1%81%D0%B8%D0%BD%D1%85%D1%80%D0%BE%D0%BD%D0%BD%D1%8B%D0%B9_%D0%BF%D1%80%D0%B8%D1%91%D0%BC%D0%BE%D0%BF%D0%B5%D1%80%D0%B5%D0%B4%D0%B0%D1%82%D1%87%D0%B8%D0%BA)_ на базе микросхемы _[CH340G](https://roboshop.spb.ru/CH340-converter)_. Сегодня принёс домой RFID/NFC контроллер _[PN532](https://roboshop.spb.ru/PN532-mini-module)_ и наверно с час  пытался завести его через `libnfc`. Но`nfc-poll` упорно возвращал _“No NFC device found”_.

Уже сложил всё обратно в коробку и собрался идти спать, как вдруг пришло в голову проверить, а не отломали ли чего при обновлении до _MacOS Mojave_? И точно, снова что-то там не срослось с драйверами, если верить беглому поиску по интернету.

Решение простое – отрываем консоль и там вводим

<pre>sudo rm -rf /Library/Extensions/usbserial.kext
sudo reboot
</pre>

После перезагрузки `nfc-poll` успешно нашёл NFC-ридер и пришлось исследовать всё, что хоть как-то походило на NFC-карту ;)