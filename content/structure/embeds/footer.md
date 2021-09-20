---
title: "footer"
date: 2018-07-24T20:15:30+03:00
draft: false
weight: 70
---
Позволяет вам добавить "подвал" во вложение сообщения. `footer` это объект который включает два значения:

* `text` - устанавливает имя для автора объекта. Markdown здесь не работает!
* `icon_url` - устанавливает иконку для автора объекта. Требует значение `text`.

Пример:

```json
{
  "embeds": [{
      "footer": {
        "text": "wow! *such markdown* :smirk:",
        "icon_url": "https://i.imgur.com/1PQ1yfi.png"
      },
      "description": "Ваша пицца готова!\n:timer:ETA: 10 минут."
  }]
}
```

![](../img/footer.png)
