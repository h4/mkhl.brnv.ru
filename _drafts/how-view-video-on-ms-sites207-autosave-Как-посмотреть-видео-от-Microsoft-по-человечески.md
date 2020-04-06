---
id: 212
title: Как посмотреть видео от Microsoft по-человечески
date: 2011-03-02T01:37:37+03:00
author: h4
layout: revision
guid: http://mkhl.brnv.ru/207-autosave/
permalink: /207-autosave/
---
Все мы знаем Microsoft, знаем что она любит идти своим путём и считает этот путь единственно верным. Возьмём, к примеру, видео. Весь мир публикует видео во флеше. Прогрессивное человечество считает, что флеш — зло и использует тег <video>. Microsoft тоже считает, что флеш зло, но и тег <video> не признаёт, у неё своя игрушка — сильверлайт.

Казалось бы, сильверлайт и сильверлайт, плагины есть для всех браузеров и операционных систем. Вот только не получилось у меня заставить работать этот плагин в Linux.

Что же делать, если посмотреть видео на сайте Майкрософт хочется, а нужного плагина нет? Предположим, что мы хотим посмотреть вот [это видео с сайта](http://www.techdays.ru/videos/3325.html) techdays.ru. Нам предложат установить плагин, но мы не будем этого делать.

[<img class="alignnone size-medium wp-image-209" title="20110216-171017-d0b2d18bd0b4d0b5d0bbd0b5d0bdd0b8d0b5_0011" src="http://mkhl.brnv.ru/wp-content/uploads/2011/02/20110216-171017-d0b2d18bd0b4d0b5d0bbd0b5d0bdd0b8d0b5_0011-300x226.png" alt="" width="300" height="226" srcset="https://mkhl.brnv.ru/wp-content/uploads/2011/02/20110216-171017-d0b2d18bd0b4d0b5d0bbd0b5d0bdd0b8d0b5_0011-300x226.png 300w, https://mkhl.brnv.ru/wp-content/uploads/2011/02/20110216-171017-d0b2d18bd0b4d0b5d0bbd0b5d0bdd0b8d0b5_0011.png 464w" sizes="(max-width: 300px) 100vw, 300px" />](http://mkhl.brnv.ru/wp-content/uploads/2011/02/20110216-171017-d0b2d18bd0b4d0b5d0bbd0b5d0bdd0b8d0b5_0011.png)

Открываем исходный код страницы и находим следующий кусок кода:

<div style="white-space:pre;">
  <div id=&#187;silverlightPlayer&#187;><br /> <object data=&#187;data:application/x-silverlight-2,&#187; type=&#187;application/x-silverlight-2&#8243; style=&#187;height:380px;width:460px&#187;><br /> <param name=&#187;source&#187; value=&#187;http://www.techdays.ru/TechDaysPlayer.xap&#187;><br /> <param name=&#187;initParams&#187;<br /> value=&#187;SourceUri=<strong>http://www.techdays.ru/get.aspx?MID=d20b7e23-ca80-421c-b3b9-2d71d5913816</strong><br /> &IsSilverLight=true,SimilarLecturesUrl=http://www.techdays.ru/HttpHandlers/LecturesHandler.ashx?Num=3325,<br /> ReplayToolTip=Replay, FrameUrl=http://www.techdays.ru/LectureContentImage.aspx?ContentId=d20b7e23-ca80-421c-b3b9-2d71d5913816<br /> &width={0}&height={1}&#187;>
</div>

<div style="white-space:pre;">
  &#8230;
</div>

<div style="white-space:pre;">
  <span style="font-family: 'Courier New', monospace; font-size: 12px; line-height: 18px;"></object></span><span style="font-family: 'Courier New', monospace; font-size: 12px; line-height: 18px;"></div></span>
</div>

  * Копируем значение SourceUrl (то, что выделено полужирным)
  * Запускаем [VLC](http://www.videolan.org/vlc/)
  * Выполняем команду «Media > Open URL»
  * Вставляем скопированный адрес
  * Смотрим видео.

<div>
  UPD: Этот способ не работает в случае с потоковым вещанием на разного род
</div>