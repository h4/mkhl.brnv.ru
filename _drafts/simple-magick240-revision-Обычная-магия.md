---
id: 241
title: Обычная магия
date: 2011-07-07T19:28:16+03:00
author: h4
layout: revision
guid: http://mkhl.brnv.ru/240-revision/
permalink: /240-revision/
---
<div>
  <p>
    Признавайтесь, часто ли вам приходится сделать примитивную обработку множества фотографий? Поменять размер, обрезать до квадрата, что нибудь ещё&#8230; Если вы для этого используете Photoshop &#8212; вы тратите кучу лишнего времени и мы идём к вам.
  </p>
  
  <p>
    Добро пожаловать к консольной утилите <a href="http://www.imagemagick.org/">ImageMagick</a>. Нет, вру, это набор утилит, каждая из которых выполняет свою собственную работу.
  </p>
  
  <p>
    <strong>Convert</strong> — колбасит файл и сохраняет под новым именем
  </p>
  
  <p>
    <strong>Mogrify</strong> — тоже, что и convert, но сохраняет в том же файле. То есть, convert — это Save As&#8230;, а mogrify — Save, без as.
  </p>
  
  <p>
    <strong>Identify</strong> <strong>—</strong> выводит всю информацию о файле: разрешение, цветовая модель и т.д.
  </p>
  
  <p>
    Предположим, что нам нужно обработать 100500 фоток: уменьшить до 800×600, а потом ещё сделать превью размером 100×100. И конечно фото разной ориентации (портретной и ландшафтной, а не то, что вы подумали).
  </p>
  
  <p>
    Уменьшить фото до нужного размера:
  </p>
  
  <blockquote>
    <p>
      convert -quality 80 -resize 800&#215;600 -strip $name &#171;med/$name&#187;;
    </p>
  </blockquote>
  
  <ul>
    <li>
      quality — степень компрессии
    </li>
    <li>
      strip — выкинуть лишнюю информацию
    </li>
  </ul>
  
  <p>
    Сделать превью для горизонтальных фото:
  </p>
  
  <blockquote>
    <p>
      convert -quality 80 -resize 180&#215;120 -crop 120&#215;120+30+0 -strip $name &#171;sml/$name&#187;;
    </p>
  </blockquote>
  
  <ul>
    <li>
      crop — обрезка ширина×высота×отступ_слева×отступ_сверху
    </li>
  </ul>
  
  <p>
    Сделать превью для вертикальных фото:
  </p>
  
  <p>
    convert -quality 80 -resize 120&#215;180 -crop 120&#215;120+0+30 -strip $name &#171;sml/$name&#187;;
  </p>
  
  <p>
    Узнать ширину картинки:
  </p>
  
  <blockquote>
    <p>
      identify -format %w $name
    </p>
  </blockquote>
  
  <p>
    А теперь соберём всё это в небольшой bash-скрипт:
  </p>
  
  <pre>#!/bin/bash
mkdir med;
mkdir sml;
for name in *.jpg; do
    convert -quality 80 -resize 180x120 -crop 120x120+30+0 -strip $name "med/$name";
    IMG_WIDTH=`identify -format %w $name`;
    IMG_HEIGHT=`identify -format %h $name`;
    if [ $IMG_WIDTH -gt $IMG_HEIGHT ]; then
        convert -quality 80 -resize 180x120 -crop 120x120+30+0 -strip $name "sml/$name";
    else
        convert -quality 80 -resize 120x180 -crop 120x120+0+30 -strip $name "sml/$name";
    fi;
done;</pre>
  
  <p>
    Вот такая вот небольшая магия.
  </p>
</div>