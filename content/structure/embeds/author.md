---
title: "author"
date: 2018-07-24T19:38:49+03:00
draft: false
weight: 35
---
Добавляет блок автора во вложение. `author` это объект который включает в себя три значения:

* `name` - устанавливает имя.
* `url` - устанавливает ссылку. Требует значения `name`. Если используется, преобразует `name` в гиперссылку.
* `icon_url` - устанавливает аватар. Требует значения `name`.

Пример:

```json
{
  "embeds": [{
    "author": {
      "name": "Доставщик пиццы 🍕",
      "url": "https://www.reddit.com/r/Pizza/",
      "icon_url": "https://i.imgur.com/1aErQKa.png"
    },
    "description": "Ваша пицца готова!\n:timer:ETA: 5 минут."
  }]
}
```

![](../img/author.png)
