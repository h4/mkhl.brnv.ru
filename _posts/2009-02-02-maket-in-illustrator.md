---
id: 72
title: Макет сайта в Illustrator. Можно, но осторожно
date: 2009-02-02T04:34:22+03:00
author: h4
layout: post
guid: http://mkhl.brnv.ru/?p=72
permalink: /maket-in-illustrator/
enclosure:
  - |
    http://www.creativebush.com/tutorials/SettingUpAIForWeb.mp4
    2703125
    video/mp4
    
categories:
  - Записи
---
Технологическим стандартом де-факто для создания графических макетов сайтов стал Adobe Photoshop. Такой макет будет принят любым верстальщиком, если выполнить минимальный набор требований, да и все входы-выходы давно описаны. Поэтому я не буду их описывать, а дам несколько рекомендаций по созданию графических макетов в Adobe Illustrator.

[<img class="alignnone size-medium wp-image-84" title="Adobe Illustrator" src="http://mkhl.brnv.ru/wp-content/uploads/2009/02/ai-300x66.png" alt="" width="300" height="66" srcset="https://mkhl.brnv.ru/wp-content/uploads/2009/02/ai-300x66.png 300w, https://mkhl.brnv.ru/wp-content/uploads/2009/02/ai.png 491w" sizes="(max-width: 300px) 100vw, 300px" />](http://mkhl.brnv.ru/wp-content/uploads/2009/02/ai.png)

В своё время я неоднократно вливался в холивары на тему «Приносите нам макеты только в фотошопе» и придерживался непопулярного мнения о том, что макет нужно делать в той программе, которая позволит сделать это максимально быстро и удобно. И верстальщик должен обладать минимальными навыками работы с разными графическими пакетами. Однако я не учёл одного маленького, но важного фактора — дизайнер должен выполнить свою работу качественно и аккуратно. Только в этом случае не возникнет проблем и деформации кармы.  
<!--more-->

  
Есть достаточно большое количество ситуаций, в которых работать с растровым редактором нерентабельно. Если на макете нет и не придвидится необходимости в слоевых масках, а есть только прямоугольники, линии, несколько картинок и текст — создать такой макет в Illustrator будет намного проще и быстрее. А уж если у нас не просто прямоугольники, а прямоугольники с круглыми уголками, то нас просто-таки спасёт _Effect > Stylize > Round Corners…_ (хотя и в Photoshop можно создавать уголки с легко изменяемым радиусом, но об этом в другой раз). Средние и большие пиктограммы тоже удобнее рисовать в векторе.

### Где больной?

[<img class="alignnone size-medium wp-image-76" title="Пикторграмма в векторном виде" src="http://mkhl.brnv.ru/wp-content/uploads/2009/02/01-300x300.png" alt="" width="300" height="300" srcset="https://mkhl.brnv.ru/wp-content/uploads/2009/02/01-300x300.png 300w, https://mkhl.brnv.ru/wp-content/uploads/2009/02/01-120x120.png 120w, https://mkhl.brnv.ru/wp-content/uploads/2009/02/01.png 460w" sizes="(max-width: 300px) 100vw, 300px" />](http://mkhl.brnv.ru/wp-content/uploads/2009/02/01.png)

В теории всё просто замечательно и радужно, но почему что же на практике? На практике мы имеем неизбежное преобразование векторного изображения в растровое. И вот на этом этапе заложена мина. Мина под названием «сглаживание». При работе над макетом в Illustrator нужно соблюдать хирургическую точность. Как только координаты точки перестают быть целыми числами мы теряем чистоту линий. Появляется грязь.

[<img class="alignnone size-medium wp-image-77" title="Пикслельная сетка" src="http://mkhl.brnv.ru/wp-content/uploads/2009/02/02-300x300.png" alt="" width="300" height="300" srcset="https://mkhl.brnv.ru/wp-content/uploads/2009/02/02-300x300.png 300w, https://mkhl.brnv.ru/wp-content/uploads/2009/02/02-120x120.png 120w, https://mkhl.brnv.ru/wp-content/uploads/2009/02/02.png 460w" sizes="(max-width: 300px) 100vw, 300px" />](http://mkhl.brnv.ru/wp-content/uploads/2009/02/02.png)

Проблема номер раз заключается в том, что в режиме отображения, установленном по умолчанию, мы видим картинку в максимальном качестве пригодном для полиграфии, а у монитора оно намного ниже. Для того, что бы видеть, как всё будет выглядеть после растеризации — включаем режим Pixel Preview (_View > Pixel Preview_). Если у вас есть второй монитор, или если есть один, но очень широкий — создаём копию окна (_Window > New Window_) и задаём разные режимы просмтотра для них.

[<img class="alignnone size-medium wp-image-78" title="Пиктограмма в режиме Pixel Prevew" src="http://mkhl.brnv.ru/wp-content/uploads/2009/02/03-300x300.png" alt="" width="300" height="300" srcset="https://mkhl.brnv.ru/wp-content/uploads/2009/02/03-300x300.png 300w, https://mkhl.brnv.ru/wp-content/uploads/2009/02/03-120x120.png 120w, https://mkhl.brnv.ru/wp-content/uploads/2009/02/03.png 460w" sizes="(max-width: 300px) 100vw, 300px" />](http://mkhl.brnv.ru/wp-content/uploads/2009/02/03.png)

Я уже упоминал про хирургическую точность — открываем палитру Transform и проверяем, что бы у нас всегда были целые значения для координат объекта и его размеров. Но это ещё не всё. Предположим, что мы создали прямоугольник размером 15х25 пикселов и расположили его в точку 150:200. Будут ли при этом чистота на границе? В состоянии по умолчанию — нет, потому что у нас нечётные значения ширины и высоты. Поэтому переводим точку привязки координат из центра в левый верхний угол. Вот теперь полный порядок.

[<img class="alignnone size-medium wp-image-79" title="Палитра Transform" src="http://mkhl.brnv.ru/wp-content/uploads/2009/02/transform.png" alt="" width="216" height="106" />](http://mkhl.brnv.ru/wp-content/uploads/2009/02/transform.png)

**upd**: кроме того, необходимо включить привязку к пикселам (_View > Snap to Grid_) и задать особые настройки в _Edit > Preferences_:

  * Категория General: _Keyboard Increment > 0.5px  
_ 
  * Категория Units & Display Performance: _Units > General > Pixels_.

Это позволит точно позиционировать объекты с помощью кнопок клавиатуры, что, несомненно, быстрее и удобнее работы с палитрой Transform.

### Линий нет, даёшь объекты

Следующая проблема — контуры толщиной в один пиксел почти всегда получаются «грязными». Причина кроется в том, что по умолчанию обводка рисуется в обе стороны от контура объекта. Выходов два: в Illustrator CS3 и выше задаём параметру Align Stroke значение «outside», либо вообще не пользуемся обводкой и создаём контуры через _Оbject > Path > Offset Path_. Второй способ лучше, потому что в этом случае мы получаем новый объект, у которого можем легко двигать опорные точки. Но теряем возможность быстро поменять толщину линии.

[<img class="alignnone size-medium wp-image-80" title="Настройка палитры Stroke" src="http://mkhl.brnv.ru/wp-content/uploads/2009/02/stroke.png" alt="" width="231" height="152" />](http://mkhl.brnv.ru/wp-content/uploads/2009/02/stroke.png)

Иногда у Illustrator ломается внутренний калькулятор и в этом случае точно выставленные линии начинают двоить. Лекарство простое и неудобное — увеличиваем масштаб, ставим рядом два окна, одно со стандартным режимом просмотра, второй — Pixel Preview. В первом аккуратно двигаем опорные точки, а по второму контролируем процесс.

Итак, дорогие дизайнеры! Создавая захыватывающие дух макеты, не забывайте о том, что потом ваш макет будут мучать и резать. Что бы макет не изуродавали, подготовьте его ко взрослой жизни — проверьте все детали при большом увеличении в режиме Pixel Preview. При необходимости внесите коррективы.

### Таки всё плохо, что делать?

На написание этой заметки меня сподвиг один из последних полученных мною макетов. Все линии были сбиты, контуры были сделаны как обводка.

[<img class="alignnone size-medium wp-image-81" title="Грязная пиктограмма" src="http://mkhl.brnv.ru/wp-content/uploads/2009/02/sml.png" alt="" width="50" height="50" />](http://mkhl.brnv.ru/wp-content/uploads/2009/02/sml.png)

Для исправления ситуации прежде всего избавляемся от обводок, нам нужны только объекты. Для этого делаем так: Object > Expand. После чего выравниваем всё с точностью до пиксела.

[<img class="alignnone size-medium wp-image-83" title="Пиктограмма исправленная" src="http://mkhl.brnv.ru/wp-content/uploads/2009/02/sml-edited1.png" alt="" width="42" height="42" />](http://mkhl.brnv.ru/wp-content/uploads/2009/02/sml-edited1.png)

### Итого

Делать макеты в Issustrator можно. Но очень важно уметь правильно их готовить. Как в изысканой кухне — прежде всего нужно соблюдать чистоту и точность.

Так же рекомендую к прочтению:

  * [Обращение верстальщика к дизайнеру](http://tachisis.livejournal.com/498035.html) (правильно, но спорно, чёрт возьми);
  * [Создание макета страницы в Illustrator](http://habrahabr.ru/blogs/design/44026/) и [его вёрстка](http://habrahabr.ru/blogs/webdev/44064/);
  * [Растрирование графики в Illustrator](http://turbomilk.ru/blog/cookbook/adobeillustrator/rasterizing_in_adobe_illustrator_10_cs/)
  * [Настройка Illustrator для создания макетов сайтов](http://www.creativebush.com/tutorials/SettingUpAIForWeb.mp4) (скринкаст, eng)