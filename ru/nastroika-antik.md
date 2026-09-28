# 🛡️ Настройка Antik

[Antik Browser](https://antik-browser.com/ru) — это мощный антидетект браузер, предназначенный для комфортной и безопасной работы с множеством аккаунтов в Google Ads, социальных сетях, онлайн-маркетплейсах, гемблинг-площадках и криптобиржах. Благодаря использованию отпечатков реальных устройств и продвинутой системе подмены данных, аккаунты остаются «живыми» намного дольше, чем при использовании других антидетект-решений.

В этом обзоре мы подробно расскажем о ключевых особенностях Antik Browser, на примере покажем, как создать 10 браузерных профилей с использованием резидентских прокси от [**GonzoProxy**](https://gonzoproxy.com/?utm_source=gitbook\&utm_medium=ru\&utm_content=antik), а также объясним, почему именно качественные прокси так важны для безопасности ваших аккаунтов.

***

## 🌟 Основные преимущества Antik Browser

### 1️⃣ Командная работа без ограничений

Antik Browser идеально подходит для команд, работающих над множеством проектов одновременно. Вот почему:

* **Неограниченное количество участников и команд**.
* **Четкое разграничение прав доступа** к профилям и данным.
* **Совместное использование профилей** (прокси, отпечатки, заметки и теги) между членами команды.
* **Автоматизация рутинных задач** (вход в аккаунты, веб-скрапинг и пр.), что значительно ускоряет работу.



<figure><img src=".gitbook/assets/team.png" alt=""><figcaption></figcaption></figure>



Эти функции особенно полезны маркетологам, арбитражникам и SMM-специалистам, стремящимся оптимизировать рабочий процесс.

***

### 2️⃣ Удобная работа с расширения

В Antik Browser встроена удобная система управления расширениями для Chrome, которые разбиты на группы для быстрого поиска и установки.



<figure><img src=".gitbook/assets/расширения.png" alt=""><figcaption></figcaption></figure>



***

### 3️⃣ Восстановление удаленных профилей

Если вы случайно удалили профиль, не переживайте! Вкладка «Корзина» позволит легко восстановить любой удаленный профиль или же полностью очистить ненужные данные.



<figure><img src=".gitbook/assets/trash.png" alt=""><figcaption></figcaption></figure>



***

### 🚀 Создаем профили с прокси от GonzoProxy

Чтобы аккаунты не банили, важно использовать прокси от реальных устройств — **резидентские или мобильные**, а не дата-центровые. Идеально подходят прокси от [**GonzoProxy**](https://gonzoproxy.com/?utm_source=gitbook\&utm_medium=ru\&utm_content=antik), которые обеспечивают максимальную надежность и безопасность.

#### 🔧 Общие настройки профилей в Antik Browser:

* **Имя профиля**
* **Папка**
* **Операционная система**: Windows или MacOS
* **Лейбл** (определяет расширения и закладки):
  * Default, Facebook, Google, Tik-Tok, Crypto, SMM-Marketing, Matched Betting





<figure><img src=".gitbook/assets/1.png" alt=""><figcaption></figcaption></figure>



Переходим в [**GonzoProxy**](https://gonzoproxy.com/?utm_source=gitbook\&utm_medium=ru\&utm_content=antik) и создаем прокси, для примера возьмем **USA**



<figure><img src=".gitbook/assets/0.png" alt=""><figcaption></figcaption></figure>



* **Прокси** (поддерживаемые форматы в Antik Browser):
  1. `192.168.0.1:8000`
  2. `socks5://login:password@192.168.0.1:8000`
  3. `192.168.0.1:8000:login:password`
  4. `login:password|192.168.0.22:8000`

Вставляем полученные прокси в профиль



<figure><img src=".gitbook/assets/2.png" alt=""><figcaption></figcaption></figure>



Дополнительно вы можете задать стартовую страницу, указать заметку и загрузить Cookie.

#### ⚙️ Расширенные настройки (рекомендуем включить):

| Параметр          | Значение / Режим                                                        |
| ----------------- | ----------------------------------------------------------------------- |
| **User Agent**    |  Без изменений, либо вставляем свой                                     |
| **Memory**        |  Выставляем от 4 до 8 GB                                                |
| **CPU**           |  Выставляем от 2 до 16 ядер                                             |
| **WebGL**         |  Включить шум                                                           |
| **Client Rects**  |  Включить шум                                                           |
| **Web GPU**       |  Включить                                                               |
| **Canvas**        |  Подмена                                                                |
| **Battery**       |  Подмена                                                                |
| **WebGL Info**    |  Вручную                                                                |
| **WebRTC**        |  Подмена                                                                |
| **Media Devices** | <p>Вручную: <br>VideoInput - 1<br>AudioInput - 1<br>AudioOutput - 1</p> |
| **Часовой пояс**  |  Подмена                                                                |
| **Геолокация**    |  Подмена                                                                |

***

### 📌 Создаем сразу 10 профилей с прокси от GonzoProxy

#### ✅ Шаг 1: настройка параметров

* Выбираем количество профилей (10)
* Задаем имена и папку для удобного управления
* User Agent, CPU, Memory — выбираем случайные настройки
* Лейбл для подгрузки нужных расширений: Default, Facebook, Google, Tik-Tok, Crypto, SMM-Marketing, Matched Betting
* Включаем все расширенные настройки защиты (Canvas, WebGL, WebRTC и т.д.)

#### ✅ Шаг 2: берем прокси от [GonzoProxy](https://gonzoproxy.com/?utm_source=gitbook\&utm_medium=ru\&utm_content=antik)

На GonzoProxy выбираем получение прокси в формате:

```
login:password@ip:port
```



<figure><img src=".gitbook/assets/прокси.png" alt=""><figcaption></figcaption></figure>



Например:

```
Gonzoj9CiIi_c_US_s_573228HPF_ttl_72h:RNW78Fm5@pool.gonzoproxy.com:1000
Gonzoj9CiIi_c_US_s_882282HPF_ttl_72h:RNW78Fm5@pool.gonzoproxy.com:1000
Gonzoj9CiIi_c_US_s_140456HPF_ttl_72h:RNW78Fm5@pool.gonzoproxy.com:1000
```

Вставляем массово в Antik Browser в таком виде:

```
socks5://Gonzoj9CiIi_c_US_s_573228HPF_ttl_72h:RNW78Fm5@pool.gonzoproxy.com:1000
socks5://Gonzoj9CiIi_c_US_s_882282HPF_ttl_72h:RNW78Fm5@pool.gonzoproxy.com:1000
socks5://Gonzoj9CiIi_c_US_s_140456HPF_ttl_72h:RNW78Fm5@pool.gonzoproxy.com:1000
```



<figure><img src=".gitbook/assets/прокси2 (1).png" alt=""><figcaption></figcaption></figure>



После этого жмем **«создать»** и проверяем работоспособность всех прокси.



<figure><img src=".gitbook/assets/прокси 3 (1).png" alt=""><figcaption></figcaption></figure>



✅ **Проверка успешна — все прокси работают идеально!**

***

### 🔥 Прогрев куки: почему это важно?

Прогрев куки необходим, чтобы ваш профиль выглядел максимально естественным в глазах систем. Это уменьшает риск банов и улучшает доверие платформ к вашим аккаунтам.

В Antik Browser есть полезная функция — **куки-бот**. Просто зайдите в настройки профиля, включите куки-бот и добавьте сайты, на которых бот будет прогревать профиль.



<figure><img src=".gitbook/assets/куки.png" alt=""><figcaption></figcaption></figure>



📍 Вот 10 сайтов для США:

```
google.com
youtube.com
amazon.com
reddit.com
twitter.com
facebook.com
cnn.com
espn.com
walmart.com
nytimes.com
```



<figure><img src=".gitbook/assets/куки2.png" alt=""><figcaption></figcaption></figure>

➡️ Жмем Start Cookie Robot



<figure><img src=".gitbook/assets/куки 3.png" alt=""><figcaption></figcaption></figure>

Отлично, мы прогрели профиль, поступаем идентично с остальными.

***

### 🎯 Итоги:&#x20;

Используя Antik Browser вместе с качественными прокси от GonzoProxy, вы получаете комплексное и надежное решение для работы с множеством аккаунтов без риска блокировок.

✅ [**Antik Browser**](https://antik-browser.com/ru) даёт вам продвинутую анонимность и простоту управления.\
✅ [**GonzoProxy**](https://gonzoproxy.com/?utm_source=gitbook\&utm_medium=ru\&utm_content=antik) обеспечивает надежные, реальные прокси, которые максимально защищают аккаунты от подозрений и банов.

Выбирая эту связку, вы инвестируете в безопасность, эффективность и стабильность своего бизнеса! 🚀

***

### 👾 Попробовать можно здесь: [GonzoProxy.com](https://gonzoproxy.com/?utm_source=gitbook\&utm_medium=ru\&utm_content=antik)

***

### 📱 Мы на связи

* [Telegram-канал ](https://t.me/GonzoProxy)
* [Telegram-чат ](https://t.me/GonzoProxy_Chat)
* [Instagram](https://www.instagram.com/gonzoproxy)
* [Поддержка 24/7 ](https://t.me/GonzoProxy_bot)

💬 Наша команда всегда на связи! Обращайтесь в любое время суток — решим любой вопрос в течение нескольких минут.

