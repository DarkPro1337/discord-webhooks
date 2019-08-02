---
title: "IFTTT Platform"
date: 2018-07-25T00:13:07+03:00
weight: 10
draft: false
---
[**IFTTT Platform**](https://platform.ifttt.com/maker) позволяет вам создавать и публиковать апплеты, чтобы вы могли делиться ими с другими. Также он позволяет вставить скрипт, который будет выполняться после запуска. Таким образом, вы можете изменять выходные данные и пропускать действия используя Typescript/Javascript.

* [Учебник Javascript](https://learnxinyminutes.com/docs/ru-ru/javascript-ru/)
* [Учебник Typescript](https://learnxinyminutes.com/docs/ru-ru/typescript-ru/)

```typescript
// Каждый элемент данных триггера является строкой и доступен только для чтения, без исключений.
// Вместо того, чтобы писать `Twitter.newTweetByYou` и т.д. каждый раз вы можете сократить
// его до `Trigger` потому что апплет может иметь только один триггер на данный момент.
var Text = Twitter.newTweetByYou.Text;
var UserName = Trigger.UserName;
var LinkToTweet = Trigger.LinkToTweet;
var CreatedAt = Trigger.CreatedAt;

// Если вы не хотите конвертировать HEX код цвета в integer вы можете использовать одну из
// встроенных в JS функций или просто присвоить ему HEX код.
var Color = parseInt('1da1f2', 16);
var Color2 = 0x1da1f2;

// Meta.currentUserTime
// Meta.triggerTime
// Они оба возвращают объект Moment.js. Гляньте https://momentjs.com для дополнительной информации ;)

// Создание тела JSON
var json = {
  "embeds": [{
    "author": {
      "name": UserName,
      "url": LinkToTweet
    },
    "description": Text,
    "color": Color,
    "timestamp": Meta.triggerTime
  }]
};

// также вы можете написать его намного чище

var json = {
  embeds: [{
    author: {
      name: UserName,
      url: LinkToTweet
    },
    description: Text,
    color: Color,
    timestamp: Meta.triggerTime
  }]
};

// довольно аккуратно, да?

// .skip('комментарий') позволяет вручную пропускать действия. Комментарий будет отображаться в логах как причина..
if (Text.indexOf('skip') > 0) {
  MakerWebhooks.makeWebRequest.skip('Skipped!');
}

// .set[field] метод позволяет заменять данные действий
MakerWebhooks.makeWebRequest.setBody(JSON.stringify(json));

// Объяснение:
// JSON.stringify() - конвертирует JS объект в JSON [String]
// MakerWebhooks.makeWebRequest.setBody() - заменяет тело по упомолчанию на пользовательское

// Готово!
```
