![alt text](https://i.imgur.com/4PImKjv.png)

# Настройка
1. Создайте [гугл-форму](https://docs.google.com/forms/u/0/)
2. Откройте редактор скриптов
 
![alt text](https://i.imgur.com/wYrU7qE.png)

3. Вставьте скрипт

![alt text](https://i.imgur.com/djMSntQ.png)

```sh
function onSubmit(e) {
  var discordPayload = { 
    content: '',
    embeds: [{
      type: 'rich',
      title: '',
      color: 16711680,
      fields: []
    }]
  }
  e.response.getItemResponses().forEach(function(i) {
    var v = i.getResponse() || 'None'
    discordPayload.embeds[0].fields.push({ name: i.getItem().getTitle(), value: v })
  })
  UrlFetchApp.fetch('ССЫЛКА НА WEBHOOK', {
    method: 'post',
    payload: JSON.stringify(discordPayload),
    contentType: 'application/json'
  })
}
```


4. Создайте WEBHOOK в текстовом канале Discrod, куда хотите, чтобы приходил ответ. Скопируйте ссылку WebHook и вставьте вместо "ССЫЛКА НА WEBHOOK"

![alt text](https://i.imgur.com/57SAVeC.png)

![alt text](https://i.imgur.com/ozzFp3j.png)

5. Нажмите "Изменить" - "Триггеры текущего проекта" - (внизу) "Добавление триггера" - "Сохранить"

![alt text](https://i.imgur.com/bjiwxVN.png)

![alt text](https://media.discordapp.net/attachments/758623055098019901/758624169985310740/unknown.png?width=700&height=681)

6. Отправьте тестовый ответ, чтобы убедиться, что он работает.
