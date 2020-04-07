---
id: 795
title: Установка базового софта на Ubuntu 18.04
date: 2020-04-07T23:28:00+03:00
author: h4
layout: post
permalink: /install-common-soft-on-ubutu-1804/
---

Шпаргалка со списком команд для установки софта, который чаще всего требуется накатить на свежую Ubuntu. 
Проверялось для 18.04 LTS

## Установка pipenv на Ubuntu 18.04

```bash
sudo apt update
sudo apt install python3.7
# It will install pipenv into /root. If you don't want it – omit sudo
sudo pip3 install --user pipenv
# cd to project dir and execute. 
~/.local/bin/pipenv install --deploy --ignore-pipfile --sequential
```

## Установка NodeJS на Ubuntu 18.04

```bash
sudo apt update
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
sudo apt install -y nodejs
```
