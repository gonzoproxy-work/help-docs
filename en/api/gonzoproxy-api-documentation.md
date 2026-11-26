# 🔧 GonzoProxy API Documentation

Client documentation

**Status:** Production

This documentation combines two API sections:

* **A. Proxy generation and reference lists**: base URL `https://api.gonzoproxy.app/functions/v1/proxy-api`
* **B. Sub-account management**: base URL `https://api.gonzoproxy.app/functions/v1`

***

### Authentication

All requests to the API (both sections) require an `x-api-key` header.

```http
x-api-key: <your_api_key>
Content-Type: application/json
```

**How to get an API key:**

1. Open your GonzoProxy dashboard.
2. Go to `Settings → API Keys`.
3. Create a new key.
4. Use it in all API requests.

Do not pass the API key in the URL or as a query parameter. Use the HTTP header only.

### Units

All traffic values are sent and returned in **bytes**.

| Value   |         Bytes |
| ------- | ------------: |
| `1 GB`  |  `1000000000` |
| `5 GB`  |  `5000000000` |
| `10 GB` | `10000000000` |

***

## A. Proxy generation and reference lists

Base URL:

```
https://api.gonzoproxy.app/functions/v1/proxy-api
```

### A.1 Generate proxy

**Method:** `POST` **Path:** `/generate`

#### Request parameters

Passed in the JSON request body.

**Required parameter**

| Parameter | Type     | Description                                            |
| --------- | -------- | ------------------------------------------------------ |
| `country` | `string` | ISO country code (`US`) or full name (`United States`) |

**Optional parameters**

| Parameter      | Type      | Description                         |
| -------------- | --------- | ----------------------------------- |
| `product`      | `string`  | Proxy pool, see "Choosing the pool" |
| `state`        | `string`  | State or region                     |
| `city`         | `string`  | City                                |
| `zip`          | `string`  | ZIP code                            |
| `isp`          | `string`  | Internet service provider name      |
| `sd_code`      | `number`  | Subdivision code                    |
| `count`        | `number`  | Number of proxies to generate       |
| `rotation`     | `boolean` | `true`: rotating IP. `false` or not sent: sticky session, see "Sticky session" |
| `ttl`          | `number`  | Requested sticky-session lifetime, up to 72 hours |
| `ttl_unit`     | `string`  | `hours` (default), `minutes` or `seconds` |
| `ip_hold`      | `boolean` | Keep the same IP: the connection fails instead of moving to a new IP. Sticky session only |
| `format`       | `string`  | Proxy string format in the response, see "Response" |
| `login`        | `string`  | Custom login                        |
| `password`     | `string`  | Custom password                     |
| `rg_id`        | `string`  | Additional sticky-session parameter |
| `session_rand` | `string`  | Random seed for sticky sessions     |

**Choosing the pool**

The pool is set by the `product` parameter:

| Value            | Pool                                            |
| ---------------- | ----------------------------------------------- |
| `residential`    | Residential. Also used when `product` is not sent |
| `mobile`         | Mobile                                          |
| `server_dynamic` | Datacenter                                      |

For the datacenter pool the API also accepts `datacenter` and `dc`. The value is not case-sensitive. An empty value is treated as `residential`. Any other value the API does not recognize, for example a typo, returns HTTP 400 with `product must be one of: "residential", "mobile", "server_dynamic"`.

In `POST /generate` the pool goes in the JSON body. In GET requests (the reference lists in A.2 and `GET /traffic` in A.3) it goes in the query string, for example `/countries?product=mobile`. Without it, GET requests use `residential`; in GET requests an unrecognized value is not an error and is treated as `residential` too.

#### Response

Example of a successful response with `format` set to `username:password@ip:port`. In place of `ip`, the string contains the connection address, usually a host name, shown here as `<host>`.

```json
{
  "success": true,
  "proxies": ["<username>:<password>@<host>:<port>"]
}
```

`proxies` holds as many strings as you asked for in `count`. The order of the parts and the separators in each string are set by `format`:

| `format`                           | String                    |
| ---------------------------------- | ------------------------- |
| not sent, or `user:pass@ip:port`   | `user:pass@ip:port` (default) |
| `1` or `ip:port:user:pass`         | `ip:port:user:pass`       |
| `2` or `user:pass:ip:port`         | `user:pass:ip:port`       |
| `3` or `ip:port@user:pass`         | `ip:port@user:pass`       |

The same templates written with `username:password` instead of `user:pass` are accepted too. An unsupported template returns HTTP 400 with `Unsupported format`, and a value longer than 32 characters returns HTTP 400 with `format too long (max 32 chars)`.

**Sticky session: `rotation`, `ttl`, `ttl_unit`, `ip_hold`**

* `rotation: true` gives a rotating IP. `ttl` and `ip_hold` are ignored in this mode.
* `rotation: false`, or `rotation` not sent, gives a sticky session: the string keeps the same IP for as long as it can.
* `ttl` is the requested lifetime of a sticky session. `ttl_unit` sets its unit: `hours` (default), `minutes` or `seconds`; `h`, `m` and `s` are accepted too. Any other unit returns HTTP 400 with `ttl_unit must be one of: "hours", "minutes", "seconds"`.
* The maximum is 72 hours. A larger value is cut to 72 hours in the same unit, without an error: `ttl: 500` in hours becomes 72 hours, `ttl: 5000` in minutes becomes 4320 minutes.
* `ip_hold: true` works only with `rotation: false`. If the IP of the session drops, the connection fails instead of moving to a new IP, and the session does not get a new address. To continue, request a new string. With `ip_hold` the login in the string contains `_iphold_max`.

`ttl` is a requested lifetime, not a guarantee: the IP can change earlier, for example when the device behind it goes offline. In our own run on 14 September 2026, 51 of 90 sessions (56.7%, Wilson interval 46.4% to 66.4%) still held the same IP after 84 minutes, and half of the losses happened inside the first 35 minutes. Handle an address change in your code instead of assuming the session survives.

### A.2 Reference lists for filters

The API lets you retrieve available countries, regions, cities, ZIP codes, and internet service providers.

#### A.2.1 List of countries

**Method:** `GET` **Path:** `/countries`

#### A.2.2 States / regions

**Method:** `GET` **Path:** `/states` **Required parameter:** `country`

#### A.2.3 List of cities

**Method:** `GET` **Path:** `/cities` **Required parameter:** `country` **Optional parameter:** `state`

#### A.2.4 ZIP codes

**Method:** `GET` **Path:** `/zips` **Required parameter:** `country` **Optional parameters:** `state`, `city`

Example response:

```json
{
  "zips": ["10001", "10002"]
}
```

#### A.2.5 Internet service providers (ISP)

**Method:** `GET` **Path:** `/isps` **Required parameter:** `country` **Optional parameters:** `state`, `city`

Example requests:

```
/isps?country=US
/isps?country=US&state=New York&city=New York
```

Example response:

```json
{
  "isps": ["Comcast", "Verizon"],
  "isps_detailed": [
    { "isp_name": "Comcast", "isp_code": 1783 },
    { "isp_name": "Verizon", "isp_code": 1902 }
  ]
}
```

### A.3 Traffic balance

**Method:** `GET` **Path:** `/traffic` **Optional parameter:** `product` (see "Choosing the pool", default `residential`)

Returns traffic used and the remaining traffic of the account the API key belongs to, for one pool. All values are in bytes.

```bash
curl -sS "https://api.gonzoproxy.app/functions/v1/proxy-api/traffic?product=residential" \
  -H "x-api-key: <your_api_key>"
```

Example response:

```json
{
  "traffic_used_day": 125000000,
  "traffic_used_7d": 870000000,
  "traffic_used_month": 3100000000,
  "traffic_used_total": 12400000000,
  "traffic_remaining": 1875000000
}
```

| Field                | Description                       |
| -------------------- | --------------------------------- |
| `traffic_used_day`   | Traffic used over the last day    |
| `traffic_used_7d`    | Traffic used over the last 7 days |
| `traffic_used_month` | Traffic used over the last month  |
| `traffic_used_total` | Traffic used in total             |
| `traffic_remaining`  | Remaining traffic                 |

***

## B. Sub-account management

Base URL:

```
https://api.gonzoproxy.app/functions/v1
```

### B.1 Create a sub-account

Creates a new sub-account linked to your main account.

Once it is created, the system automatically sets up every available product for the sub-account: `residential`, `mobile` and `server_dynamic`.

```http
POST /create-sub-account
```

#### Parameters

Sent in the JSON request body.

| Field              | Type     | Required | Description          |
| ------------------ | -------- | -------- | -------------------- |
| `email`            | `string` | Yes      | Sub-account email    |
| `sub_account_name` | `string` | No       | Sub-account name     |

#### Curl

```bash
curl -sS -X POST "https://api.gonzoproxy.app/functions/v1/create-sub-account" \
  -H "Content-Type: application/json" \
  -H "x-api-key: <your_api_key>" \
  -d '{
    "email": "employee@example.com",
    "sub_account_name": "Employee 1"
  }'
```

#### Response

```json
{
  "success": true,
  "data": {
    "sub_account_name": "Employee 1",
    "email": "employee@example.com",
    "status": "provisioning"
  }
}
```

#### Response fields

| Field              | Type             | Description                                                     |
| ------------------ | ---------------- | --------------------------------------------------------------- |
| `sub_account_name` | `string \| null` | Sub-account name                                                |
| `email`            | `string`         | Sub-account email                                               |
| `status`           | `string`         | Creation status: `provisioning`, `partial`, `ready` or `failed` |

#### Statuses

| Status         | Description                           |
| -------------- | ------------------------------------- |
| `provisioning` | The sub-account is being created      |
| `partial`      | Some of the products are already set up |
| `ready`        | All sub-account products are ready    |
| `failed`       | Creation failed                       |

#### Important

Sub-account creation is asynchronous. A `success: true` response means the request was accepted and the sub-account has started to be created.

Once creation is complete, the sub-account becomes available in these methods:

* `POST /list-sub-accounts`
* `POST /get-sub-account-traffic-stats`
* `POST /sub-account-adjust`

#### Possible errors

| HTTP  | Error                         | Description                                         |
| ----- | ----------------------------- | --------------------------------------------------- |
| `400` | `email_required`              | Email is missing                                    |
| `400` | `email_invalid`               | Email is invalid                                    |
| `400` | `email_too_long`              | Email is too long                                   |
| `400` | `sub_account_name_invalid`    | Sub-account name is invalid                         |
| `400` | `sub_account_name_too_long`   | Sub-account name is too long                        |
| `401` | `missing_x_api_key`           | API key is missing                                  |
| `403` | `invalid_or_inactive_api_key` | API key is invalid or inactive                      |
| `409` | `external_id_exists`          | A sub-account with this email already exists        |
| `409` | `parent_products_incomplete`  | The main account does not have all products enabled |
| `429` | `rate_limited`                | Sub-account creation limit exceeded                 |

#### Error example

```json
{
  "success": false,
  "error": "email_required"
}
```

### B.2 List sub-accounts

Returns the sub-accounts linked to your main account.

```http
POST /list-sub-accounts
```

#### Request

```json
{}
```

#### Curl

```bash
curl -sS -X POST "https://api.gonzoproxy.app/functions/v1/list-sub-accounts" \
  -H "Content-Type: application/json" \
  -H "x-api-key: <your_api_key>" \
  -d '{}'
```

#### Response

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

#### Response fields

| Field               | Type             | Description                       |
| ------------------- | ---------------- | --------------------------------- |
| `proxy_login`       | `string \| null` | Sub-account proxy login           |
| `sub_account_name`  | `string \| null` | Sub-account name                  |
| `is_active`         | `boolean`        | Whether the sub-account is active |
| `traffic_remaining` | `number`         | Remaining traffic in bytes        |
| `traffic_total`     | `number \| null` | Total traffic limit in bytes      |

### B.3 Sub-account traffic statistics

Returns traffic usage statistics for a specific sub-account.

```http
POST /get-sub-account-traffic-stats
```

#### Parameters

| Field         | Type     | Required     | Description                                       |
| ------------- | -------- | ------------ | ------------------------------------------------- |
| `proxy_login` | `string` | Yes          | Sub-account proxy login                           |
| `period`      | `string` | No           | Statistics period. Defaults to `day`              |
| `date`        | `string` | No           | Period date, e.g. `2026-05-19`, `2026-05`, `2026` |
| `start_date`  | `string` | For `custom` | Period start date in `YYYY-MM-DD` format          |
| `end_date`    | `string` | For `custom` | Period end date in `YYYY-MM-DD` format            |
| `group_by`    | `string` | No           | Grouping for `custom`: `day` or `month`           |

Available `period` values: `day`, `week`, `month`, `year`, `custom`

#### Curl: daily statistics

```bash
curl -sS -X POST "https://api.gonzoproxy.app/functions/v1/get-sub-account-traffic-stats" \
  -H "Content-Type: application/json" \
  -H "x-api-key: <your_api_key>" \
  -d '{
    "proxy_login": "GonzoLoginTest",
    "period": "day"
  }'
```

#### Curl: custom period

```bash
curl -sS -X POST "https://api.gonzoproxy.app/functions/v1/get-sub-account-traffic-stats" \
  -H "Content-Type: application/json" \
  -H "x-api-key: <your_api_key>" \
  -d '{
    "proxy_login": "GonzoLoginTest",
    "period": "custom",
    "start_date": "2026-05-01",
    "end_date": "2026-05-19",
    "group_by": "day"
  }'
```

#### Response

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

#### `points[]` fields

| Field               | Type             | Description                                   |
| ------------------- | ---------------- | --------------------------------------------- |
| `time`              | `string`         | Point time in UTC                             |
| `bytes`             | `number`         | Traffic used during the interval              |
| `traffic_remaining` | `number \| null` | Remaining traffic at this point, if available |

### B.4 Adjust sub-account traffic or status

Changes a sub-account's total traffic balance or active status.

```http
POST /sub-account-adjust
```

Supported operations: `set_traffic`, `activate`, `deactivate`

#### B.4.1 Set sub-account traffic

`target_traffic_bytes` is the sub-account's final traffic balance, not the amount to add. When the sub-account's traffic balance is increased, the difference is deducted from the main account's balance of the same pool: residential unless `product` is sent.

If a sub-account currently has `1 GB` and you want it to have `5 GB`, pass `5000000000`.

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
  -H "x-api-key: <your_api_key>" \
  -d '{
    "proxy_login": "GonzoLoginTest",
    "operation": "set_traffic",
    "target_traffic_bytes": 5000000000
  }'
```

#### B.4.2 Activate sub-account

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
  -H "x-api-key: <your_api_key>" \
  -d '{
    "proxy_login": "GonzoLoginTest",
    "operation": "activate"
  }'
```

#### B.4.3 Deactivate sub-account

When deactivated, the sub-account's remaining traffic is returned to the main account's balance of the same pool: residential unless `product` is sent.

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
  -H "x-api-key: <your_api_key>" \
  -d '{
    "proxy_login": "GonzoLoginTest",
    "operation": "deactivate"
  }'
```

#### Response (for all `sub-account-adjust` operations)

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

#### Response fields

| Field                        | Type             | Description                                          |
| ---------------------------- | ---------------- | ---------------------------------------------------- |
| `proxy_login`                | `string \| null` | Sub-account proxy login                              |
| `sub_account_name`           | `string \| null` | Sub-account name                                     |
| `operation`                  | `string`         | Operation performed                                  |
| `target_traffic_bytes`       | `number`         | Sub-account's final traffic                          |
| `previous_sub_traffic_bytes` | `number`         | Sub-account's traffic before the operation           |
| `delta_bytes`                | `number`         | Difference between the old and new value             |
| `parent_traffic_after`       | `number`         | Main account's remaining traffic after the operation |
| `sub_traffic_after`          | `number`         | Sub-account's remaining traffic after the operation  |
| `is_active`                  | `boolean`        | Final sub-account status                             |
| `changed`                    | `boolean`        | Whether an actual change occurred                    |

***

## API response codes

### General codes (section A)

| Code  | Description                  |
| ----- | ---------------------------- |
| `200` | Successful request           |
| `400` | Request parameter error      |
| `401` | Missing or empty `x-api-key` |
| `403` | Invalid or disabled API key  |
| `404` | Invalid request address      |
| `429` | Rate limit exceeded          |
| `500` | Internal service error       |

Error format:

```json
{
  "error": "Error description"
}
```

### Common errors (section B / sub-accounts)

| HTTP  | Error                                                    | Description                                                           |
| ----- | -------------------------------------------------------- | --------------------------------------------------------------------- |
| `400` | `Invalid JSON body`                                      | Malformed JSON                                                        |
| `400` | `proxy_login is required`                                | `proxy_login` not provided                                            |
| `400` | `operation must be set_traffic, activate, or deactivate` | Invalid operation                                                     |
| `400` | `target_traffic_bytes is required`                       | `target_traffic_bytes` not provided for `set_traffic`                 |
| `401` | `Missing x-api-key header`                               | API key not provided                                                  |
| `403` | `Forbidden`                                              | Sub-account does not belong to your account                           |
| `404` | `parent_not_found`                                       | API key not found                                                     |
| `404` | `sub_account_not_found`                                  | Sub-account not found                                                 |
| `409` | `sub_inactive`                                           | Cannot change traffic on a disabled sub-account. Run `activate` first |
| `409` | `insufficient_parent_traffic`                            | Insufficient traffic on the main account                              |

<br>
