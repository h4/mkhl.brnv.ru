---
id: 643
title: Получение номера недели на JS
date: 2014-10-22T16:26:48+03:00
author: h4
layout: revision
guid: http://mkhl.brnv.ru/249-revision-v1/
permalink: /249-revision-v1/
---
**Внимание:** среди действий, описанных в статье, есть неточности. Правильная функция вычисления номера недели находится в конце статьи.

Учебный процесс в [нашем институте](http://www.avalon.ru) (как и во многих других) завязан на недельные циклы. Поэтому жизненно необходимо иметь возможность определить номер недели по дате. Оказывается, количество методов, предоставляемых объектом _Date_ в _JavaScript_ довольно скуден, и определять номер недели он не умеет. Ну, делать нечего — изобретём свой велосипед. Собственно нам нужно выяснить, сколько дней прошло с начала года (этого от _Date_ мы тоже узнать не можем), дополнить его до целого числа недель и поделить на семь. Определим сегодняшнюю дату:  
var ts = new Date(); Теперь узнаем, а какой же нынче год-то на дворе и, заодно, какой день недели пришёлся на первое января.

    var Y = ts.getFullYear();
    var newYear = new Date(ts.getFullYear(), 0, 1);
    var newYearDay = newYear.getDay(); Гуд, теперь можем узнать число дней, прошедших с нового года. Да, кому-то придётся перевести дикое число миллисекунд в дни. 
    
    var delta = Math.floor((ts.getTime() - newYear.getTime())/1000/60/60/24); И последняя деталь нашего велосипеда — получение числа недель: 
    
    var wNum = Math.floor((delta + newYearDay)/7);
    

## Ставим на конвеер

Теперь объединим всё это в одну функцию, что бы потом использовать столько раз, сколько нужно. В идеале можно расширить _прототип_ объекта _Date_ новым методом, но кошерно ли это?

    var getWeekNum = function(dt) {
        /**
         В коде функции — ошибка, воспользуйтесь вторым вариантом
        */
        var ts,
           newYear,
           newYearDay,
           wNum;
    
        ts = (dt) ? new Date(dt) : new Date();
        newYear = new Date(ts.getFullYear(), 0, 1);
        newYearDay = newYear.getDay();
    
        wNum = Math.floor(((ts.getTime() - newYear.getTime())/1000/60/60/24 + newYearDay)/7);
    
        return wNum;
    }
    

**UPD 11.10.2013:** Сегодня снова воспользовался этой функцией и получил неожиданные результаты. В итоге, выяснил, что код функции ошибочен. Вот новая функция, она правильная:

    function timeToDays(time) {
        return time/1000/60/60/24;
    } 
    
    function getWeekNumber(date) {
        var weekNumber;
        var yearStart;
        var ts;
    
        if (_.isDate(date)) {
            ts = new Date(date);
        } else {
            ts = date ? new Date(date) : new Date();
        }
    
        ts.setHours(0, 0, 0);
        ts.setDate(ts.getDate() + 4 - (ts.getDay()||7));
    
        yearStart = new Date(ts.getFullYear(), 0, 1);
    
        weekNumber = Math.floor((timeToDays(ts - yearStart) + 1) / 7);
    
        return weekNumber;
    }