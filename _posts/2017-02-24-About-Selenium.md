---
layout: post
title: "O Selenium в общем"
date: 2017-02-24
---

Сюда буду постить какуюто общую инфу про селениум.

Ну начну пожалуй с того что есть [официальный сайт](http://www.seleniumhq.org/) и [сайт на русском](http://selenium2.ru/).

Моё знакомство с Селениум началось с [Selenium IDE](https://addons.mozilla.org/ru/firefox/addon/selenium-ide/),
что по сути есть плагин для FireFox-а. Но с ним иногда приятно просто считерить и записать тест что бы потом перекинуть
его(тест) в среду разработки и потом с ним делать какие-то махинации.

*надо про это потом написать*

Для того что бы запускать тесты на Селениум, я( по совету друзей)
1. Сделал папку TOOLS на системном диске и прописал её в системной PATH(как с JAVА-ой)
2. Добавил в эту папку драйвера(ну или вспомогательные исполняемые файлы) для браузером которые я хочу запускать в тестах.
Взять эти драйвера можно [вот тут](http://www.seleniumhq.org/download/) в разделе *Third Party Browser Drivers*.

Ну а если заморачиватся, то вот ссылки прямые на эти драйвера
[chromedriver] (https://sites.google.com/a/chromium.org/chromedriver/),
[geckodriver(Для FireFox)] (https://github.com/mozilla/geckodriver),
[IEDriverServer (для браузеров IE 7-11)] (http://www.seleniumhq.org/download/),
[MicrosoftWebDriver (для браузера Edge)] (https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/).

Ну помимо обычных браузеров есть еще так называемые Ненастоящие браузеры.
Один из них это [PhantomJS] (https://github.com/detro/ghostdriver) с остальными понка дело не имел.

*Если что будет допишу ;)*

Ну вот мы добалили все драйвера и у нас установлены все браузеры(глупо пытаться запускать что-то что не усьановленно).

Переходим к коду:
Первый мой тест на JAVA выглядел вот так:

```java
import org.junit.After;
import org.junit.Before;
import org.junit.Test;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.WebDriverWait;
import static org.openqa.selenium.support.ui.ExpectedConditions.titleIs;

public class MyFirstTest {
    private WebDriver driver;
    private WebDriverWait wait;

    @Before
    public void start(){
        driver = new ChromeDriver();
        wait = new WebDriverWait( driver, 10);
    }

    @Test
    public void myFirstTest(){
        driver.get("http://www.google.com/");
        driver.findElement(By.name("q")).sendKeys("webdriver");
        driver.findElement(By.name("btnG")).click();
        wait.until(titleIs("webdriver - Поиск в Google"));
    }

    @After
    public void stop(){
        driver.quit();
        driver = null;
    }
}
```
Думаю что надо немного пройтись и обьяснить что к чему(что б и самому не забыть)
1. Импорт подбрасывается автоматически
2. Класс MyFirstTest название
3. private WebDriver driver и private WebDriverWait wait - обьявление двух локальных переменных.
4. @Before - то что должно быть выполнено перед тестом(надстройка) может быть вынесена в другой класс(файл) и быть общая для всех тестов.
Внутри мы создаем новый driver для Chrome можно прописать другое значение и тогда может запуститься другой драйвер
5. @Test - сам по себе тест
    1. driver.get("http://www.google.com/"); - переходим на страницу www.google.com/
    2. driver.findElement(By.name("q")).sendKeys("webdriver"); - находим на странице элемент по имени *q* и внего передаём *webdriver*
    3. driver.findElement(By.name("btnG")).click(); - находим элемент по имени *btnG* и жмём на него
    4. wait.until(titleIs("webdriver - Поиск в Google")); - ждем пока тайтл не сменится на *webdriver - Поиск в Google*
6. @After - То что должно быть выполнено после теста(как и @Before может быть вынесено в отдельный класс) останавливаем и закрываем
драйвер и соответственно и браузер.

Вот первый тест написан и пройден. УРА!

