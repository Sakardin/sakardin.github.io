---
layout: post
title: "JAVA ставим Gradle, Selenuim и Junit"
date: 2017-02-23
---

Ну и так JAVу мы поставили теперь что с этим делать?
Тут я попытаюсь расказать как поставить среду разработки и потом настроить сборщик GRADLE, репозиторий MAVEN,
а так-же SELENIUM и JUNIT.

И так, понимая что я это уже знаю но все равно...

**IDEA**

Среда разработки, находится она по [адрессу](https://www.jetbrains.com/idea/)

Тут все просто: качаем(версия *Community* бесплатная), ставим, запускаем.

Дальше выбираем новый проект, ну или старый(если есть какой)

Все мы внутри что дальше?

**GRADLE**

File > New > Module > Gradle

![New Project]({{ site.url }}/pict/New_project.jpg)

указываем GroupID и ArtifactID(надо дополнить инфой про что это конкретно)

![GroupID]({{ site.url }}/pict/GroupID.jpg)

указываем настройки GRADLE(я обычно ставлю три галочки вверху, но потом дополню инфой зачем)

Next > Finish(создались директории и файл build.gradle)

Вот в build.gradle мы и будем указывать зависимости которые нам надо. Вот поэтому мы и отправляемся на...

[**MAVEN**](https://search.maven.org/)

это репозиторий откуда будут устанавливаться зависимости и модули.
если IDEA была установлена с нуля есть смысл зайти в:

File >Settings > Build > Build Tools > Maven > Repositories

и посмотреть что добавленно

`https://repo1.maven.org/`

Итак! Все нормально, все добавленно, значит мы идем на сайт [MAVEN](https://search.maven.org/)
и вбиваем в поиск то что нам надо ( например Selenium java)

![Maven1]({{ site.url }}/pict/Maven1.jpg)

выбираем последнюю версию  seleniuma, заходим в Gradle, копируем строчку и вставляем в файл
build.gradle в dependencies.

![Maven2]({{ site.url }}/pict/Maven2.jpg)

Должно получится что-то типа такого

``dependencies {
     testCompile group: 'junit', name: 'junit', version: '4.11'
     compile 'org.seleniumhq.selenium:selenium-java:3.0.1'

 }``

После того как все сделано надо обновить проект Gradle > Refresh

НУ вот так просто настраивается все это дело.







