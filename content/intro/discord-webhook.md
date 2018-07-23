---
title: "Discord Webhook"
date: 2018-07-23T22:17:15+03:00
draft: false
weight: 10
---
## Структура Вебхуков

Прежде чем использовать Вебхуки вы должны знать структуру. Все ниже перечисленные элементы необязательны, но вам всё равно придётся использовать [`content`](structure/content.md) и [`embeds`](structure/embeds/) хотя бы раз. Это минимальное требование.

* [`username`](structure/username.md) - заменяет имя вебхука
* [`avatar_url`](structure/avatar_url.md) - заменяет аватар вебхука
* [`content`](structure/content.md) - устанавливает текст выводимый вебхуком \(до 2000 символов\)
* [`embeds`](structure/embeds/) - массив вложенных объектов в сообщении. Это означает, что вы можете указать туда более одного объекта в одном сообщении
  * [`color`](structure/embeds/color.md) - устанавливает цвет для полоски вложения. Указывайте цвет в десятичной системе цифр, а не шестнадцатеричной. Используйте SpyColor для этого.
  * [`author`](structure/embeds/author.md) - добавляет блок автора во вложение
    * `name` - имя автора
    * `url` - ссылка на автора. Если бы использован `name` превращается в гиперссылку
    * `icon_url` - ссылка на иконку автора
  * [`title`](structure/embeds/title.md) - устанавливает заголовок вложения
  * [`url`](structure/embeds/url.md) - ссылка вложения. Если бы использован `title` превращается в гиперссылку
  * [`description`](structure/embeds/description.md) - текст описания
  * [`fields`](structure/embeds/fields.md) - массив объекта `field` во вложении
    * `name` - имя поля
    * `value` - значение поля
    * `inline` - если значение true, то поля будут отображаться на одной линии, но их может быть только 3 на одной линии, или 2 если был использован `thumbnail`
  * [`thumbnail`](structure/embeds/thumbnail.md) - добавляет миниатюрное изображение во вложение
    * `url` - ссылка на изображение
  * [`image`](structure/embeds/image.md) - добавляет изображение во вложение
    * `url` - ссылка на изображение
  * [`footer`](structure/embeds/footer.md) - добавляет "подвал" \(нижний блок\) во вложение
    * `text` - текст нижнего блока, не поддерживает [Markdown](other/discord-markdown.md#formatirovanie-teksta)
    * `icon_url` - ссылка на иконку нижнего блока
  * `timestamp` - отметка времени по стандарту [ISO8601](https://ru.wikipedia.org/wiki/ISO_8601) \(`yyyy-mm-ddThh:mm:ss.msZ`\)

## Пример Вебхука

```json
{
  "username": "Вебхук",
  "avatar_url": "https://i.imgur.com/8gzrpIh.png",
  "content": "Текст сообщения. До 2000 символов.",
  "embeds": [
    {
      "author": {
        "name": "DOGE",
        "url": "https://www.reddit.com/r/doge/",
        "icon_url": "https://i.imgur.com/1PQ1yfi.png"
      },
      "title": "Заголовок",
      "url": "https://google.com/",
      "description": "Текст сообщения. Здесь можно использовать Markdown. *Курсив* **жирный** __подчёркнутый__ ~~зачёркнутый~~ [гиперссылка](https://google.com) `код`",
      "color": 15258703,
      "fields": [
        {
          "name": "Текст",
          "value": "Ещё текста",
          "inline": true
        },
        {
          "name": "Нам нужно больше текста",
          "value": "Агась",
          "inline": true
        },
        {
          "name": "Используйте параметр `\"inline\": true` , если вы хотите чтоб поля распалагались на одной линии.",
          "value": "Ладно..."
        },
        {
          "name": "Спасибо!",
          "value": "Не за что! :wink:"
        }
      ],
      "thumbnail": {
        "url": "https://i.imgur.com/2p68pbG.jpg"
      },
      "image": {
        "url": "https://i.imgur.com/2p68pbG.jpg"
      },
      "footer": {
        "text": "Вау! Как класно! :smirk:",
        "icon_url": "https://i.imgur.com/AAeBJBp.png"
      }
    }
  ]
}
```

## Как он выглядит

![](/discord-webhooks/intro/img/discord-webhook_example.png?classes=shadow)
