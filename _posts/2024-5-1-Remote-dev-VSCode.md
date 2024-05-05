---
layout: post
title: "Удалённая разработка с VS Code в браузере"
---
Code Server выполняет Visual Studio Code на удалённом сервере, доступном через браузер.

## Зачем мне это нужно?
* Согласованная среда: вы можете писать код на хромбуке, планшете или ноутбуке с согласованной средой разработки, пользуясь "домашними" настройками.
* Мультиплатформенность: все преимущества VS Code будут доступны из любого браузера, включая планшеты.
* Производительность сервера: вы можете пользоваться возможностями крупных облачных серверов для ускорения тестов, компиляции, загрузок и прочего. С помощью DigitalOcean сервера могут быть масштабированы до любого размера.
* Экономия заряда батареи: вы сэкономите энергию заряда, т.к. все вычисления будут производиться на сервере.

## Настройка
Представленный ниже вариант настройки очень эффективный с точки зрения гибкости, производительности и экономии:
1. С мобильного устройства на основе заготовленного образа создайте Droplet (виртуальный сервер).
2. Произведите обновление с GitHub.
3. Установите VS Code в браузере вместе с Code Server.
4. Выполните необходимую работу.
5. Отправьте на GitHub.

## Установка Code Server
1. Для его установки идите на [страницу последних версий](https://github.com/cdr/code-server/releases/latest) и скопируйте ссылку на последний выпуск для Linux. Выполните в консоли следующие команды:
```
# Скачать последнюю версию Github (вставьте скопированную ссылку)
wget https://github.com/cdr/code-server/releases/download/{version}/code-server{version}-linux-x64.tar.gz
# Распаковать tar
tar -xvzf code-server{version}-linux-x64.tar.gz
# Run Code Server
cd code-server{version}-linux-x64
./code-server
```
2. Извлеките публичный IP-адрес созданного виртуального сервера и укажите браузеру: `http://{публичный ip}:8080`
3. Необходимо открыть в редакторе и поправить файл настроек `~/.config/code-server/config.yaml`, копируем оттуда пароль или меняем на свой и прописываем адрес своего сервера:
  bind-addr: 1.12.3.4:8080
  auth: password
  password: bvpiareecleeeck
  cert: false
1. Так как официальный маркетплейс VS Code не может использоваться, у Coder есть свой [собственный](https://github.com/cdr/code-server#extensions), который предоставляет открытые расширения.
2. Все шрифты будут работать нормально при условии, что они установлены на локальный компьютер, т.к. отображает текст именно ваш браузер.