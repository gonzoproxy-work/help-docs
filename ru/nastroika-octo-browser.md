# 🦑 Настройка Octo Browser

[**Octo Browser**](https://octobrowser.net/ru/) это антидетект-браузер, который держит каждый аккаунт в отдельном профиле, а прокси задаёт профилю отдельный IP-адрес.

В этой инструкции показано, как добавить резидентские прокси [**GonzoProxy**](https://gonzoproxy.com/?utm_source=gitbook\&utm_medium=octobrowser\&utm_content=ru) в профили Octo Browser.

***

## 📌 Основные особенности Octo Browser

### 1️⃣ Имитация ручного ввода текста

Функция **«Paste as Human Typing»** в Octo Browser вставляет текст посимвольно, имитируя набор на клавиатуре.

#### Как это сделать

* Скопируйте необходимый текст в буфер обмена.
* В браузере **Octo** нажмите правой кнопкой мыши в поле ввода текста и выберите **«Type text from clipboard»**.
* Или используйте горячие клавиши: **CTRL + SHIFT + E**.
* Octo вводит текст с переменной скоростью.



<figure><img src=".gitbook/assets/type_as_human.gif" alt=""><figcaption></figcaption></figure>



***

### 2️⃣ Установка расширений

Расширения это дополнительные программы, которые расширяют стандартные возможности браузера. В Octo вы можете устанавливать любые расширения из обычного магазина Chrome.



{% embed url="https://youtu.be/m1vCANPNVTo?si=nDNdZghqzqEpST-0" %}



***

### 3️⃣ Корзина

Если вы случайно удалили профиль, в Octo Browser есть корзина: там профили хранятся до **48 часов** и их можно восстановить.

> ⚠️ Важно! Через 48 часов профили удаляются окончательно и восстановлению уже не подлежат.



{% embed url="https://youtu.be/xlvVwfMWHHo?si=2ybgk9PhCrg5A32Y" %}



***

### 4️⃣ Куки робот

**Куки робот Octo Browser** автоматически переходит по указанным вами ссылкам и собирает куки и пиксели в профиль.

#### Особенности работы Куки робота

* Чем больше ссылок вы загрузите, тем дольше робот будет их обрабатывать.
* После завершения работы робота все полученные куки сохраняются в профиле.
* Посмотреть собранные куки можно по ссылке: `chrome://settings/content/all`.



{% embed url="https://youtu.be/OPEHaS7i8C0?si=FcUv_YtF9uKG0Nkb" %}



***

### 5️⃣ Подмена видеопотока

Эта функция **Octo Browser** подменяет видео с веб-камеры заранее подготовленным видеороликом. Функция доступна в **Windows**.

#### Требования к видеофайлу

* **Форматы:** `.mp4` или `.mov`
* **Кодек:** `h264`
* **Максимальный размер:** до **50 Мб**



{% embed url="https://youtu.be/pL08HZ30URA?si=s_bDgkoBhBEGVxvi" %}



***

### 6️⃣ Командная работа

В **Octo Browser** есть набор функций для командной работы:

* ✅ Обмен профилями, куками и прокси.
* ✅ Настройка ролей и доступов к профилям.
* ✅ История действий каждого участника.
* ✅ Создание задач, назначение исполнителей и сроков.



{% embed url="https://youtu.be/Ie2hXKKQ9Co?si=vzGDSDa7-uXZfn71" %}



***

### 7️⃣ Шаблоны профилей

**Шаблоны** это возможность заранее настроить параметры профиля, чтобы быстрее создавать новые профили:

* Прокси, расширения, теги, иконки профиля и стартовые страницы задаются заранее.
* Вы можете изменять все параметры профиля, кроме выбранной операционной системы.
* Шаблоны доступны для всех подписок и могут быть защищены паролем.



{% embed url="https://youtu.be/EUCocm86kkM?si=aF6JRXvHIMFE0sla" %}



***

## 🛠️ Создание 20 профилей с резидентскими прокси от GonzoProxy

### 📍 Шаг 1: Подготовка прокси в [GonzoProxy](https://gonzoproxy.com/?utm_source=gitbook\&utm_medium=octobrowser\&utm_content=ru)

* Создайте **20 резидентских прокси** (например, США).



<figure><img src=".gitbook/assets/резиденсткие.png" alt=""><figcaption></figcaption></figure>



* Формат прокси будет таким:

```
Gonzoj9CiIi_c_US_s_204976RWZ_ttl_72h:RNW78Fm5@connect.gonzoproxy.app:10000
```

* Добавляем перед прокси `socks5://` или `https://`

```
socks5://Gonzoj9CiIi_c_US_s_204976RWZ_ttl_72h:RNW78Fm5@connect.gonzoproxy.app:10000
```

* Вставьте полученные прокси в **Octo Browser**&#x20;



<figure><img src=".gitbook/assets/прокси (1).png" alt=""><figcaption></figcaption></figure>

***

### 📍 Шаг 2: Создание и настройка шаблона профиля

* Задайте название профиля и выберите удобную иконку.
* Отметьте **20 прокси** из первого шага.
* Добавьте теги, стартовые страницы и закладки.
* Включите опции шума: **WebGL**, **Canvas**, **Audio**, **Client Rects**.
* Оставьте язык, часовой пояс и геолокацию как **«Зависит от IP»**.
* Установите нужные расширения.



<figure><img src=".gitbook/assets/шаблон.png" alt=""><figcaption></figcaption></figure>



***

### 📍 Шаг 3: Массовое создание профилей

* Перейдите в режим **массового создания профилей**.



<figure><img src=".gitbook/assets/профили.png" alt=""><figcaption></figcaption></figure>



* Укажите количество: **20,** нажмите **«Добавить»** и сохраните.



<figure><img src=".gitbook/assets/профили 2.png" alt=""><figcaption></figcaption></figure>



🎉 **Готово!** Созданы 20 профилей, у каждого свой прокси.



<figure><img src=".gitbook/assets/профили 3.png" alt=""><figcaption></figcaption></figure>



***

### 👾 Попробовать можно здесь: [GonzoProxy.com](https://gonzoproxy.com/?utm_source=gitbook\&utm_medium=octobrowser\&utm_content=ru)

***

### 📱 Мы на связи

* [Telegram-канал ](https://t.me/GonzoProxy)
* [Telegram-чат ](https://t.me/GonzoProxy_Chat)
* [Instagram](https://www.instagram.com/gonzoproxy)
* [Поддержка 24/7 ](https://t.me/GonzoProxy_bot)

💬 Наша команда всегда на связи! Обращайтесь в любое время суток.
