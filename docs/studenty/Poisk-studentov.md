---
tags: [Студенты]
---

# Поиск студентов

Данный эндпоинт предоставляет функционал поиска студентов по платформе

<!-- 
theme: warning
 -->

 > Данный эндпоинт работает в связке с jwt-токеном, который требуется получить при авторизации

### Запрос

```curl
curl --request GET \
  --url http://127.0.0.1:3102/students \
  --header 'Authorization: Bearer JWT-TOKEN' \
  --header 'Content-Type: application/json'
```

### Ответ

<!-- 
type: tab
title: Пример ответа
-->
```json
[
  {
    "firstName": "occaecat commodo",
    "lastName": "incididunt dolor culpa ea id",
    "email": "xbfDX4cvsMp-p@bRiDCyI.llu",
    "birthDay": "1984-07-16",
    "skills": [
      {
        "title": "Excepteur",
        "id": "8003523e-fa3b-a5a7-5521-568b7e22a653"
      },
      {
        "title": "dolor Ut fugiat proident in",
        "id": "a7a782ab-e1af-227d-fc6e-3746264c4221"
      }
    ],
    "phone": "553-805-39",
    "id": "c3fdfa85-68b0-d6fa-385a-bbb313d1b82e"
  }
]
```

<!-- 
type: tab
title: Схема
-->
```yaml json_schema
title: Студенты
type: object
x-tags:
  - Студенты
description: Данная модель описывает сущность Студента в системе
properties:
  id:
    type: string
    format: uuid
  firstName:
    type: string
    example: Наталия Шипелова
    description: Имя пользователя
  lastName:
    type: string
    description: Фамилия пользователя
  email:
    type: string
    description: email пользователя
    format: email
  phone:
    type: string
    pattern: '^\d{3}\-\d{3}-\d{2}$'
    example: 987-987-22
    description: Телефончик
  birthDay:
    type: string
    format: date
    description: Дршечка
  skills:
    type: array
    uniqueItems: true
    items:
      type: object
      title: Hard скиллы пользователя
      properties:
        id:
          type: string
          format: uuid
        title:
          type: string
          description: Название скилла
      required:
        - title
      description: Модель описывает скиллы пользователя
required:
  - firstName
  - lastName
  - email
```
<!-- type: tab-end -->