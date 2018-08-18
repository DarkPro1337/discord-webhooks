---
title: "Twitch"
date: 2018-07-25T00:33:41+03:00
weight: 5
draft: false
---
## Обычная версия

#### if `Stream going live for X` then `Make a web request`

```json
{
  "embeds": [{
    "color": 6570405,
    "author":{
      "name":"{{ChannelName}}",
      "url":"{{ChannelUrl}}"
    },
    "description": "**is now streaming on Twitch**",
    "fields": [
      {
        "name": ":video_game: Game",
        "value": "{{Game}}",
        "inline": true
      },
      {
        "name": ":eye: Viewers",
        "value": "{{CurrentViewers}}",
        "inline": true
      }
    ],
    "image": {
      "url": "{{StreamPreview}}"
    },
    "footer": {
      "text": "http://twitch.tv",
      "icon_url": "https://d1qb2nb5cznatu.cloudfront.net/startups/i/114142-19c0993bf69c468f1350fd422bfad6b2-medium_jpg.jpg?buster=1410211530"
    }
  }]
}
```

![](../img/twitch-basic.png)

## Улучшенная версия

#### if `Stream going live for X` then `Make a web request`

{{% notice warning %}}
**В 8-ой и 21-ой строках вам нужно будет заменить текст URL AVATAR на ссылку со своим аватаром.** Вы можете указать как и с самого Twitch так и с любого хостинга. Я рекомендую использовать для этого [imgur](https://imgur.com/)!
{{% /notice %}}

```json
{
	"content": ":loudspeaker: Хей @everyone! {{ChannelName}} сейчас стримит {{ChannelUrl}} ! Залетайте! :wink:",
	"embeds": [{
		"color": 6570405,
		"author": {
			"name": "{{ChannelName}}",
			"url": "{{ChannelUrl}}",
			"icon_url": "URL AVATAR"
		},
		"description": "**[{{ChannelName}}]({{ChannelUrl}})** сейчас стримит на Twitch!",
		"fields": [{
			"name": ":video_game: Game",
			"value": "{{Game}}",
			"inline": true
		}, {
			"name": ":eye: Viewers",
			"value": "{{CurrentViewers}}",
			"inline": true
		}],
		"thumbnail": {
			"url": "URL AVATAR"
		},
		"image": {
			"url": " {{StreamPreview}}"
		},
		"footer": {
			"text": "twitch.tv | {{CreatedAt}}",
			"icon_url": "https://d1qb2nb5cznatu.cloudfront.net/startups/i/114142-19c0993bf69c468f1350fd422bfad6b2-medium_jpg.jpg?buster=1410211530"
		}
	}]
}
```

![](../img/twitch-ifttt_1.png)

## Версия для [IFTTT Platform](../../services/ifttt-platform)

#### if `Stream going live for X` filter `Filter code` then `Make a web request` {#if-stream-going-live-for-x-then-make-a-web-request-1}

{{% notice warning %}}
**В 7-ой строке вам нужно будет заменить текст URL AVATAR на ссылку со своим аватаром.** Вы можете указать как и с самого Twitch так и с любого хостинга. Я рекомендую использовать для этого [imgur](https://imgur.com/)!
{{% /notice %}}

{{% notice warning %}}
**IFTTT Platform понимает JSON, но вам нужно будет преобразовать его в TypeScript.**

* `{{ }}` - заменяется на `${ }`
* У пары ключ-значение с ключа нужно убрать кавычки \(`" "`\), а у значения нужно заменять кавычки \(`" "`\) на гравис (``` ` ` ```)
  * Если у пары ключ-значение, в значении указывается переменная, то её обрамлять не нужно!
{{% /notice %}}

{{% notice note %}}
Для лучшего понимания попробуйте поизменять мой пример.
{{% /notice %}}

{{% notice tip %}}
**Эта версия умеет генерировать случайные названия для первью стримов**, благодаря этому превью со стримов будут кэшироваться правильно. Так к примеру человек, который увидит уведомление о стриме, не будет видеть один  и тот же превью каждый раз.
{{% /notice %}}

### `Filter Code`

```typescript
var CreatedAt = Meta.triggerTime
var Game = Trigger.Game
var ChannelName = Trigger.ChannelName
var ChannelUrl = Trigger.ChannelUrl
var CurrentViewers = Trigger.CurrentViewers
var preview = Trigger.StreamPreview + '?v=' + Math.round(Math.random() * 1000000);
var body = { content: `:loudspeaker: Хей @everyone! ${ChannelName} сейчас стримит ${ChannelUrl} ! Залетайте! :wink:`, embeds: [{ color: 6570405, author: { name: `${ChannelName}`, url: `${ChannelUrl}`, icon_url: `URL AVATAR` }, description: `**[${ChannelName}](${ChannelUrl})** is now streaming on Twitch!`, fields: [{ name: `:video_game: Game`, value: `${Game}`, inline: true }, { name: `:eye: Viewers`, value: `${CurrentViewers}`, inline: true }], thumbnail: { url: `URL AVATAR` }, image: { url: preview }, footer: { text: "twitch.tv", icon_url: `https://d1qb2nb5cznatu.cloudfront.net/startups/i/114142-19c0993bf69c468f1350fd422bfad6b2-medium_jpg.jpg?buster=1410211530` }, timestamp: CreatedAt }] };
MakerWebhooks.makeWebRequest.setBody(JSON.stringify(body));
```

![](../img/twitch-ifttt_2.png)
