# GoPay API Docs

Postman collections, integration examples, and SDK guides for the GoPay Merchant API.

## Quick Start

### 1. Импорт коллекции

1. Откройте Postman
2. Нажмите **Import** (Ctrl+O)
3. Перетащите или выберите файл `postman/GoPay-API.postman_collection.json`

### 2. Импорт environment

Импортируйте один из файлов окружения:

| Файл | Описание |
|------|----------|
| `postman/GoPay-Production.postman_environment.json` | Продакшн |
| `postman/GoPay-Testing.postman_environment.json` | Тестовый режим (`testing_mode: true`) |

### 3. Настройка ключей

1. Выберите импортированный environment в правом верхнем углу Postman
2. Нажмите на иконку глаза рядом с environment
3. Заполните значения:
   - `api_key` — ваш API-ключ
   - `secret_key` — ваш секретный ключ

### 4. Готово

Подпись (HMAC-SHA512) рассчитывается автоматически через Pre-request Script на уровне коллекции. Просто выберите любой запрос и нажмите **Send**.

## Эндпоинты

| Метод | Путь | Описание |
|-------|------|----------|
| POST | `/v1/payments` | Создать платёж |
| POST | `/v1/payments/query` | Получить статус платежа |
| POST | `/v1/static-qr/` | Создать статический QR-код |
| POST | `/v1/static-qr/query` | Получить QR по ID |
| POST | `/v1/payment-app` | Список платёжных приложений |

## Аутентификация

Все запросы подписываются с помощью HMAC-SHA512:

```
payload = nonce + "\n" + request_body + "\n"
signature = HMAC-SHA512(payload, secret_key).toUpperCase()
```

Заголовки добавляются автоматически:
- `GoPay-Api-Key` — API-ключ
- `GoPay-Nonce` — уникальный идентификатор запроса (UUID без дефисов, 32 символа)
- `GoPay-Signature` — подпись в верхнем регистре

## API Reference

Документация API: [doc.gopay.kg/v1/](https://doc.gopay.kg/v1/)

OpenAPI Schema: [doc.gopay.kg/v1/schema/](https://doc.gopay.kg/v1/schema/)
