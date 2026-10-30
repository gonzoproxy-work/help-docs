# 🔄 IP Rotation

## 🔁 What is IP rotation?

**Rotation** is the frequency at which the IP address on your proxy changes.\
**GonzoProxy** offers three modes, each suited for different tasks. The mode is selected in the **Rotation** field of the generator and is written into the login of the connection string.

***

### 1️⃣ One IP for a set time

🔒 The gateway holds the same exit IP for the whole session instead of changing it on every request. The session length is set in the **Limit Session** field, up to 72 hours.

If the device behind the address goes offline, the system issues a new IP with the same settings and the connection keeps working.

Connection string example:

```
Gonzoj9CiIi_c_US_sd_443_s_663698TEC_ttl_72h:RNW78Fm5@connect.gonzoproxy.app:10000
```

`s_663698TEC` is the session ID, `ttl_72h` the session length.

#### ✅ Ideal for:

* 👥 Working with social media accounts
* 💰 Cryptocurrency-related tasks
* ⚙️ Software usage where a stable session is important

📌 **How long the address actually holds.** We measured this on our own account on 14 September 2026, through `connect.gonzoproxy.app:10000`. Over a horizon of 84 minutes, 51 of 90 sessions kept the same IP, that is 56.7% (Wilson interval 46.4% to 66.4%). Half of the losses happened inside the first 35 minutes.

📌 Plan for that: a session with one IP is a request, not a guarantee. If your job breaks when the address changes, keep a check in it and open a new session when the IP moves. If it is better for your job to stop than to continue from another address, use the Keep IP mode.

***

### 2️⃣ Keep IP: the IP does not change

📍 The IP is held for the whole session, up to 72 hours, and does not change on its own. If the device behind the address goes offline, the connection returns an error and no new IP is issued. To continue, create a new proxy in the generator: it will get a different address.

In the login this mode is marked with the `_iphold_max` suffix. It goes right after the session ID and before `_ttl_`:

```
Gonzoj9CiIi_c_US_sd_443_s_663698TEC_iphold_max_ttl_72h:RNW78Fm5@connect.gonzoproxy.app:10000
```

#### ✅ Ideal for:

* 👥 Social media accounts
* 🛒 Marketplace accounts
* 📢 Ad accounts

📌 Choose it when an IP change in the middle of work triggers checks on the platform, and it is better to stop than to continue from another address. A device can go offline at any moment, long before the session ends: keep a check in your job and create a new proxy when the connection returns an error.

***

### 3️⃣ Randomize IP (New IP for each request)

🔄 The IP address changes **with every connection**.

The login has no session ID and no session length:

```
Gonzoj9CiIi_c_US_sd_443:RNW78Fm5@connect.gonzoproxy.app:10000
```

#### ✅ Perfect for:

* 🤖 Scrapers
* 🧾 Mass account registration
* ⚙️ Automated systems and scripts

📌 If you need to **change the IP as often as possible**, this is your choice.

***

### ⏳ Session length: up to 72 hours

The **Limit Session** field sets the session length for the first two modes, in seconds, minutes or hours. The maximum is 72 hours, that is 4320 minutes or 259,200 seconds. If you enter more, the generator shows "Max 72 hours." and does not create the proxy. The value is an upper bound, not a guarantee.

***

### ❓ Why isn’t the IP static and may change on its own?

All **GonzoProxy residential proxies** work through real IP addresses from live users.\
📱 When a device disconnects or goes offline, what happens next depends on the mode. With one IP for a set time, the system automatically assigns you a **new IP** to keep the connection active. In the Keep IP mode, the connection returns an error and no new IP is issued.

This is **normal behaviour for a residential pool**: the address belongs to a real device, and it is the device, not the gateway, that decides when it goes offline.

***

### 👾 Try it here: [GonzoProxy.com](https://gonzoproxy.com)

***

### 📱 Stay Connected

* [Telegram Channel](https://t.me/GonzoProxy)
* [Telegram Chat ](https://t.me/GonzoProxy_Chat)
* [Instagram](https://www.instagram.com/gonzoproxy)
* [24/7 Support](https://t.me/GonzoProxy_bot)

💬 Our team is always here for you! Reach out anytime.
