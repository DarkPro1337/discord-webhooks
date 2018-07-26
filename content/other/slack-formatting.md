---
title: "Slack форматирование"
date: 2018-07-27T01:34:11+03:00
weight: 10
draft: false
---
Вебхуки Discord так же поддерживают форматирование [Slack](https://slack.com/). Просто добавьте `/slack` к URL вебхука, чтобы использовать его.

## Первый слой

| **Discord** | **Slack** | **Комментарий** |
| --- | --- | --- |
| username | username |  |
| avatar\_url | icon\_url |  |
| content | text |  |
| embeds | attachments |  |

## embeds \(attachments\)

| **Discord** | **Slack** | **Комментарий** |
| --- | --- | --- |
| color | color | Поддерживает hex-коды цветов `"#4c73c7"` и три предустановленных цвета: `good` \(зелёный\), `warning` \(жёлтый\) и `danger` \(красный\). |
| author | - | Блок автора объявляется по разному. Смотрите таблицу [`author`](slack-formatting.md#author). |
| title | title |  |
| url | title\_link |  |
| description | text |  |
| fields | fields |  |
| image | - | Блок картинки объявляется по разному. Смотрите таблицу [`image`](slack-formatting.md#image). |
| thumbnail | - | Блок миниатюры объявляется по разному. Смотрите таблицу `thumbnail`. |
| footer | footer | Это не блок, смотрите таблицу [`footer`](slack-formatting.md#footer). |
| timestamp | ts | Требует формат времени [Unix-время](https://ru.wikipedia.org/wiki/Unix-%D0%B2%D1%80%D0%B5%D0%BC%D1%8F). |
| - | fallback | Краткое содержание для уведомлений или IRC. Не поддерживает разметку. Не уверен, что Discord поддерживает это. |
| - | pretext | Сломанная шткуа. Должна работать как `content`, появляясь перед вложением, но оно просто добавляется к `description`. |

## author

| **Discord** | **Slack** | **Комментарий** |
| --- | --- | --- |
| name | author\_name | Просто напишите его внутри `attachments`, как `color` и т.п. |
| url | author\_link |  |
| icon\_url | author\_icon |  |

## fields

| **Discord** | **Slack** | **Комментарий** |
| --- | --- | --- |
| name | title |  |
| value | value |  |
| inline | short |  |

## image

| **Discord** | **Slack** | **Комментарий** |
| --- | --- | --- |
| url | image\_url | Здесь нету блока `image`. Просто пишите его внутри `attachments`, как `color` и т.п. |

## thumbnail

| **Discord** | **Slack** | **Комментарий** |
| --- | --- | --- |
| url | thumb\_url | Здесь нету блока `thumbnail`. Просто пишите его внутри `attachments`, как `color` и т.п. |

<h2>footer</h2>

| **Discord** | **Slack** | **Комментарий** |
| --- | --- | --- |
| text | footer | Здесь нету блока `footer`. Просто пишите его внутри `attachments`, как `color` и т.п. |
| icon | footer\_icon |  |

## Пример

```json
{
  "username": "Вебхук",
  "icon_url": "https://i.imgur.com/8gzrpIh.png",
  "text": "Текст сообщения. До 2000 символов.",
  "attachments": [
    {
      "author_name": "DOGE",
      "author_link": "https://www.reddit.com/r/doge/",
      "author_icon": "https://i.imgur.com/1PQ1yfi.png",
      "title": "Заголовок",
      "title_link": "https://google.com/",
      "text": "Текст сообщения. Здесь можно использовать Markdown. *Курсив* **жирный** __подчёркнутый__ ~~зачёркнутый~~ [гиперссылка](https://google.com) `код`",
      "color": "#e8d44f",
      "fields": [
        {
          "title": "Тест",
          "value": "Ещё текста",
          "short": true
        },
        {
          "title": "Нам нужно больше текста",
          "value": "Агась",
          "short": true
        },
        {
          "title": "Используйте параметр `\"inline\": true` , если вы хотите чтоб поля распалагались на одной линии.",
          "value": "Ладно..."
        },
        {
          "title": "Спасибо",
          "value": "Не за что! :wink:"
        }
      ],
      "thumb_url": "https://i.imgur.com/2p68pbG.jpg",
      "image_url": "https://i.imgur.com/2p68pbG.jpg",
      "footer": "Вау! Как класно! :smirk:",
      "footer_icon": "https://i.imgur.com/AAeBJBp.png"
    }
  ]
}
```

![](../img/slack-formatting.png)

## Дополнительная информация

* [Выполнение Slack-совместимых вебхуков](https://discordapp.com/developers/docs/resources/webhook#execute-slackcompatible-webhook)
* [Входящие вебхуки](https://api.slack.com/incoming-webhooks)
* [Основы форматирования сообщений](https://api.slack.com/docs/message-formatting)
* [Прикрепление контента и ссылок к сообщению ](https://api.slack.com/docs/message-attachments)
