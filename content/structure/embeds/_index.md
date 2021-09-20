---
title: "embeds"
date: 2018-07-24T19:26:57+03:00
draft: false
weight: 20
---
Добавляет сообщение с вложением. `embeds` это массив, который может содержать до 10 вложений в одном сообщении.

Пример:

```json
{
  "embeds": [{
    "title": "Здравствуй!",
    "description": "Привет! :grinning:"
  }]
}
```

![](./../img/embeds_1.png)

```json
{
  "embeds": [
    {
      "title": "Мяу!",
      "color": 32768
    },
    {
      "title": "Мяу-мяу!",
      "color": 13369344
    }
  ]
}
```

![](./../img/embeds_2.png)
