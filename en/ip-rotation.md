# 🔄 IP Rotation

## 🔁 What is IP rotation?

**Rotation** is the frequency at which the IP address on your proxy changes.\
**GonzoProxy** offers two types of rotation, each suited for different tasks.

***

### 1️⃣ Sticky IP (Sticky Session)

🔒 A sticky session asks the gateway to hold the same exit IP for the whole session instead of changing it on every request. The session length is set in the **Limit Session** field, up to 7 days.

#### ✅ Ideal for:

* 👥 Working with social media accounts
* 💰 Cryptocurrency-related tasks
* ⚙️ Software usage where a stable session is important

📌 **How long the address actually holds.** We measured this on our own account on 14 September 2026, through `connect.gonzoproxy.app:10000`. Over a horizon of 84 minutes, 51 of 90 sessions kept the same IP, that is 56.7% (Wilson interval 46.4% to 66.4%). Half of the losses happened inside the first 35 minutes.

📌 Plan for that: a sticky session is a request, not a guarantee. If your job breaks when the address changes, keep a check in it and open a new session when the IP moves.

***

### 2️⃣ Randomize IP (New IP for each request)

🔄 The IP address changes **with every connection**.

#### ✅ Perfect for:

* 🤖 Scrapers
* 🧾 Mass account registration
* ⚙️ Automated systems and scripts

📌 If you need to **change the IP as often as possible**, this is your choice.

***

### ❓ Why isn’t the IP static and may change on its own?

All **GonzoProxy residential proxies** work through real IP addresses from live users.\
📱 When a device disconnects or goes offline, the system automatically\
assigns you a **new IP** to keep the connection active.

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
