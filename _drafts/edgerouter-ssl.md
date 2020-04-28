# Обновление SSL-сертификатов на EdgeRouter (дубовый способ)

Дома за интернет у меня отвечает EdgeRouter X и я прикрутил к нему SSL-сертификаты от Let's Encrypt, но пока что самым корявым способом – получаю сертификаты на серваке, который стоит за роутером, а потому копирую их по ssh не EdgeRouter. Этот подход работает для браузера, но старые версии curl не могут найти корневой сертификат и отказываются с ним работать. Curl мне нужен для того, чтобы своевременно приходили уведомления об истекающем сертификате.

Как сделать так, чтобы всё работало:

```bash
cd /etc/letsencrypt/%domain_name%/live
cat cert.pem privkey.pem > server.pem
```

Дальше нужно скопировать `server.pem` и `chain.pem` на роутер и положить их в каталог `/etc/lighttpd`.

На роутере нужно поправить `/etc/lighttpd/conf-enabled/10-ssl.conf`:

```nginx
$SERVER["socket"] == "%ROUTER_IP%:443" {
	ssl.engine  = "enable"
	ssl.use-sslv3 = "disable"
	ssl.pemfile = "/etc/lighttpd/server.pem"
	ssl.ca-file = "/etc/lighttpd/chain.pem"
	ssl.dh-file = "/etc/lighttpd/dhparam.pem"
	ssl.cipher-list = "EECDH+AESGCM:EDH+AESGCM"
}
```

и перезапустить `lighttpd`:

```bash
sudo kill $(cat /var/run/lighttpd.pid)
sudo /usr/sbin/lighttpd -f /etc/lighttpd/lighttpd.conf
```



А вообще надо бы всё автоматизировать, например с помощью вот этого скрипта: https://github.com/hungnguyenm/edgemax-acme