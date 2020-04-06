---
id: 181
title: Обязательные дополнения к Eclipse
date: 2010-10-30T14:22:52+03:00
author: h4
layout: revision
guid: http://mkhl.brnv.ru/178-revision-3/
permalink: /178-revision-3/
---
Я долгое время выбирал для себя удобную среду разработки. Перепробовал кучу всего, от Notepad++ до Dreamweaver и IntelliJ Idea, но остановился в итоге на Eclipse. Не потому что она самая лучшая &#8212; она и потормозить любит, и поглючить &#8212; а потому что работает везде, и дома под виндой, и под линуксом, и на MacOS.

Но «голая» Eclipse &#8212; вещь совершенно для меня бесполезная, нужно ставить расширения. За последние пару дней я решил обновить Eclipse на всех своих компьютерах до версии 3.6, а это потребовало переустановки расширений. Ну а что бы в следующий раз не вспоминать, что мне нужно &#8212; запишу тут единым списком.

## Подключаем репозитории

Расширения хранятся в репозиториях. В свежую Eclipse они не включены, поэтому добавляем ручками:

Help > Install Software&#8230; нажимаем кнопку Add&#8230; и в поле Location вставляем http://download.eclipse.org/releases/helios &#8212; это основной репозиторий расширений Eclipse.

После добавления репозитория IDE получит список расширений и сгруппирует их по типам. В результате  одно и тоже расширение может оказаться в нескольких местах.

Я сразу ставлю следующие:

  * Collaboration: 
      * Eclipse EGit
      * Eclipse JGit
      * Subversive SVN Team Provider
  * General Purpose Tools 
      * PHP Development Tools
      * Remote System Explorer End-User runtime
      * Remote System Explorer User Action
  * Web, XML, and Java EE Development 
      * Eclipse Web Developer Tools
      * Eclipse XML Editors and Tools
      * Eclipse XSL Developer Tools <span></span>
      * Rich Ajax Platform (RAP) Tooling <span></span>1.3.1.20100916-0013
      * Web Page Editor (Optional) <span></span>2.3.1.v20100906-4609oB5855L6N

Два раза нажимаем Next, подтверждаем согласие с лицензиями и Finish.

Если при установке выскакивает сообщение, что мы пытаемся поставить неподписаное расширение &#8212; придётся согласиться с этим, после установки Eclipse предложить перезапуститься или просто применить изменения. Раньше я экономил полминуты и нажимал Apply Changes, но сейчас соглашаюсь на перезапуск. После перезапуска получаем Eclipse с которой уже можно работать.