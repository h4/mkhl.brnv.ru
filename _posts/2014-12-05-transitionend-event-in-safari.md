---
id: 649
title: Событие transitionend в Safari
date: 2014-12-05T02:09:44+03:00
author: h4
layout: post
guid: http://mkhl.brnv.ru/?p=649
permalink: /transitionend-event-in-safari/
categories:
  - Записи
---
Делал простенький lightbox с transition. Кликнули по картинке — в body добавился блок-оверлей и в нём плавно раскрылась большая картинка. Кликнули по оверлею — картинка свернулась и оверлей исчез.

Чтобы удалять оверлей после того, как завершится транзишн использовал подписку на соответствующее событие:

<pre>this._fullImage.one('transitionend', this._close.bind(this));</pre>

Естественно, нужно было проверить, что если transition не поддерживается, то закрывать оверлей немедленно:

<pre>this.transitionSupports = 'transition' in document.body.style;
if (this.transitionSupports) {
    this._fullImage.one('transitionend', this._close.bind(this));
} else {
    this._close();
}</pre>

Однако оказалось, что в Сафари оверлей не удалялся. Всё дело в том, что в этом браузере свойство `document.body.style.transition` есть, а вот событие нужно отлавливать с вендорным префиксом, и стили тоже должны быть с префиксами. То есть как-то так:

<pre>this.transitionSupports = 'transition' in document.body.style;
if (this.transitionSupports) {
    this._fullImage.one('transitionend webkitTransitionEnd', this._close.bind(this));
} else {
    this._close();
}</pre>