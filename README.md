


Технология 'Java Bean' применяется для организации обмена данными между компонентами в GUI-приложении.
======================================================================================================
GUI-приложение - в первую очередь это приложение которое работает в среде Операционной Системы.
                 Такое приложение имеет клиентскую часть: 'фрейм' на локальной Оерационной Системе, который содержит виджеты (кнопки, радиокнопки, ...). С помощью его пользователь может отправлять/общаться с программой...
                 И обработчик: это и есть сама программа-обработчик, которая выполняет какие-то операции/действия...
Связь между 'клиентской программой' и 'программой-обработчика' выполняется через Операционную Систему. В очередь сообщений Операционной Системы ложиться запрос запрос от клиентского фрейма (виджета).
А дальше Операционная Система достает из очереди эти сообщения и рассылает их программе-обработчику...

Технология 'Enterprice Java Bean' применяется для организации обмена данными между компонентами в WEB-приложении.
=================================================================================================================
WEB-приложение - в первую очередь это приложение которое работает в среде на Сервере Приложений.
                 Такое приложение имеет клиентскую часть: веб-страницу на удаленном компьютере, которая содержит виджеты (кнопки, радиокнопки, ...). С помощью его пользователь может отправлять/общаться с программой...
                 И серверную часть: это и есть сама программа-обработчик, которая выполняет какие-то операции/действия...
Связь между 'клиентской программой' и 'программой-обработчика' выполняется через HTTP-протокол, с помощью сессии (и еще куки).
Внутри сессии храняться классы-объекты, это такая форма данных которыми обменивается веб-приложение.
В рамках технологии 'Enterprice Java Bean', такие классы-объекты называются 'бинами'. То есть, если иметь доступ к сессии, тогда из сессии можно достать такой объект и получить полный доступ информации...
(Для создания )

'Vaadin'
==============================================================================================
Vaadin-приложение представляет собой фреймворк, который компилирует из кода-Java в код-JavaScript клиентскую часть веб-приложения.
Основным Java-классом является тип 'Application', в котором содержутся виджеты... Работа с этим классом-Application похожа на стиль-SWING.
На каждый виджет вешается слушатель (Event) внутри которого реализована функция-обработчика.
И именно сюда, в эту функцию-обработчика, передается наш бин.
Поэтому связь/обмен данными для виджетов в Vaadin-приложении выполняется с помощью объектов...
В свою же очередь Vaadin-приложение компилирует JavaScript/AJAX, с помощью которого и организуется связь между компонентами...

'GWT'
==============================================================================================
GWT-приложение похоже на Vaadin-приложение и делает примерно тоже самое...
GWT-приложение использует SOAP-протокол для связи/обмена данными между компонентами.
Значит, существуют два порта GWT-приложения:
1. внутренний порт - используется только для компонентов (внутренними сервисами GWT...)
2. внешний порт - это рабочий порт, который используется для всех пользователей, доступ к веб-приложению
Основным Java-классом является тип 'EntryPoint', в котором содержутся виджеты... Работа с этим классом-Application похожа на стиль-SWING.
Но здесь, GWT-приложение не имеет сессий из которых можно было-бы доставать объекты, используется (веб) SOAP-сервис, которая позволяет описывать классы-объекты/обмена данными. И именно поэтому GWT-приложение имеет два порта...
Такой (веб) SOAP-сервис, используется только для внутреннего доступа к данным (компонентов веб-приложения...)

'REST'
==============================================================================================
Это веб-сервис который используется для обмена данными в текстовой форме.
Такой (веб) REST-сервис, в отличие от SOAP-сервиса, используется только для внешнего доступа к данным (для пользователй...).
Он удобен тем, что пользователю ненужно знать тип/структуру объекта чтобы запросить данные по форме - достаточно знать только URL-путь...





(Java. HTTP протокол и работа с WEB) http://www.javaportal.ru/java/articles/java_http_web/article02.html
========================================================================================================
HTTP (Hyper Text Transfert Protocol) - это (обычный) текстовый документ который может содержать любые данные/символы... (Обычный) текст становится гипер-текстом именно уже внутри веб-браузера.
Передавать по Hyper Text Transfert Protocol можно любые данные: текст, (бинарные) картинки, спец-символы и прочее...
* механизм работы HTTP-протокола основан на прицыпе - "Запрос-Ответ"

TCP
---
Каждая (рабочая) программа имеет собственный адресс по которому можно получить доступ к этой программе. Локально (внутри компьютера) доступ к программе из-другой-программы можно получить по номеру (адрессу) порта который эта программа занимает.

IP
--
Глобально, доступ к компьютеру, на котором работает локальная программа, можно получить по сетевому адрессу компютера (зарегистрированного в этой сети).
Существует много разных разновидностей сетей (локальные сети, корпоративные сети, глобальные сети сети малого/среднего маштаба, ...). Чтобы установить вид/тип сети внутри которой сейчас работают - это выполняется с помощью маски подсети. (это нужно чтобы ограничить доступ и пересечение компьютерных адрессов в разных подсетях)

Socket (гнездо) - это такой себе виртуальный терминал который позволяет подсоединиться к рабочей программе из-другой-программы по номеру (адрессу) порта который эта программа занимает.

Из нутри, сервер приложений состоит из сокета + (базового) сервлета.
* Этот сокет имеет настроенный ранее оговоренный и зарезервированный номер порта.
* (Базовый) сервлет работает в (дежурном) режиме ожидания. Основная задача базового сервлета находить другие сервлеты согласно клиентским запросам и предоставлять к ним доступ или-же предоставлять доступ к статическим веб-страницам. (для того чтобы находить другие сервлеты для этого существуют карты веб-приложений 'web.xml' которые описывают правила доступа к веб-приложению...)

(Как создать Servlet? Полное руководство) http://devcolibri.com/4284
====================================================================
Сервлет - это тоже есть веб-приложение - класс-наследник HttpServlet, имеет екшин-методы (doGet,doPost,...) и болшую часть своего рабочего времени он находиться в дежурном режиме...
Сервлет работает внутри контейнера-сервлетов и имеет дескриптор разворачивания (на контейнере-сервлетов) - 'web.xml'.
Пользователь/клиент может взаимодействовать с сервлетом через HTTP-протокол.
После получения и обработки клиентского запроса сервлет возвращает (динамически сформированный) html-документ. (или же в карте приложения 'web.xml' указываем статическую веб-страницу)
Все запросы и ответы обвернуты для сервлета в объекты (типа) 'HttpServletRequest'/'HttpServletResponse'.



|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||
(Java. HTTP протокол и работа с WEB ** Работа с TCP/IP в Java. Сокеты) http://www.javaportal.ru/java/articles/java_http_web/article02.html >> http://www.javable.com/columns/serv_side/workshop/18/ch1/
                 (Java. HTTP протокол и работа с WEB ** Протокол HTTP) http://www.javaportal.ru/java/articles/java_http_web/article03.html
                      (Java. HTTP протокол и работа с WEB ** Сервлеты) http://www.javaportal.ru/java/articles/java_http_web/article05.html
                                 (Распределение протоколов по уровням) https://ru.wikipedia.org/wiki/TCP/IP >> http://www.dokwork.ru/2012/02/http-java-tcp.html
                         (Распределение протоколов по уровням ** HTTP) https://ru.wikipedia.org/wiki/HTTP
                          (Распределение протоколов по уровням ** TCP) https://ru.wikipedia.org/wiki/TCP
                           (Распределение протоколов по уровням ** IP) https://ru.wikipedia.org/wiki/IP >> https://ru.wikipedia.org/wiki/Маршрутизация
                                  (http header отправка запросов java) https://github.com/Home-SignUp/Jenkins-SignUp/tree/hotfix-3.1.1.4/gui
                                                                       http://www.dokwork.ru/2012/02/http-java-http.html
                                                                       http://juravskiy.ru/?p=585
                                                                       http://scriptsite.ru/article/show/5/
                                                                       http://habrahabr.ru/post/215117/
                                                                       http://www.xiper.net/learn/also-need-to-know/how-does-a-browser-HTTP-request.html
(DevColibri ** Как создать Servlet? Полное руководство) http://devcolibri.com/4284
                          (javatalks ** Сервлет VS JSP) http://javatalks.ru/topics/5524
                                                        http://javatalks.ru/topics/21133

HTTP (Hyper Text Transfert Protocol) был изначально создан для пересылки HTML-документов, преимущественно текстовых. HTTP в своей работе использует возможности TCP/IP.
Любой HTTP запрос, как и любой ответ по этому протоколу состоит из двух блоков: "заголовок" и собственно "данные" (заголовок отделён от данных двойным символом переноса строки в Java это будет "\n\n", хотя допускается и "\r\n\r\n" для платформы Windows).
Так как HTTP был изначально ориентирован на пересылку прежде всего текстовой информации, то HTTP заголовок является полностью текстовым.
:::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::
JSP должна отвечать за "Вид" (то что видит пользователь И чтоб дизайнеру было легче ориентироваться), а сервлет должен отвечать за "Контроллер" (то что делается внутри).
Сервлет взаимодействует с клиентами посредством принципа: "Запрос-Ответ" (они обычно используются для расширения веб-серверов).
Метод "GET" ....... используется для запроса содержимого указанного ресурса...
Условный GET ...... позволяет обновлять кэшированные объекты без пересылки данных, уже сохраненных клиентом...
Частичный GET ..... Позволяет собирать объект из частей без передачи данных уже имеющихся на стороне клиента и потому запрашивает передачу только части объекта.
Метод "HEAD" ...... по действию практически идентичен методу GET с одним отличием - в ответе на метод HEAD сервер выдаёт только HTTP заголовок, не выдавая содержимого документа.
Метод "POST" ...... предназначен для передачи данных на сервер, отправка файла. (Сообщение ответа сервера на выполнение метода POST не кэшируется)
Метод "PUT" ....... по действию идентичен методу POST, но как и HEAD выдаёт только заголовок HTTP.
Метод "OPTIONS" ... выдаёт все действия, которые можно совершить с документом.
Метод "DELETE" .... указывает серверу, чтобы он предпринял попытку к удалению документа. Возможным ответом является ошибка политики безопасности ("403 Forbidden").
Метод "TRACE" ..... можно получить путь запроса до сервера, список узловых точек, гейтов (Gate), путь через прокси-сервера.
Метод "CONNECT" ... возвращает есть ли связь с сервером и поддерживает ли сервер HTTP протокол. 

---| Для HTTP существует разновидность стандарта URI, называемая URL (Uniform Resource Location - формат записи нахождения ресурса), к примеру: |---
   http://devresource.org:80/javalinks/catalog.php3?name=java&cat=2#section1
1) [http://] ..................................... указывает на протокол доступа к документу
2) [devresource.org:80/javalinks/catalog.php3]
   [devresource.org] ............................. IP адрес
   [:80] ......................................... порт сервера
   [/javalinks/catalog.php3] ..................... путь до документа от корня сервера
3) [?name=java&cat=2] ............................ это часть "GET"-запроса, отделена от документа символом "?"
4) [#section1] ................................... URI-"секция" (Uniform Resource Identifier = формат записи индитефикатора ресурса) отделённая символом "#" (при HTML форматировании в документа можно положить закладку)

---| Параметры HTTP запроса |---
GET / HTTP/1.1
Content-Type: application/json;
Host: localhost
Accept: image/gif, image/x-xbitmap, image/jpeg, image/pjpeg, */*
Accept-Language: ru, en
Accept-Charset: windows-1251, KOI8-R
Accept-Encoding: compressed, gzip
User-Agent: Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0; MyIE2; .NET CLR 1.0.3705)
Referer: http://localhost/?test=test
Cookie: param1=value1; param2=value2
Range-Unit: 2015 | 1024
Pragma: no-cache
Cache-Control: no-cache, must-revalidate
Pragma: must-revalidate, max-age=1000
Proxy-Connection: Keep-Alive
Proxy-Connection: close

---| Параметры HTTP ответа |---
HTTP/1.1 200 OK
Set-Cookie: name=value; expires=date; path=PATH; domain=HOSTNAME; secure
Location: http://www.devresource.org
Date: Mon, 07 Apr 2003 14:51:19 GMT
Last-Modified: Mon, 07 Apr 2003 14:51:00 GMT
Server: Apache/1.3.20 (Win32) PHP/4.3.0
Keep-Alive: timeout=15, max=100
Connection: Keep-Alive
Accept-Ranges: bytes
Content-Length: 673
Content-Type: application/zip
Content-Disposition: attachment; filename=test.zip
Accept-Charset: windows-1251
Accept-Encoding: compress, gzip
Accept-Language: ru
Transfer-Encoding: chunked

This a test!!!

---| Коды ответов сервера |---
Коды с номером типа 1xx: информационный - запрос послан, идёт процесс
Коды с номером типа 2xx: удачное завершение - запрос полностью послан, прочитан/понят сервером и принят им
Коды с номером типа 3xx: перенаправление - действие нуждается в уточнении либо просто информационный ответ
Коды с номером типа 4xx: ошибка клиента - запрос клиента имеет либо неправильный синтаксис, либо не понят
Коды с номером типа 5xx: ошибка сервера - сервер не может обработать запрос клиента

WEB-сервер ........ программа, которая держит сокет сервера, принимает и передаёт данные.
Сервлеты .......... это модули обработки HTTP и FTP запросов.
Базовый сервлет ... является "мозгом" WEB-сервера и работает в связке с WEB-сервером (именно ему отправляет сервер данные и от него же получает ответ, отправляемый клиенту).
                    Основная функция этого сервлета - прочитать запрос клиента, расшифровать его и, в соответствиии с расшифровкой, передать работу сервлету, отвечающему за этот тип запрашиваемой информации.
|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||


+ + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + +
  http://milayanyaka.blogspot.com/p/blog-page_18.html
http://habrahabr.ru/post/113121/
http://www.quizful.net/post/gwt-tutorial-introduction
http://habrahabr.ru/post/192262/   (http://sysmagazine.com/posts/192262/)   http://www.pvsm.ru/java/42351/print/
http://plugin.gwt-platform.googlecode.com/hg/update/
http://habrahabr.ru/post/154321/
http://habrahabr.ru/post/87728/
http://habrahabr.ru/post/141398/
http://samples.gwtproject.org/samples/Showcase/Showcase.html#!CwDatePicker
  http://habrahabr.ru/post/246285/
  http://snsankar.blogspot.com/
https://github.com/JobTest/vitrinaPredmainTask/tree/miratex-master/Task/src/test/java/com/miratex
https://github.com/Home-Java8/Java7/blob/master/README-3.md
https://github.com/Home-Java8/Java7/blob/master/src/main/java/com/HashMapStructure.java
  https://github.com/TimReset/example.gwt.gxt.test
http://habrahabr.ru/company/haulmont/blog/248545/
http://habrahabr.ru/hub/gwt/

https://sites.google.com/site/progerbingbang/google-web-toolkit/unittestinggwtapplicationswithjunit
http://archive.is/dxV40
http://www.quizful.net/test/gwt-google-web-toolkit
https://netbeans.org/kb/74/web/quickstart-webapps-gwt_ru.html

http://dou.ua/lenta/articles/gwt-and-build-systems/
  http://j4sq.blogspot.com/2012/01/java-spring-hibernate.html
http://catine.ru/kuchniy/translation/gwt-dlya-nachinayushhix-podgotovka-k-rabote/
http://ru.tmsoftstudio.com/file/page/Eclipse4/e4_ch10_primer-sozdanie-gwt-prilozheniya-content-delivery-node-dlya-platformy-google-app-engine.html
  (GWT-PF "GWT Pleso Framework" приложения без использования баз данных и RPC) http://gwt.org.ua/ru/tutorials/tutorial1-part1/
                                                                               http://gwt.org.ua/ru/tutorials/tutorial1-part2/
  http://gwt-rus.blogspot.com/
  (Разрабатываем приложение на Spring и GWT) http://alextretyakov.blogspot.com/2011/10/4.html
http://www.tutorialspoint.com/gwt/gwt_create_application.htm
http://www.programcreek.com/2011/01/a-example-application-of-gwt/
http://ru.stackoverflow.com/questions/52540/Сайты-с-туториалами-по-gwt-smartgwt
+ + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + +
https://github.com/Home-GWT/MySampleApplication2
https://github.com/Home-GWT/sample
https://github.com/JobTest/SOAPExample
https://github.com/JobTest/SOAPExample/tree/master/src/main/resources/wsdl
https://github.com/JobTest/SOAPExample/blob/master/src/main/java/dev/bay/ws/publisher/Publisher.java
https://github.com/JobTest/vitrinaPredmainTask/tree/miratex-master/Task

* 'sample' - сперва нужно мавеном собрать (clean + package), а потом запустить через плагин gwt (118n + run)
(Блог Милой Няки ** Стандартное GWT-приложение. Добавление кнопки) http://milayanyaka.blogspot.com/p/blog-page_18.html
                 (Блог Милой Няки ** GWT-приложение игра "Memory") http://milayanyaka.blogspot.com/p/gwt-memory.html
				                                                   http://edcamemora3.appspot.com/

              (веб страница headers)
                (Кэширование в HTTP) http://webo.in/articles/all/http-caching/
                      (HTTP-headers) http://kek.ksu.ru/eos/tests/LHeaders.html
		                             http://kek.ksu.ru/eos/tests/LMeta.html
		                             http://kek.ksu.ru/eos/tests/uchebnik.html
(http header отправка запросов java) https://github.com/Home-SignUp/Jenkins-SignUp/tree/hotfix-3.1.1.4/gui
					   
(Home-SOAP/SOAPExample) https://github.com/Home-SOAP/SOAPExample/blob/master/src/main/java/dev/bay/ws/publisher/Publisher.java
+ + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + + +


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
(SOAP UI и тестирование сервисов) http://www.dataart.ua/blog/2014/04/soap-ui-i-testirovanie-servisov/
                (Что такое SOAP?) http://ru.stackoverflow.com/questions/257184/Что-такое-soap

(SOAP-сервер на Java при участии Apache CXF и Spring ** YetAnotherService.zip) http://habrahabr.ru/post/137543/
                       (Тестирование веб сервисов или как пользоваться SoapUI) http://www.proghouse.ru/programming/20-soapui
					                             (SoapUI for IDE (deprecated)) http://www.soapui.org/soapui-for-ide/soapui-for-ide.html

												        (SoapUI) http://www.soapui.org/
(Home / soapui-intellij-plugin ** Download SoapUI-x64-5.2.1.exe) http://sourceforge.net/projects/soapui/files/soapui-intellij-plugin/
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++


(Учебник Google Web Toolkit) https://drive.google.com/file/d/0B418nT5Bo9w_engtSTdpVDllY2s/view?pli=1 << http://cofe-tv.blogspot.com/2010/11/google-web-toolkit.html
(веб-разработка на GWT и mvp4g) http://www.addconf.ru/presentations/ADD-2/presentations/AntonKotenko.pdf
(gwt-mvp4g-layouting-demo) https://github.com/shamansir/gwt-mvp4g-layouting-demo
                           https://github.com/shamansir/gwt-mvp4g-layouting/
(Mvp4g Showcase (v1.5.0)) http://mvp4gexsc.appspot.com/
                          https://code.google.com/p/mvp4g/source/browse/trunk/examples/?r=131
                          https://code.google.com/archive/p/mvp4g/downloads
                          http://mvp4g.googlecode.com/svn/maven2/releases/com/googlecode/mvp4g/mvp4g/1.5.0/
http://shamansir.github.io/gwt-mvp4g-layouting-demo/index-ru.html
(Deferred-вызовы серверного API в GWT (без RPC)) http://shamansir-ru.tumblr.com/post/1728720550/deferred-вызовы-серверного-api-в-gwt-без-rpc



Добавление GWT в существующею WEB страницу
==========================================
Хост-страница может содержать пустые элементы <body>
Один из фактов, что вы должны знать, хост страница приложения не обязана быть только HTML файлом, созданной с нуля.
Гибкая архитектура GWT дает возможность для интеграции GWT с существующими веб-страницами, в том числе использование технологий сервера как PHP, PERL, JAVA и т.д.
Вы хотите добавить на стороне клиента поведение в одной из ваших страниц, используя GWT. Просто добавьте <script> тег, указывающий на GWT приложение, внутри вашего PHP страницы - тега <head> (Добавив одну строчку в эту PHP, страницу вы сделали поддержу GWT):
    <script language='javascript' src='com.google.gwt.sample.stockwatcher.StockWatcher.nocache.js'></script>
Вы можете добавить виджеты GWT стороны клиента к страницам так же, как вы может со статическими хост страницами.
Это означает, что GWT может легко работать с любой технологией стороны сервера, которую вы используете, пусто будет хоть PHP, Рубин, или даже ASP.NET.

Поддержка языка (JAVA)
======================
GWT поддерживает семантику языка JAVA версии 1.5. Вы можете использовать любы собственные типы данных, классы (и прочее) в вашем приложении. 
Однако JAVASCRIPT не поддерживает 64-битные целые числа и числа с плавающей точкой, одинарной точности, так-что следует избегать использование переменных long или ключевого слова strictfp в исходном тексте JAVA.
JAVASCRIPT (и его расширения, GWT) не поддерживает многопоточность, так-что не используйте слово synchronized, и не делайте вызовов методов Object.wait(), Object.notify() и Object.notifyAll().
Так же, GWT не поддерживает механизмы рефлексии, хотя есть возможность узнать имя класса, для указанного объекта, через метод GWT.getTypeName(Object).
JAVASCRIPT также имеет встроенный сборщик мусора (GC), но JAVASCRIPT не поддерживает финализаторов, так что Java финализаторы определенные в программе не будут выполнены в web режиме.

Поддержка библиотеки времени исполнения
=======================================
JAVA 2 SE и JAVA EE библиотеки поставляют большое кол-во классов, но не вся их функциональность возможна в браузере.
GWT поддерживает часть JAVA платформы, которая определена в пакетах: java.lang и java.util.
GWT частично эмулирует регулярные выражения JAVA, синтаксис регулярных выражений используемых в GWT не идентичен JAVA регулярных выражений. GWT использует возможности регулярных выражений JAVASCRIPT.

Обеспечение GWT совместимости
=============================
При написании приложения используйте языковые возможности (фичи языка) и классы которые поддерживает GWT.
Что бы найти несовместимость (классов/языка) в процессе разработки вашего приложения, отлаживайте его при помощи Хост — режима, если будет задействована не поддерживаемая JAVA функциональность, то вы увидите в окне отладки соответствующие сообщения.

Создание пользовательского интерфейса
=====================================
GWT пользовательский интерфейс состоит из виджетев и панелей.
Виджеты предоставляют общие пользовательские инструменты как кнопки, текстовые поля и деревья.
Панели как DocPanel, HorizontalPanel, и RootPanel, содержат виджеты и определяют как они должны располагаться в окне браузера.
( Есть несколько способов создания пользовательских виджетов самим. Вы также можете найти хороший выбор из сторонних библиотек виджетов в сети )

Главная панель (RootPanel)
==========================
На верхнем уровне иерархии любой GWT пользовательский интерфейс, всегда содержит главную панель (RootPanel).
RootPanel всегда обертывания фактический элемент HTML хост страницы. По умолчанию RootPanel обертывает элемент <body> HTML хост страницы.
Вы можете получить ссылку на эту RootPanel через вызов метода RootPanel.get(). Вы также можете указать RootPanel и для других HTML элементов страницы. Просто укажите ID атрибут интересующего HTML элемента в параметре метода RootPanel.get(String).

================
Главный класс 'EntryPoint' — входная точка приложения.
Метод 'onModuleLoad()' — это куда мы помещаем код запуска нашего приложения.
Последний шаг заключается в том, чтобы добавить нашу внешнюю вертикальную панель (VerticalPanel) к главной панели (RootPanel).

Проверка интерфейса
===================
Сохраните отредактированный файл и запустить в хост-режиме.

Добавление слушателей событий
=============================
GWT является событие-ориентированным (это означает, что весь код выполняется в ответ на некоторые другие события).

Интерфейс слушателя
===================
сначала надо сообщить GWT, в каких типах событий вы заинтересованы (это известно как подписаться на события. С точки зрения виджета, мы говорим что виджет публикует события которые доставляются (перенаправляются) любым слушателям).

Подписка на события
===================
Существуют различные интерфейсы слушателей в GWT, например:
интерфейс ClickListener является простым обработчиком событий кликов мыши. Он содержит только один метод, onClick (Widget).
( Вы заметите, что мы использовали анонимный внутренний класс для реализации ClickListener. В нем мы определили метод onClick (Widget), в котором делегируем вызовметода, addStock() )

Адаптеры слушателей
===================
GWT имеет класс - адаптер. Адаптеры просто пустые реализации того или иного интерфейса.


GWT (Google Web Toolkit) ... набор полезных инструментов
========================
Версия 1.0 вышла в мае 2006-го года
Версия 1.6 Google Eclipse Plugin структура проекта соответствует спецификации Web Application
Версия 2.0 'Development Mode', 'Code Splitting', 'Декларативный UI', 'Client Bundle'
Версия 2.1 'MVP-концепция', 'RequestFactory/Editors'
Версия 2.2 'UI Designer', 'поддержка HTML5 Canvas', остаётся только 'Java 1.6'
( GWT активно развивается, при том что уже содержит в себе всё необходимое )

----------------------------------------------------------------------------------------------------------------------------------[ Концепции GWT ]
● Java → JavaScript, JSNI
● Dev elopment Mode
● Code Splitting
● <Module>.gwt.xml
● MVC, MVP, RMVP, EventBus
● Deferred Binding
● Dependency Injection
● Remote Service
● JUnit
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Java → JavaScript, JSNI ....... (JavaScript Native Interface) Можно делать обёртки для нативных JavaScript виджетов. JSNI можно использовать для оборачивания стронних компонентов, написанных на JavaScript, в GWT-виджеты
=======================
public native static void getJson(int requestId, String url, StockWatcher handler) 
/*-{
  ...
  document.body.appendChild(script);
}-*/;

EntryPoint .................... Любой GWT-проект начинается с точки входа

Development Mode .............. (плагин для вашего любимого IDE, плагин для вашего любимого браузера) помогает отлаживать проект: при изменении Java-кода достаточно нажать Ctrl+F5 в вашем браузере — и изменения придут в силу!

Code Splitting ................ позволяет загружать части проекта по отдельности: за счёт этого вы можете разбить проект на крупные модули — и пользователи будут счастливы!

<Module>.gwt.xml-файлы ........ то же, что и web.xml для веб-приложения: здесь хранится вся конфигурация проекта (Компоненты/Браузеры/Локали/Отладка)

Model View Controller (MVC)    ( View >> Controller >> Model )
Model View Presenter (MVP)     ( View <<>> Presenter <<>> Model )
                                        +-> Event Bus <-+
Reverse MVP (RMVP)             ( View <<>>  Presenter  <<>> Model )
EventBus ...................... центральный канал сообщения

Deferred Binding .............. (CompileTime-связывание)
                                Ответ на отсутствие Reflection
                                Динамическое создание имплементации на основе интерфейса (и только при необходимости).
                                инструмент для создания кроссбраузерных и межязыковых реализаций. То есть для приёмов, которые будут различаться между контекстами использования проекта.
======================
GWT.create(....class)

Dependency Injection .......... (Runtime-связывание)
                                Через фреймворки GWT INjection / Guice
                                Привязка экземпляров к интерфейсам в одной точке (отделение поведения от решения об имплементации)
                                Позволяет забыть об XML-настройкахи фабриках
                                позволяет вам с лёгкостью управлять имплементациями логических частей проекта во время его работы. (Например, подменять драйвера баз данных или имплементации сервисов. То, что вы делали в application-context.xml в Spring, но намного лучше)

Remote Service ................ серверное API, построенное на Java-интерфейсах
==============
public interface StringReverserService extends RemoteService {
    public String reverseString(String stringToReverse);
}
public interface StringReverserServiceAsync {
    void reverseString(String stringToReverse, AsyncCallback async);
}

JUnit ......................... GWT-код легко тестировать благодаря поддержке JUnit
=====
public class StockWatcherTest extends GWTTestCase {  
    public String getModuleName() {
        return "com.google.gwt.sample.stockwatcher.StockWatcher";
    }
    ...
}

Недостатки и замечания
======================
Всё равно требуется хорошее знание JavaScript
Ручная вёрстка (HTMLPanel) становится не поддерживаемой и не кроссбраузерной
GWT — для веб-приложений, а не для вычурных порталов
Писать свои или расширять существующие компоненты можно, но тогда забота о кроссбраузерности — на вас
Нет ориентировки на не-Java Server-Side (что ж, построим всё на RequestBuilder)
Одна JS-ошибка валит всё приложение (JavaScript-ошибки малоинформативны, придётся поотлаживать alert'ами. Есть же GWT.setUncaughtExceptionHandler)
Хотя с включённой отладочной информацией разобраться, конечно, легче. "Development Mode" работает медленнее, чем реальный код: проблемы с контролем событий
( Каждый обоснованный недостаток GWT имеет разумное решение )

MVP4G ......................... Аннотации — сила mvp4g
                                фреймворк облегчает работу с (R)MVP
                                + Организацию мульти-модульного приложения
                                + Проектирование и разработку шин событий
                                + Работу с историей (в т.ч. хэшбэнги#!)
                                Код с использованием фреймворка mvp4g значительно проще GWT-кода без его использования. Это достигается за счёт грамотного использования аннотаций у Пьера.
=====
● Чем помогает?
● Система аннотаций
● Реализация RMVP
● Реализация EventBus
● URL, HistoryConverters, #!
● Мультимодульность
● PlaceService
● Замечания
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
История и шины событий — каркас навигационной системы вашего сайта.
Модули можно загружать асинхронно! Значит пользователь не получит ненужных ему килобайтов, если не будет посещать какие-то разделы.
Замечания: При использовании GwtEvent, нужновнимательно следить за активацией презентеров. Коллбэки — проще.
Есть LazyView и LazyPresenter
В GWT есть обширнейшая библиотека компонентов и арсенал лэйаутов. Однако, разработка сайта с собственным уникальным стилем чревата проблемами с кроссбраузерностью.
( Кастомные компоненты Не наследовать, а делегировать - То есть лучше либо делать сайт как можно проще в плане дизайна,... либо следует выделить значительное количество времени проектировщиков UI, дизайнеров и программистов на проработку собственной библиотеки виджетов )
недостаток: Layouting - Если ваш сайт содержит логические блоки, которые выстраиваются в разном порядке, в зависимости от контекста.

i18n .......................... если вы научите переводчиков пользоваться properties-файлами или дадите им PoEdit или Pootle
                                (ResourceBundles) Позволяют использовать локализованные ресурсы
====
public interface ErrorsConstants extends ConstantsWithLookup {
    Map<String,String> errors(); 
}

ErrorsConstants_ru.properties
ERR_101 = Ошибка авторизации
ERR_102 = Неизвестная ошибка
ERR_103 = Ресурс не найден

errors = ERR_101, ERR_102, ERR_103


public interface LoginMessages extends Messages {
    public String enterName();
    public String emailExists(String email);
    public String emailInvalid(String email);
    public String loginFailed(String username);
    public String youFailedNTimes(@PluralCountint times);
}

public interface MenuConstants extends Constants {
    public String login();
    public String logout();
    public String contacts();
    public String settings();
}

LoginMessages_ru.properties
enterName = Введите имя
emailExists = E-mail {0} зарегистрирован в системе
emailInvalid = Некорректный e-mail {0}
loginFailed = Не удалось зайти пользователем {0}
youFailedNTimes = Кол-во неудачных попыток: {0,number}
youFailedNTimes[one] = {0,number} неудачная попытка
youFailedNTimes[few] = {0,number} неудачных попыток

MenuConstants_ru.properties
login= Войти
logout = Выйти
contacts = Контакты
settings = Настройки

LoginMessages messages = GWT.create(LoginMessages.class);
MenuConstants constants = GWT.create(MenuConstants.class);





*********************************************************************************************[ Открытые ]
- http://www.quizful.net/post/gwt-tutorial-introduction
- http://habrahabr.ru/post/113121/
-   http://milayanyaka.blogspot.com/p/blog-page_18.html
-   http://milayanyaka.blogspot.com/p/gwt-memory.html
-   http://habrahabr.ru/post/76043/
+ http://alextretyakov.blogspot.com/2011/10/4.html
- http://multiblog.ru/profile/admin/created/topics/page319/
- http://habrahabr.ru/post/113121/
+ http://bb3x.ru/blog/gwt-podglyadyivaem-v-peredavaemyie-dannyie/
-   https://github.com/arcbees/gwtp
-   http://gwtp-sample-tab.appspot.com/#!homeNewsPage
-   http://gwtp-sample-nested.appspot.com/
-   http://gwtp-sample-basic-spring.appspot.com/#home
-   http://gwtp-sample-basic.appspot.com/#response;textToServer=Sasha
- http://habrahabr.ru/post/192262/
- http://www.pvsm.ru/java/42351/print/
- http://sysmagazine.com/posts/192262/
- http://plugin.gwt-platform.googlecode.com/hg/update/
- http://habrahabr.ru/post/154321/
- http://habrahabr.ru/post/87728/
-   http://habrahabr.ru/post/141398/
-   http://samples.gwtproject.org/samples/Showcase/Showcase.html#!CwDatePicker
(Habra Test gwt)
- http://habrahabr.ru/post/246285/
-   http://snsankar.blogspot.com/
-   https://github.com/JobTest/vitrinaPredmainTask/tree/miratex-master/Task/src/test/java/com/miratex
-   https://github.com/Home-Java8/Java7/blob/master/README-3.md
-   https://github.com/Home-Java8/Java7/blob/master/src/main/java/com/HashMapStructure.java
-   https://github.com/TimReset/example.gwt.gxt.test
+ http://habrahabr.ru/company/haulmont/blog/248545/
+ http://habrahabr.ru/hub/gwt/
(gwt собеседование)
+ https://sites.google.com/site/progerbingbang/google-web-toolkit/unittestinggwtapplicationswithjunit
- http://archive.is/dxV40
- http://www.quizful.net/test/gwt-google-web-toolkit
- https://netbeans.org/kb/74/web/quickstart-webapps-gwt_ru.html
(gwt пример)
+ http://dou.ua/lenta/articles/gwt-and-build-systems/
+   http://j4sq.blogspot.com/2012/01/java-spring-hibernate.html
+ http://catine.ru/kuchniy/translation/gwt-dlya-nachinayushhix-podgotovka-k-rabote/
+ http://ru.tmsoftstudio.com/file/page/Eclipse4/e4_ch10_primer-sozdanie-gwt-prilozheniya-content-delivery-node-dlya-platformy-google-app-engine.html
+ http://gwt.org.ua/ru/tutorials/tutorial1-part1/
+ http://gwt.org.ua/ru/tutorials/tutorial1-part2/
-   http://gwt-rus.blogspot.com/
+ http://alextretyakov.blogspot.com/2011/10/4.html
+ http://www.tutorialspoint.com/gwt/gwt_create_application.htm
+ http://www.programcreek.com/2011/01/a-example-application-of-gwt/
- http://ru.stackoverflow.com/questions/52540/Сайты-с-туториалами-по-gwt-smartgwt

**********************************************[ Открытые ]
+ http://habrahabr.ru/post/246285/
+ http://127.0.0.1:8888/GxtModule.jsp#StudentsListPlace:list
+ https://netbeans.org/kb/74/web/quickstart-webapps-gwt_ru.html
+ http://habrahabr.ru/post/94844/
+ http://samples.gwtproject.org/samples/Showcase/Showcase.html#!CwHorizontalPanel
+ http://alextretyakov.blogspot.com/2011/10/4.html

+ https://www.youtube.com/watch?v=JnVxtLPUE9I
+ http://habrahabr.ru/post/81895/
+ http://ru.enetri.com/2010/05/18/1.html
+ http://habrahabr.ru/post/40444/
+ http://mrbool.com/using-google-web-toolkit-with-hibernate/29393

+ http://habrahabr.ru/post/40444/
+ http://habrahabr.ru/post/94844/
+ http://habrahabr.ru/post/22970/
+ http://gwt.org.ua/ru/blog/2008/04/03/gwt-dojo-draw-demo/
+ http://gwt.org.ua/ru/blog/2007/10/20/eclipse-team/
+ http://gwt.org.ua/demos/gwt-dojo-drawdemo/DojoSimpleDemo.html
+ http://ru.enetri.com/2010/05/18/1.html

**********************************************[ Открытые ]
+ http://habrahabr.ru/post/81895/
+ http://ru.enetri.com/2010/05/18/1.html
+ http://habrahabr.ru/post/40444/
+ http://mrbool.com/using-google-web-toolkit-with-hibernate/29393
+ http://alextretyakov.blogspot.com/2011/10/4.html
+ (JobTest/AddressBook) https://github.com/JobTest/AddressBook
+ http://samples.gwtproject.org/samples/Showcase/Showcase.html#!CwHorizontalPanel
+ http://habrahabr.ru/post/94844/
+ http://habrahabr.ru/post/246285/ >> http://127.0.0.1:8888/GxtModule.jsp#StudentsListPlace:list
- http://snsankar.blogspot.com/
+ (Learn about GWT + Spring + Hibernate integration) https://www.youtube.com/watch?v=JnVxtLPUE9I

(GWT MVP / View <<>> Presenter <<>> Model) https://github.com/Home-GWT/docs
(Spring / @SessionAttributes("myobject")) http://vmustafayev4en.blogspot.com/2012/10/power-of-springs-modelattribute-and.html
(Spring / Controller) https://github.com/JobTest/vitrinaPredmainTask/tree/miratex-master/Task/src/test/java/com/miratex
(Spring / @Transactional) https://github.com/JobTest/vitrinaPredmainTask/tree/miratex-master/Task
* (Учебник GWT) https://drive.google.com/file/d/0B418nT5Bo9w_engtSTdpVDllY2s/view?pli=1
* (Введение в платформу веб-инструментария Google Web Toolkit) https://netbeans.org/kb/74/web/quickstart-webapps-gwt_ru.html
(Hibernate) https://github.com/JobTest/AddressBookDB
(Hibernate cache) http://habrahabr.ru/post/135176/
(Жизненный цикл потока) https://github.com/Home-Java8/MyMap/blob/master/description.txt
(Евгений Борисов — Spring-потрошитель, часть 1) https://mail.yandex.ua/?uid=40270829&login=sashakmets#message/2370000006227199072/r=%D0%B7%D0%B0%D0%B3%D0%BE%D0%BB%D0%BE%D0%B2%D0%BE%D0%BA&pos=46&reqid=3487605fa0b4b225ee74c7fa6abe398d&filter=folder:,attaches:no,dates=-
(java hibernate пример) https://mail.yandex.ua/?uid=40270829&login=sashakmets#message/2370000006060497655/r=%D0%B7%D0%B0%D0%B3%D0%BE%D0%BB%D0%BE%D0%B2%D0%BE%D0%BA&pos=91&reqid=3487605fa0b4b225ee74c7fa6abe398d&filter=folder:,attaches:no,dates=-
(java сокеты многопоточность) https://mail.yandex.ua/?uid=40270829&login=sashakmets#message/2560000000729919226
(github ** gwt-mvp4g-layouting-demo) https://github.com/shamansir/gwt-mvp4g-layouting-demo
(Home-SOAP/SOAPExample) https://github.com/Home-SOAP/SOAPExample/blob/master/src/main/java/dev/bay/ws/publisher/Publisher.java

(java servlet методы)
http://www.java2ee.ru/servlets/lifecycle.html
http://blog-tago.blogspot.com/2011/02/listeners.html
(java что такое сессия)
http://crypto.pp.ua/2010/06/seans-sessiya-v-java/
http://javatutor.net/books/tiej/servlets
(что такое enterprise javabeans)
* http://ejb.javadev.ru/
(Руководство программиста Enterprise JavaBeans) http://www.javaportal.ru/java/tutorial/EJBProgrammersGuide.pdf
https://ru.wikipedia.org/wiki/Enterprise_JavaBeans

(Re: BMW530 е39 X5 2001 * 1 700 $ (098 418 9440) * olx + машина по доверенности срок кончился) https://mail.yandex.ua/?uid=40270829&login=sashakmets#message/2560000000316343629
                                                                                               http://kirovograd.kir.olx.ua/obyavlenie/avtomobil-bmw530-e39-IDdtJIX.html#b227283048

* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *[ Закрытые ]
(Справочные материалы)
          (quizful ** Введение в GWT) http://www.quizful.net/post/gwt-tutorial-introduction << http://archive.is/dxV40
	 (quizful ** Тест знаний GWT 1.6) http://www.quizful.net/test/gwt-google-web-toolkit
(habrahabr ** Введение в MVP GWT 2.1) http://habrahabr.ru/post/113121/
            (GWT Interview Questions) http://snsankar.blogspot.com/

(ИГРЫ на GWT)
-----------------------------------------------( работает через создание maven-проекта )
(Блог Милой Няки ** Standart) https://github.com/Home-GWT/Standart3 << http://milayanyaka.blogspot.com/p/blog-page_18.html
  (Блог Милой Няки ** Memory) https://github.com/Home-GWT/Memory3 << http://milayanyaka.blogspot.com/p/gwt-memory.html
-----------------------------------------------( простой проект, НЕработает потому-что нужны GAE-библиоеки для гугловскй авторизации )
  (Сапер на GWT) http://habrahabr.ru/post/76043/ >> https://github.com/wargoth/yaminesweeper >> https://github.com/wargoth/yaminesweeper/tree/test_refactoring
                 http://m.habrahabr.ru/post/76043/comments/
				 http://cofe-tv.blogspot.com/2011/02/blog-post_24.html

(MVP)
(Тестирование GWT приложений архитектуры MVP) http://habrahabr.ru/post/246285/
             (github ** example.gwt.gxt.test) https://github.com/TimReset/example.gwt.gxt.test

(GWTP)
-----------------------------------------------( мавен-проект реализован через MVP-фреймворк, НЕТ исходников )
(GWT-Platform основы работы с презентерами) http://habrahabr.ru/post/192262/ << http://sysmagazine.com/posts/192262/
                                            http://www.pvsm.ru/java/42351/print/
											http://multiblog.ru/profile/admin/created/topics/page319/
-----------------------------------------------( GWTP Samples Project Home )
           (github ** GWTP) https://github.com/arcbees/gwtp
         (GWTP Tabs Sample) http://gwtp-sample-tab.appspot.com/#!homeNewsPage
       (GWTP Nested Sample) http://gwtp-sample-nested.appspot.com/
(GWTP Basic Spring Example) http://gwtp-sample-basic-spring.appspot.com/#home
       (GWTP Basic Example) http://gwtp-sample-basic.appspot.com/#response;textToServer=Sasha

(gwt hibernate пример)
-----------------------------------------------
(github ** gwt-spring-hibernate-tutorial) https://github.com/chieukam/gwt-spring-hibernate-tutorial

(GWT виджеты)
                              (GWT.Начинающим на заметку) http://habrahabr.ru/post/141398/
                                 (GWT виджеты из коробки) http://samples.gwtproject.org/samples/Showcase/Showcase.html#!CwDatePicker
(если нужен продвинутый виджет, тогда SmartGWT и Ext-GWT) http://www.smartclient.com/smartgwt/showcase/#main

(MVP4G)
(веб-разработка на GWT и mvp4g) http://www.addconf.ru/presentations/ADD-2/presentations/AntonKotenko.pdf
     (gwt-mvp4g-layouting-demo) https://github.com/shamansir/gwt-mvp4g-layouting-demo
                                https://github.com/shamansir/gwt-mvp4g-layouting/
      (Mvp4g Showcase (v1.5.0)) http://mvp4gexsc.appspot.com/
                                https://code.google.com/p/mvp4g/source/browse/trunk/examples/?r=131
                                https://code.google.com/archive/p/mvp4g/downloads
                                http://mvp4g.googlecode.com/svn/maven2/releases/com/googlecode/mvp4g/mvp4g/1.5.0/
                                http://shamansir.github.io/gwt-mvp4g-layouting-demo/index-ru.html

(GWT – подглядываем в передаваемые данные) http://bb3x.ru/blog/gwt-podglyadyivaem-v-peredavaemyie-dannyie/
-----------------------------------------------
В GWT при первом входе на заказчика грузится логика, пускай и много, но лишь один раз. Позже загрузки между заказчиком и сервером ходят только чистые данные бизнес-логики.
Дабы показать на заказчике 1КБ данных (несколько строчек таблицы, скажем), вам придется передать в браузер 15-30 кБ html-а (считаем, что изображения и скрипты закешированы). А чай данных на странице обыкновенно значительно огромнее: заголовки, меню, разные блоки и т.д. Реально, довольно интенсивная данными и функционалом страница обыкновенно весит не менее 100-200 кБ. GWT же для отображения такой же страницы заберет с сервера 1 кБ данных и всё.

(Видеоурок — Java + Intellij IDEA 9 + GWT 2.0 + Apache Tomcat) http://habrahabr.ru/post/87728/ >> https://yadi.sk/public/?hash=0%2BCaswMj4phCN6w%2F3saSt48Lk23kT07makFceizeKw0%3D
  (Введение в платформу веб-инструментария Google Web Toolkit) https://netbeans.org/kb/74/web/quickstart-webapps-gwt_ru.html



+++++++++++++++++++++++++++++++++++++++++++++++
Libraries
Modules >> GWT
Modules >> Web
>> Artifacts
Facets >> GWT (Web)
Facets >> Web
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
http://not-accidental-chaos.blogspot.com/2013/09/persistence-unit.html
https://github.com/wizardjedi/my-spring-learning/wiki/Работа-с-базами-данных-на-основе-jpa
http://devcolibri.com/3575
*********************************************************************************************





