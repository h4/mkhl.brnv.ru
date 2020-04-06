---
id: 786
title: Установка Pillow на Mac0S 10.14 Mojave
date: 2019-07-25T09:24:25+03:00
author: h4
layout: revision
guid: https://mkhl.brnv.ru/785-revision-v1/
permalink: /785-revision-v1/
---
Хех, похоже, скоро тема «как вкорячить Pillow на новую версию MacOS» станет самой популярной в моём бложике.

Итак, что имеем:

  * MacOS 10.14 Mojave
  * Python 3.7 в virtualenv
  * Что-то там давно поставлено через Homebrew, то есть CommandLine от XCode вроде как должны быть
  * Желание развернуть локально что-то, с зависимостью от Pillow (в моём случае – [opencv/cvat](https://github.com/opencv/cvat))

Пытаемся ставиться из зависимостей:

<pre class="wp-block-preformatted">$ pip install -r development.txt </pre>

Но в ответ получаем что-то невразумительное:

<pre class="wp-block-preformatted">> The headers or library files could not be found for zlib,<br />     a required dependency when compiling Pillow from source.<br />> <code>Please see the install instructions at:    https://pillow.readthedocs.io/en/latest/installation.html</code></pre>

В документации к Pillow по ссылке ничего вразумительного не нашлось, но нагуглилась вот такая последовательность действий, которая приводит к успеху:

<pre class="wp-block-preformatted">$ xcode-select --install<br />$ sudo installer -pkg /Library/Developer/CommandLineTools/Packages/macOS_SDK_headers_for_macOS_10.14.pkg -target /</pre>

Я не зря упоминал в самом начале, что Command Line Tools вроде бы ставились после установки операционки, я не уверен на 100%, но похоже, что после каких-то апдейтов системы они потерялись. Это приводило к тому, что запуск инсталлера (вторая команда выше) падала с ошибкой 

<pre class="wp-block-preformatted">> installer: Error - the package path specified was invalid: '/Library/Developer/CommandLineTools/Packages/macOS_SDK_headers_for_macOS_10.14.pkg'.</pre>