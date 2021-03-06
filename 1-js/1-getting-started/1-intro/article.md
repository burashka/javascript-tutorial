# Введение в JavaScript

Давайте посмотрим, что такого особенного в JavaScript, почему именно он, и какие еще технологии существуют, кроме JavaScript.

## Что такое JavaScript?   

*JavaScript* изначально создавался для того, чтобы сделать web-странички "живыми".  
Программы на этом языке называются *скриптами*. В браузере они подключаются напрямую к HTML и, как только загружается страничка -- тут же выполняются.

**Программы на JavaScript -- обычный текст**. Они не требуют какой-то специальной подготовки.

В этом плане JavaScript сильно отличается от другого языка, который называется [Java](http://ru.wikipedia.org/wiki/Java).

[smart header="Почему <u>Java</u>Script?"]
Когда создавался язык JavaScript, у него изначально было другое название: "LiveScript". Но тогда был очень популярен язык Java, и маркетологи решили, что схожее название сделает новый язык более популярным.

Планировалось, что JavaScript будет эдаким "младшим братом" Java. Однако, история распорядилась по-своему, JavaScript сильно вырос, и сейчас это совершенно независимый язык, со своей спецификацией, которая называется [ECMAScript](https://ru.wikipedia.org/wiki/ECMAScript), и к Java не имеет никакого отношения.

У него много особенностей, которые усложняют освоение, но по ходу учебника мы с ними разберёмся.
[/smart]

JavaScript может выполняться не только в браузере, а где угодно, нужна лишь специальная программа -- [интерпретатор](http://ru.wikipedia.org/wiki/%D0%98%D0%BD%D1%82%D0%B5%D1%80%D0%BF%D1%80%D0%B5%D1%82%D0%B0%D1%82%D0%BE%D1%80). Процесс выполнения скрипта называют "интерпретацией".

[smart header="Компиляция и интерпретация, для программистов"]
Для выполнения программ, не важно на каком языке, существуют два способа: "компиляция" и "интерпретация". 

<ul>
<li>*Компиляция* -- это когда исходный код программы, при помощи специального инструмента, другой программы, которая называется "компилятор", преобразуется в другой язык, как правило -- в машинный код. Этот машинный код затем распространяется и запускается. При этом исходный код программы остаётся у разработчика.</li>
<li>*Интерпретация* -- это когда исходный код программы получает другой инструмент, который называют "интерпретатор", и выполняет его "как есть". При этом распространяется именно сам исходный код (скрипт). Этот подход применяется в браузерах для JavaScript.</li>
</ul>

Современные интерпретаторы перед выполнением преобразуют JavaScript в машинный код или близко к нему, оптимизируют, а уже затем выполняют. И даже во время выполнения стараются оптимизировать. Поэтому JavaScript работает очень быстро.
[/smart]

Во все основные браузеры встроен интерпретатор JavaScript, именно поэтому они могут выполнять скрипты на странице. Но, разумеется, JavaScript можно использовать не только в браузере. Это полноценный язык, программы на котором можно запускать и на сервере, и даже в стиральной машинке, если в ней установлен соответствующий интерпретатор.

[warn header="Поговорим о браузерах"]

Далее в этой главе мы говорим о возможностях и ограничениях JavaScript именно в контексте браузера.

[/warn]

## Что умеет JavaScript?   

Современный JavaScript -- это "безопасный" язык программирования общего назначения. Он не предоставляет низкоуровневых средств работы с памятью, процессором, так как изначально был ориентирован на браузеры, в которых это не требуется.

Что же касается остальных возможностей -- они зависят от окружения, в котором запущен JavaScript. В браузере JavaScript умеет делать всё, что относится к манипуляции со страницей, взаимодействию с посетителем и, в какой-то мере, с сервером: 

<ul>
<li>Создавать новые HTML-теги, удалять существующие, менять стили элементов, прятать, показывать элементы и т.п.</li>
<li>Реагировать на действия посетителя, обрабатывать клики мыши, перемещения курсора, нажатия на клавиатуру и т.п. </li>
<li>Посылать запросы на сервер и загружать данные без перезагрузки страницы (эта технология называется &quot;AJAX&quot;).</li>
<li>Получать и устанавливать cookie, запрашивать данные, выводить сообщения...</li>
<li>...и многое, многое другое!</li> 
</ul>

## Что НЕ умеет JavaScript?   

JavaScript -- быстрый и мощный язык, но браузер накладывает на его исполнение некоторые ограничения.. 

Это сделано для безопасности пользователей, чтобы злоумышленник не мог с помощью JavaScript получить личные данные или как-то навредить компьютеру пользователя. 

Этих ограничений нет там, где JavaScript используется вне браузера, например на сервере. Кроме того, современные браузеры предоставляют свои механизмы по установке плагинов и расширений, которые обладают расширенными возможностями, но требуют специальных действий по установке от пользователя

**Большинство возможностей JavaScript в браузере ограничено текущим окном и страницей.**

<img src="limitations.png" width="530" height="400">

<ul>
<li>JavaScript не может читать/записывать произвольные файлы на жесткий диск, копировать их или вызывать программы. Он не имеет прямого доступа к операционной системе.

Современные браузеры могут работать с файлами, но эта возможность ограничена специально выделенной директорией -- *"песочницей"*. Возможности по доступу к устройствам также прорабатываются в современных стандартах и частично доступны в некоторых браузерах.
</li>
<li>JavaScript, работающий в одной вкладке, не может общаться с другими вкладками и окнами, за исключением случая, когда он сам открыл это окно или несколько вкладок из одного источника (одинаковый домен, порт, протокол).

Есть способы это обойти, и они раскрыты в учебнике, но они требуют специального кода на оба документа, которые находятся в разных вкладках или окнах. Без него, из соображений безопасности, залезть из одной вкладки в другую при помощи JavaScript нельзя. 
</li>
<li>Из JavaScript можно легко посылать запросы на сервер, с которого пришла страница. Запрос на другой домен тоже возможен, но менее удобен, т. к. и здесь есть ограничения безопасности. 
</li>
</ul>

## В чём уникальность JavaScript?   

Есть как минимум *три* замечательных особенности JavaScript:

[compare]
+Полная интеграция с HTML/CSS.
+Простые вещи делаются просто.
+Поддерживается всеми распространёнными браузерами и включён по умолчанию.
[/compare]

**Этих трёх вещей одновременно нет больше ни в одной браузерной технологии.** 

Поэтому JavaScript и является самым распространённым средством создания браузерных интерфейсов.

## Тенденции развития

Перед тем, как вы планируете изучить новую технологию, полезно ознакомиться с её развитием и перспективами. Здесь в JavaScript всё более чем хорошо.

### HTML 5

*HTML 5* -- эволюция стандарта HTML, добавляющая новые теги и, что более важно, ряд новых возможностей браузерам.

Вот несколько примеров:
<ul>
<li>Чтение/запись файлов на диск (в специальной "песочнице", то есть не любые).</li>
<li>Встроенная в браузер база данных, которая позволяет хранить данные на компьютере пользователя.</li>
<li>Многозадачность с одновременным использованием нескольких ядер процессора.</li>
<li>Проигрывание видео/аудио, без Flash.</li>
<li>2D и 3D-рисование с аппаратной поддержкой, как в современных играх.</li>
</ul>

Многие возможности HTML5 всё ещё в разработке, но браузеры постепенно начинают их поддерживать.

[summary]Тенденция: JavaScript становится всё более и более мощным и возможности браузера растут в сторону десктопных приложений.[/summary]

### EcmaScript 6

Сам язык JavaScript улучшается. Современный стандарт EcmaScript 5 включает в себя новые возможности для разработки, EcmaScript 6 будет шагом вперёд в улучшении синтаксиса языка.

Современные браузеры улучшают свои движки, чтобы увеличить скорость исполнения JavaScript, исправляют баги и стараются следовать стандартам.

[summary]Тенденция: JavaScript становится всё быстрее и стабильнее, в язык добавляются новые возможности.[/summary]

Очень важно то, что новые стандарты HTML5 и ECMAScript сохраняют максимальную совместимость с предыдущими версиями. Это позволяет избежать неприятностей с уже существующими приложениями.

Впрочем, небольшая проблема с "супер-современными штучками" всё же есть. Иногда браузеры стараются включить новые возможности, которые ещё не полностью описаны в стандарте, но настолько интересны, что разработчики просто не могут ждать.  

...Однако, со временем стандарт меняется и браузерам приходится подстраиваться к нему, что может привести к ошибкам в уже написанном, основанном на старой реализации, JavaScript-коде. Поэтому следует дважды подумать перед тем, как применять на практике такие "супер-новые" решения.

При этом все браузеры сходятся к стандарту, и различий между ними уже гораздо меньше, чем всего лишь несколько лет назад.

[summary]Тенденция: всё идет к полной совместимости со стандартом.[/summary]


## Альтернативные браузерные технологии

Вместе с JavaScript на страницах используются и другие технологии. Связка с ними может помочь достигнуть более интересных результатов в тех местах, где браузерный JavaScript пока не столь хорош, как хотелось бы. 

### Java   

Java -- язык общего назначения, на нём можно писать самые разные программы. Для интернет-страниц есть особая возможность - написание *апплетов*.

*Апплет* -- это программа на языке Java, которую можно подключить к HTML при помощи тега `applet`, выглядит это примерно так:

```html
<!--+ run -->
<applet code="BTApplet.class" codebase="/files/tutorial/intro/alt/">
  <param name="nodes" value="50,30,70,20,40,60,80,35,65,75,85,90">
  <param name="root" value="50">
</applet>
```

Такой тег загружает Java-программу из файла `BTApplet.class` и выполняет её с параметрами `param`. Апплет выполняется в отдельной части страницы, в прямоугольном "контейнере". Все действия пользователя внутри него обрабатывает апплет. Контейнер, впрочем, может быть и спрятан, если апплету нечего показывать.

Конечно, для этого на компьютере должна быть установлена и включена среда выполнения Java, включая браузерный плагин. Кроме того, апплет должен быть подписан сертификатом издателя (в примере выше апплет без подписи), иначе Java заблокирует его.

**Чем нам, JavaScript-разработчикам, может быть интересен Java?**

В первую очередь тем, что подписанный Java-апплет может всё то же, что и обычная программа, установленная на компьютере посетителя. Конечно, для этого понадобится согласие пользователя при открытии такого апплета.

[compare]
+Java может делать *всё* от имени посетителя, совсем как установленная программа. Потенциально опасные действия требуют подписанного апплета и согласия пользователя.
-Java требует больше времени для загрузки.
-Среда выполнения Java, включая браузерный плагин, должна быть установлена на компьютере посетителя и включена.
-Java-апплет не интегрирован с HTML-страницей, а выполняется отдельно. Но он может вызывать функции JavaScript.
[/compare]


### Плагины и расширения для браузера

Все современные браузеры предоставляют возможность написать плагины. Для этого можно использовать как JavaScript (Chrome, Opera, Firefox), так и язык С (ActiveX для Internet Explorer).

Эти плагины могут как отображать содержимое специального формата (плагин для проигрывания музыки, для показа PDF), так и взаимодействовать со страницей.

Как и в ситуации с Java-апплетом, у них широкие возможности, но посетитель поставит их в том случае, если вам доверяет.

### Adobe Flash   

Adobe Flash -- кросс-браузерная платформа для мультимедиа-приложений, анимаций, аудио и видео. 

*Flash-ролик* -- это скомпилированная программа, написанная на языке ActionScript. Её можно подключить к HTML-странице и запустить в прямоугольном контейнере.

В первую очередь Flash полезен тем, что позволяет **кросс-браузерно** работать с микрофоном, камерой, с буфером обмена, а также поддерживает продвинутые возможности по работе с сетевыми соединениями. 

[compare]
+Сокеты, UDP для P2P и другие продвинутые возможности по работе с сетевыми соединениями
+Поддержка мультимедиа: изображения, аудио, видео. Работа с веб-камерой и микрофоном.
-Flash должен быть установлен и включён. А на некоторых устройствах он вообще не поддерживается.
-Flash не интегрирован с HTML-страницей, а выполняется отдельно.
-Существуют ограничения безопасности, однако они немного другие, чем в JavaScript.
[/compare]

Из Flash можно вызывать JavaScript и наоборот, поэтому обычно сайты используют JavaScript, а там, где он не справляется -- можно подумать о Flash.


## Языки поверх JavaScript


Синтаксис JavaScript устраивает не всех: одним он кажется слишком свободным, другим -- наоборот, слишком ограниченным, третьи хотят добавить в язык дополнительные возможности, которых нет в стандарте...

Это нормально, ведь требования и проекты у всех разные. 

В последние годы появилось много языков, которые добавляют различные возможности "поверх" JavaScript, а для запуска в браузере -- при помощи специальных инструментов "трансляторов" превращаются в обычный JavaScript-код.

Это преобразование происходит автоматически и совершенно прозрачно, при этом неудобств в разработке и отладке практически нет.

При этом разные языки выглядят по-разному и добавляют совершенно разные вещи:

<ul>
<li>Язык [CoffeeScript](http://coffeescript.org/) -- это "синтаксический сахар" поверх JavaScript. Он сосредоточен на большей ясности и краткости кода. Как правило, его особенно любят программисты на Ruby.</li>
<li>Язык [TypeScript](http://www.typescriptlang.org/) сосредоточен на добавлении строгой типизации данных. Он предназначен для упрощения разработки и поддержки больших систем. Его разрабатывает Microsoft.</li>
<li>Язык [Dart](https://www.dartlang.org/) интересен тем, что он не только транслируется в JavaScript, как и другие языки, но и имеет свою независимую среду выполнения, которая даёт ему ряд возможностей и доступна для встраивания в приложения (вне браузера). Он разрабатывается компанией Google.</li>
</ul>

[smart header="ES6 и ES7 прямо сейчас"]
Существуют также трансляторы, которые берут код, использующий возможности будущих стандартов JavaScript, и преобразуют его в более старый вариант, который понимают все браузеры.

Например, [babeljs](https://babeljs.io/).

Благодаря этому, мы можем использовать многие возможности будущего уже сегодня.
[/smart]


## Итого

Язык JavaScript уникален благодаря своей полной интеграции с HTML/CSS. Он работает почти у всех посетителей.

...Но хороший JavaScript-программист не должен забывать и о других технологиях.

Ведь наша цель -- создание хороших приложений, и здесь Flash, Java и браузерные расширения имеют свои уникальные возможности, которые можно использовать вместе с JavaScript.

Что же касается CoffeeScript, TypeScript и других языков, построенных над JavaScript -- они могут быть очень полезны. Рекомендуется посмотреть их, хотя бы в общих чертах, но, конечно, уже после освоения самого JavaScript.

