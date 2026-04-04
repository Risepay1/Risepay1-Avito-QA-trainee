## TC - 001: Создание с валидными данными

**Предусловие:** Сервер доступен, переменная `{{baseUrl}}` настроена

**Шаги:**
1. Отправить POST запрос на `{{baseUrl}}/api/1/item`
2. В Body указаны:
```json
{
  "sellerID": 123456,
  "name": "Test item",
  "price": 1000,
  "statistics": {
    "likes": 5,
    "viewCount": 100,
    "contacts": 10
  }
}
Ожидаемый результат: Статус 200 OK.
В Response указанны: 
•	Поле id (UUID формат) 
•	Поле sellerId (число) 
•	Поле name (строка) 
•	Поле price (число) 
•	Поле statistics (объект с likes, viewCount, contacts) 
•	Поле createdAt (дата/время)
Приоритет: High
TC-002: Создание объявления с нулевыми значениями статистики
Предусловие: Сервер доступен, переменная {{baseUrl}} настроена
Шаги:
1. Отправить POST запрос на {{baseUrl}}/api/1/item
2. В Body указаны:
•	"sellerID": 234567,
•	"name": "Test with zeros",
•	"price": 1000,
•	"statistics": {
•	"likes": 0,
•	"viewCount": 0,
•	"contacts": 0
Ожидаемый результат: Статус 200 OK.
В Response указанны:
•	Поле id (UUID формат)
•	Поле sellerId (число)
•	Поле name (строка)
•	Поле price (число)
•	Поле statistics (объект с likes, viewCount, contacts)
•	Поле createdAt (дата/время)
Ошибка: BR - 001
Приоритет: High
TC-003: Создание с минимальным sellerID (граничное значение)
Предусловие: Сервер доступен, переменная {{baseUrl}} настроена
Шаги:
1. Отправить POST запрос на {{baseUrl}}/api/1/item
2. В Body указаны:
•	"sellerID": 111111,
•	"name": "Min sellerID test",
•	"price": 1000,
•	"statistics": {
•	"likes": 1,
•	"viewCount": 1,
•	"contacts": 1
Ожидаемый результат: Статус 200 OK.
Приоритет: Medium
TC-004: Создание с максимальным sellerID (граничное значение)
Предусловие: Сервер доступен, переменная {{baseUrl}} настроена
Шаги:
1. Отправить POST запрос на {{baseUrl}}/api/1/item
2. В Body указаны:
•	"sellerID": 999999,
•	"name": "Max sellerID test",
•	"price": 1000,
•	"statistics": {
•	"likes": 1,
•	"viewCount": 1,
•	"contacts": 1
Ожидаемый результат: Статус 200 OK.
Приоритет: Medium
TC-005: Создание без обязательного поля sellerID
Предусловие: Сервер доступен, переменная {{baseUrl}} настроена
Шаги:
1. Отправить POST запрос на {{baseUrl}}/api/1/item
2. В Body указаны:
•	"name": "No sellerID",
•	"price": 1000,
•	"statistics": {
•	"likes": 1,
•	"viewCount": 1,
•	"contacts": 1
Ожидаемый результат: Статус 400 Bad Request. Response содержит сообщение об ошибке
Приоритет: High
TC-006: Создание без обязательного поля name
Предусловие: Сервер доступен, переменная {{baseUrl}} настроена
Шаги:
1. Отправить POST запрос на {{baseUrl}}/api/1/item
2. В Body указаны:
•	"sellerID": 345678,
•	"price": 1000,
•	"statistics": {
•	"likes": 1,
•	"viewCount": 1,
•	"contacts": 1
Ожидаемый результат: Статус 400 Bad Request. Response содержит сообщение об ошибке
Приоритет: High


