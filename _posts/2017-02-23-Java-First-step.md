---
layout: post
title: "JAVA первые шаги"
date: 2017-02-23
---

Думаю это больше для закрепления и если что-то подзабудется что бы знать где брать.

И так. Что бы поставить JAVA на компьютере надо будет:

* Заходим на сайт [JAVA](http://www.oracle.com/technetwork/java/javase/downloads/index.html), жмём Java JDK
 и качаем ту версию которую надо для вашей системы. Понятно что для Виндовс только вот для 64 или 32(86) решает каждый сам.
* Запускаем установщик и запоминаем директорию куда она поставилось.
* Открываем: Панель основных сведений > Дополнительные параметры > Переменные среды.
* Создаем новую переменную JAVA_HOME и в неё добавляем путь куда поставилась JAVA SDK(JDK)

![JAVA_HOME]({{ site.url }}/pict/JAVA_HOME.jpg)
* Теперь редактируем PATH

`%JAVA_HOME%\bin`

![PATH]({{ site.url }}/pict/PATH.jpg)
* Все сохраняем
* Запускаем консоль

`where java`

`where javac`

Все должно найтись.

![consol]({{ site.url }}/pict/consol.jpg)


Всё просто!!!