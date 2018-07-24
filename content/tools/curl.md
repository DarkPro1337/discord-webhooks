---
title: "cURL"
date: 2018-07-25T00:19:44+03:00
weight: 15
draft: false
---
[**cURL**](https://curl.haxx.se/) - это консольная утилита и библиотека для передачи данных через URL. Доступна для большинства платформ.

* Linux - устанавливается через менеджер пакетов.
* macOS - homebrew или MacPorts
* Windows - скачать файл и распаковать его в директорию, и добавить её в PATH.

## Использование

`curl -H "Content-Type: application/json" -X POST -d <body> <link>`

```bash
curl -H "Content-Type: application/json" -X POST -d '{"username": "Тест", "content": "Привет!"}' https://discordapp.com/api/webhooks/203019812404264973/rptBmYgoehu70kw2rItSlhRqKi7kMJh1bM2KCUUD2vR6grZckvtdl62h4xR7XWUS5463

# -H "Content-Type: application/json" - загаловок которые сообщает серверу, что вы отправляете JSON данные
# -X POST - использовать метод POST
# -d '{"username": "Тест", "content": "Привет!"}' - добавляет данные в запрос
```

```bash
url='https://discordapp.com/api/webhooks/203019812404264973/rptBmYgoehu70kw2rItSlhRqKi7kMJh1bM2KCUUD2vR6grZckvtdl62h4xR7XWUS5463'
curl -H "Content-Type: application/json" \
-X POST \
-d '{"username": "Тест", "content": "Привет!"}' $url
# вы можете сделать многострочную комманду используя бэкслэш `\` и установить ссылку как переменную
# и не нужно будет вставлять её снова и снова. Так же вы можете добавить её в ваш `.*rc` файл
```
