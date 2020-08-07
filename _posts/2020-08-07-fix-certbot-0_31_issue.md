---
id: 797
title: Автообновление сертификато с certbot на Ubuntu 16.04
date: 2020-04-24T23:28:00+03:00
author: h4
layout: post
permalink: /fix-certbot-0_31_issue/
---

Есть у меня серверок, на котором крутится пара сайтов. Сайты отдаются по https, а сертификаты обслуживет Certbot. Всё как у всех.

Но, внезапно, автообновление сертификатов перестало рабоать. Полез разбираться, запускаю руками

```bash
# certbot renew
```

А в ответ прилетает что-то такое:

```
Attempting to renew cert (putina-spb.ru) from /etc/letsencrypt/renewal/mysite.com.conf produced an unexpected error: Missing command line flag or config entry for this setting:
Select the webroot for www.mysite.com:
Choices: ['Enter a new webroot', '/home/user/sites/mysite.com/www/htdocs']
```

Немного покопавшись по интернетам, выяснил, что это баг в `certbot 0.31`. Обновить на новую версию как-то не особо получилось, у меня там крутится Ubuntu 16.04, поэтому пошёл править конфиги. 

Открвыем `/etc/letsencrypt/renewal/mysite.com.conf` и дописывем в конец секцию `[[webroot_map]]`:

```ini
[[webroot_map]]
mysite.com = /home/user/sites/mysite.com/www
www.mysite.com = /home/user/sites/mysite.com/www
```

Перезапускаем `certbot renew` — и всё работает. А вообще, конечно, пора бы там операционку уже обновить н