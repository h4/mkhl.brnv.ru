---
id: 204
title: «Класситус» и оптимизация
date: 2010-12-21T13:13:33+03:00
author: h4
layout: post
guid: http://mkhl.brnv.ru/?p=204
permalink: /klassitus-vs-optymise/
categories:
  - Записи
---
<div>
  <p>
    На прошедшей 16 декабря встрече-конференции «<a href="http://webstandardsdays.ru/">Web Standards Days</a>» Вадим Пацев рассказывал про общую идеологию вёрстки проектов в Яндексе. Идеология скрывается под дурацкой аббревиатурой БЭМ и обладает <a href="http://clubs.ya.ru/bem/">собственным клубом</a> на Я.ру.
  </p>
  
  <p>
    Один из ключевых моментов — отказ от селекторов элемента в пользу селектора классов, поскольку это существенно (когда счёт идёт на миллисекунды) ускоряет рендеринг страницы. То есть вместо <code>p {}</code> рекомендуется использовать <code>.base {}</code>, к примеру. Да, именно так, добавлять классы ко всем элементам, которые нужно стилизовать. Кроме того, это позволяет избежать переопределений и конфликтов наследования.
  </p>
  
  <p>
    Разумный аргумент против — «ведь у нас много параграфов, добавление классов увеличит объём страницы!». Но намного ли? На главной странице kremlin.ru — 23 тега p. Добавив к каждому из них class=base мы увеличим объём страницы на 230 байт. При общем объёме страницы в 56 кб это просто ничтожно малая величина. Так что на этих спичках точно не стоит экономить, лучше удалить переносы строк и пробелы или оптимизировать картинки.
  </p>
  
  <p>
    Остаётся только один-единственный аргумент против указания классов всему подряд: «Мне лень везде писать эти дурацкие классы». Но и тут можно найти решение, взяв на вооружение регекспы или <a href="http://code.google.com/p/zen-coding/">zen coding</a>.
  </p>
  
  <p>
    <em>Примечание</em>: я специально не ставил кавычки вокруг имении класса для ровного счёта, в реальной жизни так делать нельзя.</div>