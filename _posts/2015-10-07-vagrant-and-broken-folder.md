---
id: 691
title: Вагрант и каталог, который не хотел удаляться
date: 2015-10-07T10:37:16+03:00
author: h4
layout: post
guid: http://mkhl.brnv.ru/?p=691
permalink: /vagrant-and-broken-folder/
categories:
  - Записи
---
В одном из фриланс-проектов используется [Vagrant](https://www.vagrantup.com/), а я недавно поставил свежий El Capitan.

Клонирую я, значится, проект и делаю в нём `$ vagrant up —provision`. Что-то там крутится, пыхтит, выплёвывает в консоль кучу всякой информации, а потом — умирает. Ну, думаю, ладно. Обновлю-ка, для начала, всё. Сношу виртуальную машину, качаю последние стабильные VirtualBox и Vagrant, устанавливаю, запускаю…

А там сайт-то простой, на php. И всё ставится через `composer install`. И вот что-то этот Бетховен (см. на лого композера) снова падает с ошибкой, что он не может удалить какой-то там каталог в процессе установки. Ну, думаю, ладно. Нахожу этот каталог на хост-машине — он прекрасно удаляется. Но композер всё равно сходит с ума и не работает.

В общем, где-то час я занимался удалением каталогов на хост-машине и изнутри виртуалки, чистил `~/.composer`, убивал и пересоздавал виртуалку — всё без толку. Если зайти через `$ vagrant ssh` на виртуалку и попробовать удалить каталоги там, то падает с ошибкой &#171;cannot remove \`/home/vagrant/project/vendor/packageName’: Is a directory&#187;. А если сделать &#171;ls&#187;, то получаем следующую картину:

    vagrant@vm:~$ ls -l project/vendor
    ls: cannot access project/vendor/packageName: No such file or directory
    total 0
    ?????????? ? ? ? ?            ? packageName
    

В этот момент мне в голову полезли мысли о том, что жесткий диск решил посыпаться, но я ещё немного погуглил, но ничего путного не нашёл. Каталоги существовали на хост машине, но были битыми в виртуалке.

И тут, во время очередного перезапуска виртуалки, я увидел ворнинг в консоли:

    => default: Checking for guest additions in VM…
        default: The guest additions on this VM do not match the installed version of
        default: VirtualBox! In most cases this is fine, but in rare cases it can
        default: prevent things such as shared folders from working properly. If you see
        default: shared folder errors, please make sure the guest additions within the
        default: virtual machine match the version of VirtualBox you have installed on
        default: your host and reload your VM.
        default:
        default: Guest Additions Version: 4.1.12
        default: VirtualBox Version: 4.3
    

А дай-ка, думаю, обновлю эти самые Guest Additions, ибо отстают они аж на два минорных релиза. Но тут надо заметить, что эта штуку нельзя поставить из виртуалбокса для для headless-вируалки. Поэтому воспользовался вот [этим гистом](https://gist.github.com/fernandoaleman/5083680), модифицировав его под себя.

    $ vagrant ssh
    vagrantup:~$ cd /opt
    vagrantup:~$ sudo wget -c http://download.virtualbox.org/virtualbox/4.3.30/VBoxGuestAdditions_4.3.30.iso \
                           -O VBoxGuestAdditions_4.3.30.iso
    vagrantup:~$ sudo mount VBoxGuestAdditions_4.3.30.iso -o loop /mnt
    vagrantup:~$ cd /mnt
    vagrantup:~$ sudo sh VBoxLinuxAdditions.run —nox11
    vagrantup:~$ cd /opt
    vagrantup:~$ sudo rm *.iso
    vagrantup:~$ sudo /etc/init.d/vboxadd setup
    vagrantup:~$ sudo apt-get install chkconfig #не уверен, что это нужно
    vagrantup:~$ sudo chkconfig —add vboxadd
    vagrantup:~$ sudo chkconfig vboxadd on
    vagrantup:~$ exit
    

Тушу виртуалку, поднимаю, делаю `composer install` — всё работает. По хорошему, теперь бы надо ещё сделать кастомный package для этого всего, но как-то лень.