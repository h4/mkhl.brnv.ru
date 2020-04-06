---
id: 761
title: 'Делаем git pull &#8212;rebase опцией по умолчанию'
date: 2018-06-15T16:57:28+03:00
author: h4
layout: revision
guid: http://mkhl.brnv.ru/757-revision-v1/
permalink: /757-revision-v1/
---
В конце января я рассказывал на митапе PiterCSS о том, [как использовать интеграцию git с WebStorm](https://www.youtube.com/watch?v=TES0ENoIDbE&t=2s) (и любой другой IDE от JetBrains) на полную катушку.

В том числе, про то, как быстро синхронизироваться с удалённой копией репозитория (_VCS > Update Project&#8230;_ или _⌘ + T_/_Ctrl + T_). При выполнении этой команды появляется вот такое окошко:

<img class="alignnone size-full wp-image-758" src="https://mkhl.brnv.ru/wp-content/uploads/2018/06/2018-06-15_16-06-35.png" alt="2018-06-15_16-06-35" width="471" height="212" srcset="https://mkhl.brnv.ru/wp-content/uploads/2018/06/2018-06-15_16-06-35.png 942w, https://mkhl.brnv.ru/wp-content/uploads/2018/06/2018-06-15_16-06-35-300x135.png 300w, https://mkhl.brnv.ru/wp-content/uploads/2018/06/2018-06-15_16-06-35-768x346.png 768w" sizes="(max-width: 471px) 100vw, 471px" /> 

Для того, чтобы история изменений была линейной — желательно использовать Update Type: Rebase, но делать это каждый раз — откровенно лень. И вот встал вопрос, а как же использовать стратегию обновления `git pull --rebase` по умолчанию? К сожалению, тогда я не смог дать ответа на этот вопрос.

Но вот сегодня копаясь на внутренней вики в нашей компании увидел, что это очень легко делается через терминал:

<pre>git config --global branch.autosetuprebase always</pre>

Эта настройка будет действовать для всех вновь создаваемых репозиториев, для тех, что уже созданы нужно выполнить из консоли вот эту команду, находясь в каталоге с нужным проектом:

<pre>git config branch.master.rebase true</pre>