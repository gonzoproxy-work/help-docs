# 🐬 Setup Dolphin{anty}

Dolphin{anty} is an anti-detect browser that keeps each account in its own profile, and a proxy is what gives every profile a separate IP address. This page shows where to paste a GonzoProxy connection string.

***

### 🔧 Profile settings in Dolphin{anty}

The settings below are the ones that have to agree with the proxy you connect.

#### 1. WebRTC



<figure><img src=".gitbook/assets/1 (6).png" alt=""><figcaption></figcaption></figure>



* **Altered**: the option to use with a proxy.
* **Manual**: only if you set the address yourself and know what you are doing.
* **Off / Real**: do not use them when you work through a proxy.

#### 2. Canvas



<figure><img src=".gitbook/assets/2 (5).png" alt=""><figcaption></figcaption></figure>



* **Noise**: for mass account creation, CPA, push, TikTok automation.
* **Real**: for manual work, farming, or long-term accounts.

#### 3. WebGL + WebGL Info



<figure><img src=".gitbook/assets/3 (4).png" alt=""><figcaption></figcaption></figure>



* **WebGL:** choose **Noise**.
* **WebGL Info:** set to **Real**, matching your GPU data. Choose **Manual** only if you are confident about your hardware setup.

#### 4. ClientRects



<figure><img src=".gitbook/assets/4 (3).png" alt=""><figcaption></figcaption></figure>



* **Real**: if you work alone and never hand the profile over.
* **Noise**: if the profile is used on several machines or by several people (for example Windows → Mac).

#### 5. Language, Timezone, and Geo



<figure><img src=".gitbook/assets/5 (3).png" alt=""><figcaption></figcaption></figure>



* Set to **Auto** when using GonzoProxy, so that timezone, language and location follow the proxy address.
* With a sticky IP you can also fix the location by hand.

#### 6. Navigator (CPU, RAM, Fonts)



<figure><img src=".gitbook/assets/6 (1).png" alt=""><figcaption></figcaption></figure>



* Leave this default unless you know exactly what you are doing.

***

### 🔌 Connecting proxies in Dolphin{anty}

* Go to **Proxies** (left sidebar).
* Click **Import proxies**.
* Paste proxies in the format:

```
login:password@host:port
```

Example with GonzoProxy:

```
Gonzoj9CiIi_c_US_sd_443_s_663698TEC_ttl_72h:RNW78Fm5@connect.gonzoproxy.app:10000
```

Put one proxy per line.

* Click **Check**. A ✅ means the proxy answered.

#### 🔹 Where to insert proxies into your profile?

* When creating or editing your profile, open the **Proxy** tab.
* Choose the type: **SOCKS5** or **HTTP(S)**.
* Paste the full proxy string without breaking it up:

```
login:password@host:port
```

***

### 🧭 Sticky or Randomize IP?



<figure><img src=".gitbook/assets/7 (3).png" alt=""><figcaption></figcaption></figure>



GonzoProxy provides two types of IP rotation. Choose according to your task.

***

#### 🔒 Sticky IP (fixed session)

The session hold time is set in the dashboard, up to 7 days. In our own measurement on 14 September 2026, 51 of 90 sessions kept the same address over an 84-minute horizon, that is 56.7% (confidence interval 46.4% to 66.4%), and half of the losses happened inside the first 35 minutes. We have not measured retention beyond that horizon and do not promise it.

Use it for:

* Facebook, TikTok, Google Ads (farming, warming, regular usage)
* Crypto exchanges, wallets
* Manual tasks, long-term projects

***

#### 🔄 Randomize IP (new IP every request)

The address changes on every connection or request.

Use it for:

* Mass account creation
* Parsing or automated software
* Aggressive CPA marketing
* Short-lived profiles

***

### ✅ Final Check

* ✅ Proxies uploaded
* ✅ Connection tested
* ✅ Profiles configured

***

### 👾 Try it here: [GonzoProxy.com](https://gonzoproxy.com)

***

### 📱 Stay Connected

* [Telegram Channel](https://t.me/GonzoProxy)
* [Telegram Chat ](https://t.me/GonzoProxy_Chat)
* [Instagram](https://www.instagram.com/gonzoproxy)
* [24/7 Support](https://t.me/GonzoProxy_bot)

💬 Our team is always here for you! Reach out anytime.
