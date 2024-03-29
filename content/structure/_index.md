---
title: "Структура вебхуков Discord"
date: 2018-07-23T22:58:42+03:00
draft: false
weight: 20
pre: "<b>2. </b>"
---
* [`username`](../../structure/username) - заменяет имя вебхука
* [`avatar_url`](../../structure/avatar_url) - заменяет аватар вебхука
* [`content`](../../structure/content) - устанавливает текст выводимый вебхуком \(до 2000 символов\)
* [`embeds`](../../structure/embeds) - массив вложенных объектов в сообщении. Это означает, что вы можете указать туда более одного объекта в одном сообщении
  * [`color`](../../structure/embeds/color) - устанавливает цвет для полоски вложения. Указывайте цвет в десятичной системе цифр, а не шестнадцатеричной. Используйте SpyColor для этого.
  * [`author`](../../structure/embeds/author) - добавляет блок автора во вложение
      * `name` - имя автора
      * `url` - ссылка на автора. Если бы использован `name` превращается в гиперссылку
      * `icon_url` - ссылка на иконку автора
  * [`title`](../../structure/embeds/title) - устанавливает заголовок вложения
  * [`url`](../../structure/embeds/url) - ссылка вложения. Если бы использован `title` превращается в гиперссылку
  * [`description`](../../structure/embeds/description) - текст описания
  * [`fields`](../../structure/embeds/fields) - массив объекта `field` во вложении
      * `name` - имя поля
      * `value` - значение поля
      * `inline` - если значение true, то поля будут отображаться на одной линии, но их может быть только 3 на одной линии, или 2 если был использован `thumbnail`
  * [`thumbnail`](../../structure/embeds/thumbnail) - добавляет миниатюрное изображение во вложение
      * `url` - ссылка на изображение
  * [`image`](../../structure/embeds/image) - добавляет изображение во вложение
      * `url` - ссылка на изображение
  * [`footer`](../../structure/embeds/footer) - добавляет "подвал" \(нижний блок\) во вложение
      * `text` - текст нижнего блока, не поддерживает [<i class="fab fa-markdown"></i> Markdown](../../other/discord-markdown#форматирование-текста)
      * `icon_url` - ссылка на иконку нижнего блока
  * `timestamp` - отметка времени по стандарту [ISO8601](https://ru.wikipedia.org/wiki/ISO_8601) \(`yyyy-mm-ddThh:mm:ss.msZ`\)
