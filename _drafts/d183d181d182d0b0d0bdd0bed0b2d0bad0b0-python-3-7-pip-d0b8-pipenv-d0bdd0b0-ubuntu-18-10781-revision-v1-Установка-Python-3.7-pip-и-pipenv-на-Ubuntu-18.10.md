---
id: 788
title: Установка Python 3.7, pip и pipenv на Ubuntu 18.10
date: 2019-10-15T22:21:11+03:00
author: h4
layout: revision
guid: https://mkhl.brnv.ru/781-revision-v1/
permalink: /781-revision-v1/
---
Пришла необходимость установить самую распоследнюю версию питона на домашний сервер, там Ubuntu 18.10. На макоси давно уже всё поставлено и проблем, вроде бы не было, а тут пришлось немного повозиться.

Добавляем новый репозиторий в `apt`, потому что Python 3.7 есть только там. Ну и сразу ставим нужную версию питона.

<pre class="wp-block-preformatted">sudo add-apt-repository ppa:ubuntu-toolchain-r/ppa<br />sudo apt install python3.7<br /></pre>

Проверяем, что новая версия установилась, но python3 пока что смотрит на старую

<pre class="wp-block-preformatted">ls -l /usr/bin/python3*</pre>

Если хочется, чтобы python3 запускался с 3.7 – заменяем симлинк. Ну или можно попробовать поиграть с `apt --update-alternatives`

<pre class="wp-block-preformatted">cd /usr/bin<br />rm /usr/bin/python3<br />ln -s python3.7 python3</pre>

Обновляем pip, если его ещё нет – ставим командой `sudo apt install python3.7-pip`

<pre class="wp-block-preformatted">python3.7 -m pip install pip</pre>

Теперь ставим `pipenv`

<pre class="wp-block-preformatted">pip3 install --user pipenv</pre>

Проверяем, что всё работает

<pre class="wp-block-preformatted">mkdir test && cd  test<br />pipenv shell<br />python --version<br />&gt; Python 3.7.3</pre>