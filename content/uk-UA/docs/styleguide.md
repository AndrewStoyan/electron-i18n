# Стиль документації Electron

Це рекомендації для написання документації Electron.

## Заголовки

* Кожна сторінка має мати єдиний заголовок рівня `#` у верхній частині.
* Розділи цієї сторінки мають мати заголовки рівня `##`.
* Sub-chapters need to increase the number of `#` in the title according to their nesting depth.
* All words in the page's title must be capitalized, except for conjunctions like "of" and "and" .
* Only the first word of a chapter title must be capitalized.

Для прикладу `Швидкий старт`:

```markdown
# Quick Start

...

## Main process

...

## Renderer process

...

## Run your app

...

### Run as a distribution

...

### Manually downloaded Electron binary

...
```

Для довідника API є деякі винятки з цих правил.

## Правила Markdown

* Використовуйте `bash` замість `cmd` в блоках коду (згідно синтаксису підсвітки).
* Лінії мають вкладатися в 80 стовпчиків.
* Списки не можуть мати вкладеність більшу ніж 2 рівні ( згідно візуалізатору markdown).
* Всі `js` та `javascript` блоки коду перевіряються за допопмогою [standard-markdown](http://npm.im/standard-markdown).

## Підбір слів

* Використовуйте "буде" замість "б" коли описуєте результати.
* Надавайте перевагу "в процесі ___", а не "далі".

## Довідник API

Наступні правила застосовуються тільки для API документації.

### Заголовок сторінки

Кожна сторінка повинна використовувати актуальне ім'я об'єкту як назву, що повертається з `require('electron')`, як-от `BrowserWindow`, `autoUpdater` і `session`.

Під заголовком сторінки має бути стрічка опису, яка починається з `>`.

Для прикладу `session`:

```markdown
# session

> Управління сесією браузера, кукі, кешем, налаштуваннями проксі і тд.
```

### Методи та події модуля

Для модулів, що не є класами, їхні методи та події мають бути перелічені під `## Методи` та `## Події` розділами.

Для прикладу `autoUpdater`:

```markdown
# autoUpdater

## Події

### Подія: 'error'

## Методи

### `autoUpdater.setFeedURL(url[, requestHeaders])`
```

### Класи

* API classes or classes that are part of modules must be listed under a `## Class: TheClassName` chapter.
* One page can have multiple classes.
* Конструктори, повинні бути перераховані на `###` рівні.
* [Статичні методи](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/static) мають бути перераховані в розділі `### Статичні Методи`.
* [Методи об'єкта класу](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes#Prototype_methods) повинні біти перераховані в главі `### Методи Екземпляру`.
* Опис всіх методів, що повертають значення, повинен починатися з "Повертає `[TYPE]` - Опис повернення"
  * Якщо метод повертає `Object`, його структура може бути визначена з використанням двокрапки потім з нового рядка невпорядкований список властивостей у стилі параметрів функції.
* Події об'єкта класу повинні бути перераховані в розділі `### Події Еекземпляру`.
* Властивості об'єкта класу повинні бути перераховані в `### Instance Properties` розділі.
  * Власстивості об'єкта класу мають починатися з "A [тип властивості] ..."

Для прикладу `Session` та `Cookies` класи:

```markdown
# session

## Методи

### session.fromPartition(partition)

## Властивості

### session.defaultSession

## Клас: Session

### Події екзкмпляру

#### Подія: 'will-download'

### Методи екземпляру

#### `ses.getCacheSize(callback)`

### Властивості екземпляру

#### `ses.cookies`

## Клас: Cookies

### Методи екземпляру

#### `cookies.get(filter, callback)`
```

### Методи

Розділи методів мають мати наступну форму:

```markdown
### `objectName.methodName(required[, optional]))`

* `required` String - A parameter description.
* `optional` Integer (optional) - Another parameter description.

...
```

Заголовок може мати рівні `###` чи `####` в залежності від того, чи це метод модуля чи класу.

For modules, the `objectName` is the module's name. For classes, it must be the name of the instance of the class, and must not be the same as the module's name.

Наприклад, методи класу `Session` у модулі `session` повинні використовувати `ses` як `objectName`.

Необов'язкові аргументи мають бути зазначені в квадратні дужки `[]`, що оточують необов'язковий аргумент, а також кома, якщо за необов'язковим аргументом слідує ще один аргумент:

```
required[, optional]
```

Below the method is more detailed information on each of the arguments. The type of argument is notated by either the common types:

* [`String`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)
* [`Number`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)
* [`Object`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)
* [`Array`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
* [`Boolean`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)
* Чи нестандартний тип як Electron's [`WebContent`](api/web-contents.md)

If an argument or a method is unique to certain platforms, those platforms are denoted using a space-delimited italicized list following the datatype. Values can be `macOS`, `Windows`, or `Linux`.

```markdown
* `animate` Boolean (optional) _macOS_ _Windows_ - Animate the thing.
```

Аргументи типу `Array` повинні вказувати, які саме елементи включає масив та бути вказані в описі нижче.

Опис аргументів для типу `Function` повинно бути чітко зазначено, як саме мають бути названі та перелік типів цих аргументів, що будут передані в функцію.

### Події (Events)

Розділи подій мають мати наступну форму:

```markdown
### Event: 'wake-up'

Returns:

* `time` String

...
```

Назва повинна починатися с `###` або `####`-рівня в залежності від того, це подія модуля чи класу.

Аргументи події слідують тим же правилам що й методи.

### Властивості (Properties)

Розділи властивостей мають мати наступну форму:

```markdown
### session.defaultSession

...
```

Назва повинна починатися с `###` або `####`-рівня в залежності від того, це властивість модуля чи класу.

## Переклади документації

Переклади документів Electron знаходяться в директорії `docs-translations`.

Щоб додати інший набір (або частковий набір):

* Створіть піддиректорію з назвою абревіатури мови.
* Перекладіть файли.
* Update the `README.md` within your language directory to link to the files you have translated.
* Add a link to your translation directory on the main Electron [README](https://github.com/electron/electron#documentation-translations).

Зауважте, що файли в `docs-translations` мають містити тільки переклади, оригінальні англійські файли не повинні копіюватися туди.
