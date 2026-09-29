# 🔧 GonzoProxy API Documentation

Клиентская документация

**Статус:** Production

Документация объединяет два раздела API:

* **A. Генерация прокси и справочники**: базовый URL `https://api.gonzoproxy.app/functions/v1/proxy-api`
* **B. Управление сабаккаунтами**: базовый URL `https://api.gonzoproxy.app/functions/v1`

***

### Авторизация

Все запросы к API (оба раздела) требуют заголовок `x-api-key`.

```http
x-api-key: <ваш_api_ключ>
Content-Type: application/json
```

**Как получить API-ключ:**

1. Откройте личный кабинет GonzoProxy.
2. Перейдите в раздел `Settings → API Keys`.
3. Создайте новый ключ.
4. Используйте его во всех API-запросах.

Не передавайте API-ключ в URL или query-параметрах. Используйте только HTTP-заголовок.

### Единицы измерения

Все значения трафика передаются и возвращаются в **байтах**.

| Значение |         Байты |
| -------- | ------------: |
| `1 GB`   |  `1000000000` |
| `5 GB`   |  `5000000000` |
| `10 GB`  | `10000000000` |

***

## A. Генерация прокси и справочники

Базовый URL:

```
https://api.gonzoproxy.app/functions/v1/proxy-api
```

### A.1 Генерация прокси

**Метод:** `POST` **Путь:** `/generate`

#### Параметры запроса

Передаются в JSON-теле запроса.

**Обязательный параметр**

| Параметр  | Тип      | Описание                                                    |
| --------- | -------- | ----------------------------------------------------------- |
| `country` | `string` | ISO-код страны (`US`) или полное название (`United States`) |

**Необязательные параметры**

| Параметр       | Тип       | Описание                              |
| -------------- | --------- | ------------------------------------- |
| `state`        | `string`  | Штат или регион                       |
| `city`         | `string`  | Город                                 |
| `zip`          | `string`  | Почтовый индекс                       |
| `isp`          | `string`  | Название интернет-провайдера          |
| `sd_code`      | `number`  | Код региона (subdivision code)        |
| `count`        | `number`  | Количество генерируемых прокси        |
| `rotation`     | `boolean` | Тип ротации IP                        |
| `ttl`          | `number`  | Время жизни сессии                    |
| `ttl_unit`     | `string`  | Единица измерения TTL                 |
| `format`       | `string`  | Формат строки прокси в ответе         |
| `login`        | `string`  | Собственный логин                     |
| `password`     | `string`  | Собственный пароль                    |
| `rg_id`        | `string`  | Дополнительный параметр sticky-сессии |
| `session_rand` | `string`  | Random seed для sticky-сессии         |

**Выбор пула**

Пул, из которого выдаётся прокси (резидентский, мобильный, датацентровый), задаётся параметром запроса. Если этот параметр не передать, `/generate` всё равно вернёт рабочую строку подключения, но она может оказаться из другого пула: строка подключается, а продукт за ней не тот. Прежде чем переносить строку в боевой контур, проверьте, к какому пулу она относится.

**О параметре `ttl`**

`ttl` задаёт запрошенное время жизни сессии, максимум 7 дней (например, `ttl=168` при `ttl_unit` в часах), но не гарантирует его. В нашем собственном прогоне 14 сентября 2026 года тот же IP на горизонте 84 минуты сохранили 51 сессия из 90 (56,7%, интервал Уилсона от 46,4% до 66,4%), причём половина потерь пришлась на первые 35 минут. Обрабатывайте смену адреса в коде, а не рассчитывайте на то, что сессия доживёт до конца.

### A.2 Справочники для фильтров

API позволяет получать доступные страны, регионы, города, ZIP-коды и интернет-провайдеров.

#### A.2.1 Список стран

**Метод:** `GET` **Путь:** `/countries`

#### A.2.2 Штаты / регионы

**Метод:** `GET` **Путь:** `/states` **Обязательный параметр:** `country`

#### A.2.3 Список городов

**Метод:** `GET` **Путь:** `/cities` **Обязательный параметр:** `country` **Необязательный параметр:** `state`

#### A.2.4 ZIP-коды

**Метод:** `GET` **Путь:** `/zips` **Обязательный параметр:** `country` **Необязательные параметры:** `state`, `city`

Пример ответа:

```json
{
  "zips": ["10001", "10002"]
}
```

#### A.2.5 Интернет-провайдеры (ISP)

**Метод:** `GET` **Путь:** `/isps` **Обязательный параметр:** `country` **Необязательные параметры:** `state`, `city`

Примеры запросов:

```
/isps?country=US
/isps?country=US&state=New York&city=New York
```

Пример ответа:

```json
{
  "isps": ["Comcast", "Verizon"],
  "isps_detailed": [
    { "isp_name": "Comcast", "isp_code": 1783 },
    { "isp_name": "Verizon", "isp_code": 1902 }
  ]
}
```

***

## B. Управление сабаккаунтами

Базовый URL:

```
https://api.gonzoproxy.app/functions/v1
```

### B.1 Список сабаккаунтов

Возвращает сабаккаунты, привязанные к вашему основному аккаунту.

```http
POST /list-sub-accounts
```

#### Запрос

```json
{}
```

#### Curl

```bash
curl -sS -X POST "https://api.gonzoproxy.app/functions/v1/list-sub-accounts" \
  -H "Content-Type: application/json" \
  -H "x-api-key: <ваш_api_ключ>" \
  -d '{}'
```

#### Ответ

```json
{
  "success": true,
  "data": {
    "sub_accounts": [
      {
        "proxy_login": "GonzoLoginTest",
        "sub_account_name": "Team 1",
        "is_active": true,
        "traffic_remaining": 2000000000,
        "traffic_total": 2000000000
      }
    ]
  }
}
```

#### Поля ответа

| Поле                | Тип              | Описание                     |
| ------------------- | ---------------- | ---------------------------- |
| `proxy_login`       | `string \| null` | Логин прокси сабаккаунта     |
| `sub_account_name`  | `string \| null` | Название сабаккаунта         |
| `is_active`         | `boolean`        | Активен ли сабаккаунт        |
| `traffic_remaining` | `number`         | Остаток трафика в байтах     |
| `traffic_total`     | `number \| null` | Общий лимит трафика в байтах |

### B.2 Статистика трафика сабаккаунта

Возвращает статистику использования трафика по конкретному сабаккаунту.

```http
POST /get-sub-account-traffic-stats
```

#### Параметры

| Поле          | Тип      | Обяз.        | Описание                                               |
| ------------- | -------- | ------------ | ------------------------------------------------------ |
| `proxy_login` | `string` | Да           | Логин прокси сабаккаунта                               |
| `period`      | `string` | Нет          | Период статистики. По умолчанию `day`                  |
| `date`        | `string` | Нет          | Дата периода. Например `2026-05-19`, `2026-05`, `2026` |
| `start_date`  | `string` | Для `custom` | Начало периода в формате `YYYY-MM-DD`                  |
| `end_date`    | `string` | Для `custom` | Конец периода в формате `YYYY-MM-DD`                   |
| `group_by`    | `string` | Нет          | Группировка для `custom`: `day` или `month`            |

Доступные значения `period`: `day`, `week`, `month`, `year`, `custom`

#### Curl: статистика за день

```bash
curl -sS -X POST "https://api.gonzoproxy.app/functions/v1/get-sub-account-traffic-stats" \
  -H "Content-Type: application/json" \
  -H "x-api-key: <ваш_api_ключ>" \
  -d '{
    "proxy_login": "GonzoLoginTest",
    "period": "day"
  }'
```

#### Curl: произвольный период

```bash
curl -sS -X POST "https://api.gonzoproxy.app/functions/v1/get-sub-account-traffic-stats" \
  -H "Content-Type: application/json" \
  -H "x-api-key: <ваш_api_ключ>" \
  -d '{
    "proxy_login": "GonzoLoginTest",
    "period": "custom",
    "start_date": "2026-05-01",
    "end_date": "2026-05-19",
    "group_by": "day"
  }'
```

#### Ответ

```json
{
  "success": true,
  "data": {
    "points": [
      {
        "time": "2026-05-19T00:00:00.000Z",
        "bytes": 125000000,
        "traffic_remaining": 1875000000
      }
    ],
    "total_bytes": 125000000,
    "period": "day",
    "date": "2026-05-19",
    "timezone": "UTC",
    "traffic_remaining": 1875000000,
    "proxy_login": "GonzoLoginTest",
    "sub_account_name": "Team 1",
    "is_active": true
  }
}
```

#### Поля `points[]`

| Поле                | Тип              | Описание                                         |
| ------------------- | ---------------- | ------------------------------------------------ |
| `time`              | `string`         | Время точки в UTC                                |
| `bytes`             | `number`         | Использованный трафик за интервал                |
| `traffic_remaining` | `number \| null` | Остаток трафика на этот момент, если есть данные |

### B.3 Изменение трафика или статуса сабаккаунта

Изменяет итоговый баланс трафика или активность сабаккаунта.

```http
POST /sub-account-adjust
```

Поддерживаемые операции: `set_traffic`, `activate`, `deactivate`

#### B.3.1 Установить трафик сабаккаунта

`target_traffic_bytes` это итоговый остаток трафика сабаккаунта, а не добавляемая разница.

Если у сабаккаунта сейчас `1 GB`, а нужно сделать `5 GB`, передайте `5000000000`.

```json
{
  "proxy_login": "GonzoLoginTest",
  "operation": "set_traffic",
  "target_traffic_bytes": 5000000000
}
```

Curl:

```bash
curl -sS -X POST "https://api.gonzoproxy.app/functions/v1/sub-account-adjust" \
  -H "Content-Type: application/json" \
  -H "x-api-key: <ваш_api_ключ>" \
  -d '{
    "proxy_login": "GonzoLoginTest",
    "operation": "set_traffic",
    "target_traffic_bytes": 5000000000
  }'
```

#### B.3.2 Активировать сабаккаунт

```json
{
  "proxy_login": "GonzoLoginTest",
  "operation": "activate"
}
```

Curl:

```bash
curl -sS -X POST "https://api.gonzoproxy.app/functions/v1/sub-account-adjust" \
  -H "Content-Type: application/json" \
  -H "x-api-key: <ваш_api_ключ>" \
  -d '{
    "proxy_login": "GonzoLoginTest",
    "operation": "activate"
  }'
```

#### B.3.3 Деактивировать сабаккаунт

При деактивации остаток трафика сабаккаунта возвращается на основной аккаунт.

```json
{
  "proxy_login": "GonzoLoginTest",
  "operation": "deactivate"
}
```

Curl:

```bash
curl -sS -X POST "https://api.gonzoproxy.app/functions/v1/sub-account-adjust" \
  -H "Content-Type: application/json" \
  -H "x-api-key: <ваш_api_ключ>" \
  -d '{
    "proxy_login": "GonzoLoginTest",
    "operation": "deactivate"
  }'
```

#### Ответ (для всех операций `sub-account-adjust`)

```json
{
  "success": true,
  "data": {
    "proxy_login": "GonzoLoginTest",
    "sub_account_name": "Team 1",
    "operation": "set_traffic",
    "target_traffic_bytes": 5000000000,
    "previous_sub_traffic_bytes": 2000000000,
    "delta_bytes": 3000000000,
    "parent_traffic_after": 7000000000,
    "sub_traffic_after": 5000000000,
    "is_active": true,
    "changed": true
  }
}
```

#### Поля ответа

| Поле                         | Тип              | Описание                                          |
| ---------------------------- | ---------------- | ------------------------------------------------- |
| `proxy_login`                | `string \| null` | Логин прокси сабаккаунта                          |
| `sub_account_name`           | `string \| null` | Название сабаккаунта                              |
| `operation`                  | `string`         | Выполненная операция                              |
| `target_traffic_bytes`       | `number`         | Итоговый трафик сабаккаунта                       |
| `previous_sub_traffic_bytes` | `number`         | Трафик сабаккаунта до операции                    |
| `delta_bytes`                | `number`         | Разница между старым и новым значением            |
| `parent_traffic_after`       | `number`         | Остаток трафика основного аккаунта после операции |
| `sub_traffic_after`          | `number`         | Остаток трафика сабаккаунта после операции        |
| `is_active`                  | `boolean`        | Итоговый статус сабаккаунта                       |
| `changed`                    | `boolean`        | Было ли фактическое изменение                     |

***

## Коды ответов API

### Общие коды (раздел A)

| Код   | Описание                           |
| ----- | ---------------------------------- |
| `200` | Успешный запрос                    |
| `400` | Ошибка параметров запроса          |
| `401` | Отсутствует или пустой `x-api-key` |
| `403` | Неверный или отключенный API-ключ  |
| `404` | Неверный адрес запроса             |
| `429` | Превышен лимит запросов            |
| `500` | Внутренняя ошибка сервиса          |

Формат ошибки:

```json
{
  "error": "Описание ошибки"
}
```

### Частые ошибки (раздел B / сабаккаунты)

| HTTP  | Ошибка                                                   | Описание                                                                      |
| ----- | -------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `400` | `Invalid JSON body`                                      | Некорректный JSON                                                             |
| `400` | `proxy_login is required`                                | Не передан `proxy_login`                                                      |
| `400` | `operation must be set_traffic, activate, or deactivate` | Некорректная операция                                                         |
| `400` | `target_traffic_bytes is required`                       | Для `set_traffic` не передан `target_traffic_bytes`                           |
| `401` | `Missing x-api-key header`                               | Не передан API-ключ                                                           |
| `403` | `Forbidden`                                              | Сабаккаунт не принадлежит вашему аккаунту                                     |
| `404` | `parent_not_found`                                       | API-ключ не найден                                                            |
| `404` | `sub_account_not_found`                                  | Сабаккаунт не найден                                                          |
| `409` | `sub_inactive`                                           | Нельзя изменить трафик отключенного сабаккаунта. Сначала выполните `activate` |
| `409` | `insufficient_parent_traffic`                            | Недостаточно трафика на основном аккаунте                                     |

<br>
