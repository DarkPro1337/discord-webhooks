---
title: "timestamp"
date: 2018-07-24T20:15:50+03:00
draft: false
weight: 75
---
Позволяет вам добовлять `timestamp` во вложение к сообщению. Время хранится как строка в следующем фомате: `"YYYY-MM-DDTHH:MM:SS.MSSZ"` . Если `footer` был использован то он будет разделён маркером \( • \). Так же, это особое поле, поскольку оно может выводить разное время основываясь на устройстве пользователя.

{{% notice note %}}
`timestamp` это не просто текст. Это преобразованный UTC формат даты и времени. Он отображает разное время из-за часовых поясов. Посмотрите пример ниже: Я поставил 12pm но он показывает 3pm из-за часового пояса UTC+3.
{{% /notice %}}

Пример:

```json
{
  "embeds": [{
    "description": "Путешествие во времени!",
    "timestamp": "2015-12-31T12:00:00.000Z"
  }]
}
```

![](../img/timestamp.png)