# Величко Дмитро ІПЗ 3.02
## Практично-лабораторне заняття №7
## Інтеграція клієнтської частини з RESTful API

Скопіюємо з 6 практичної роботи наш проект. Наш бек проект це той проект який був створений у ході 3-4 лабораторній, практичних роботах. 
### Back end
Відкриємо його і перш за все зайдемо у файл ```.env```.

Тут звертаємо увагу на рядок ```JWT_EXPIRATION```, за дефолтом тут стоїть 15 хвилин, змінюємо це значення на 60 хвилин.
![env_jwt](https://github.com/user-attachments/assets/ee4b2e12-e235-4a54-9605-d745cf945132)

Тепер якщо у нас докер контейнери є, то запускаємо Docker.

Після запуску запускаємо наш бекенд, за допомогою команди: ```npm run dev```

Після цього переходимо у Postman і робимо запит у каталозі ```auth\login``` ```POST``` запит для отримання токена.

![postman_token](https://github.com/user-attachments/assets/c21ecbd6-1d05-4388-a419-7634dbea83c4)


Тепер цей токен ставимо у файл ```.env``` у фронт-енді.

### Front end

Тепер відкриємо його. Додакмо у файл ```.env``` і вставимо такі рядки перше з яких це локальна адреса, а другий наш токен.

![env_front](https://github.com/user-attachments/assets/dc90b348-1353-4815-a865-28f53953047b)

Далі створюємо файл ```index.ts``` у каталозі ```api``` який у свою чергу знаходиться у каталозі ```src```.
![src_api_index](https://github.com/user-attachments/assets/729b9888-52e3-498a-9555-ad6e4ce80751)

Вставимо у цей файл ось такий зміст
![index_api](https://github.com/user-attachments/assets/5f994c9c-d803-4d3c-afd3-5ad15b120417)

АЛЕ перед цим додамо залежність axios. Для цього виконаємо команду: ```npm add axios```

Тепер перейдемо у файл у ```/pages/Entities.tsx``` і додамо дещо

![entities_1](https://github.com/user-attachments/assets/f5a63d37-968e-4390-9913-437ca4210b0a)
![entities_2](https://github.com/user-attachments/assets/610dd43c-a789-42a7-a172-3c651b36b11d)
![entities_3](https://github.com/user-attachments/assets/95391243-ce9e-412d-b5a9-f9ab4d77e82b)
![entities_4](https://github.com/user-attachments/assets/2eba8ae4-135e-4b3d-8014-f943bbd34de6)

Тепер перейдемо у файл ```index.ts``` який знаходиться у файлі ```entities```
![index_1_entities](https://github.com/user-attachments/assets/7abc5e72-1dfd-4cb5-bfd6-4ac12b7504e9)
![index_2_entities](https://github.com/user-attachments/assets/2ce3e2ec-3b80-4e41-97f7-cacdf1cc6d24)
![index_3_entities](https://github.com/user-attachments/assets/7c37bb23-96d9-45d8-8341-343e5c69c563)
![index_4_entities](https://github.com/user-attachments/assets/25d65030-9520-4604-9b02-2a58afaa0d19)
![index_5_entities](https://github.com/user-attachments/assets/d4f160b9-a200-43de-8ec7-cc33fc05016a)

У файлі ```/types/Entity.ts``` змінемо формат дати створення і дати оновлення
![update_entity](https://github.com/user-attachments/assets/a57bc13d-5548-4840-b4fb-5859655bdf02)

Все тепер з фронт-ендом усе.
Запустимо його за допомогою команди: ```pnpm run dev```

### Тепер результат:
## Ось наші сутності

![check_list](https://github.com/user-attachments/assets/06eb83e5-4eeb-4ed8-9e92-f7eaeb18825e)

## Тепер спробуємо замінити сутності, тобто змінити їхній зміст

![check_update](https://github.com/user-attachments/assets/c244c445-35e3-4cf3-981f-ac98b9e22cf3)

## Перевіримо паралельно на Postman

![check_update_postman](https://github.com/user-attachments/assets/1570ab04-62d3-4d7d-8952-5d160182eed6)


## Тепер перевіремо створення нової сутності
![create_new](https://github.com/user-attachments/assets/54b8d7d3-a1c7-4cc7-ba61-1d98c2a9af93)

## Тепер перевіяємо чи з'явився він у списку
![check_create_new](https://github.com/user-attachments/assets/ec68d264-7da0-4ae2-8d56-07bc5c7adcca)

## Тепер на Postman
![check_create_new_postman](https://github.com/user-attachments/assets/49ab260f-b6bc-4d0f-9ef0-7976bcfffea4)

## Тепер перевіремо видалення сутностей
Видалемо сутність ```Dima Velichko```

![check_delete](https://github.com/user-attachments/assets/3e3e04c8-8fbf-4179-914c-5ea2bf15629d)

## Тепер у Postman
![check_delete_postman](https://github.com/user-attachments/assets/7237a68d-f9d6-43b2-bfc8-6b3ec3cef8d0)

Як басимо усі операції CRUD  працюють вдало.

## Загальний висновок

У результаті роботи було успішно реалізовано інтеграцію клієнтської частини з RESTful API. Було повторно використано попередні проєкти з бекенду та фронтенду, налаштовано середовище, оновлено змінні конфігурації у `.env` файлах, а також підключено бібліотеку `axios` для зручної роботи з HTTP-запитами.

На стороні фронтенду були реалізовані функціональні компоненти, які дозволяють виконувати всі базові операції CRUD (створення, читання, оновлення, видалення) над сутностями. Усі ці дії були перевірені як через інтерфейс додатку, так і через Postman для підтвердження коректності обміну даними з API.

Таким чином, інтеграція клієнтської частини з серверною була виконана успішно, що підтверджується стабільною роботою усіх CRUD-операцій та синхронізацією даних між фронтендом і бекендом.



