# 👾 Setup Indigo X

With the upgrade from Indigo 6 to the new Indigo X, the anti-detect browser has received a major overhaul—making it more flexible, feature-rich, and ready for professional use. Indigo X helps you create unique browser profiles, bypass anti-fraud systems, and work with dozens or even hundreds of accounts without risking bans.

Indigo X works especially well when paired with GonzoProxy residential proxies, delivering top-level anonymity, a realistic digital fingerprint, and stable access to the sites you need.

***

## 📊 Indigo X features

### ♻️ 1. Profile storage types



In Indigo X, you can choose between **cloud** and **local** profile storage. This affects speed, sync, and teamwork capabilities.

| Feature      | 🌐 Cloud Profiles                                        | 💻 Local Profiles                                   |
| ------------ | -------------------------------------------------------- | --------------------------------------------------- |
| How it works | Load once, then run from cache. Sync needed for changes. | Downloaded on first launch, works locally.          |
| Data Storage | All data in AWS cloud                                    | Cookies & extensions locally, metadata in AWS cloud |
| Benefits     | Sync between devices, team-friendly                      | Instant launch anytime                              |

You can use a selector in the profile list to filter by storage type.

***

### 📱 2. Support for mobile Android profiles

Indigo X supports mobile profiles to mimic smartphone behavior. This is great for:

* Testing mobile UIs
* Working with device-sensitive apps and websites
* Stronger fingerprint masking and "natural" behavior

The browser pretends to be an Android device, masking its behavior like a real mobile user.

***

### ⚙️ 3. Android profile settings

Some settings are locked for stability and can't be changed. Here's what’s preset and what’s recommended for max masking:

**🔒 Default fixed settings**

| Setting                 | Default Value | Notes                 |
| ----------------------- | ------------- | --------------------- |
| Font Data               | Mask          | Needed for stability  |
| WebGL + WebGPU Metadata | Mask          | Cannot be set to Real |
| Media Devices           | Mask          | For performance       |
| Navigator               | Mask          | System requirement    |
| Screen Resolution       | Mask          | Must be configured    |

**📈 Recommended for Best Masking**

| Setting                 | Recommended Value |
| ----------------------- | ----------------- |
| Screen Resolution       | Mask              |
| Media Devices           | Mask              |
| WebGL + WebGPU Metadata | Mask              |
| WebGL Graphics          | Noise             |
| Canvas Graphics         | Real              |
| AudioContext            | Noise             |
| Font Data               | Mask              |

***

### 📅 4. Role & Access system

Indigo X is great for teams, thanks to a flexible role system. Each role has specific access levels:

The main role is the **Owner** of the account, with full access. Additionally, you can assign:

* **Manager**
* **User**
* **Operator**

| Feature            | 👨‍🏢 Manager     | 👤 User           | 🙇 Operator   |
| ------------------ | ----------------- | ----------------- | ------------- |
| Group Access       | All groups        | Assigned only     | Assigned only |
| Profile Management | Create, run, edit | Create, run, edit | Run only      |
| Group Management   | Yes               | No                | No            |
| Notes              | Yes               | Yes               | No            |
| Trash Bin          | Yes               | Yes               | No            |
| Member Management  | Yes               | No                | No            |

***

### 🔧 5. Indigo X browsers

Indigo X has two browser engines to choose from, depending on your tasks:

| Browser          | ✨ Features                                                                |
| ---------------- | ------------------------------------------------------------------------- |
| **Mimic X**      | Based on Chromium. Imitates real-user behavior. Versatile.                |
| **Stealthfox X** | Based on Firefox. Stronger detection resistance. Ideal for sensitive ops. |

***

### 🧠 Using Indigo X Agent

Indigo X Agent is a helper app that runs in the background and handles launching browser profiles.

ℹ️ Without the agent, you can create, edit, and move profiles—but not launch them.

#### 🔌 Connecting the Agent

1. **Download the agent** for your OS:
   * Windows
   * macOS:
     * M-series (M1, M2, M3 chips)
     * Intel (classic models)
   * Linux
2. **Install it**:
   * **Windows**: Right-click the file and choose “Run as administrator”
   * **macOS/Linux**: Follow your OS’s standard install procedure
3. In Indigo X, click **“Connect Agent”**
4. Wait for the components to load and sync. The agent will handle the rest.



<figure><img src=".gitbook/assets/2 (12).png" alt=""><figcaption></figcaption></figure>



***

### 🌐 Using GonzoProxy residential proxies with Indigo X



1. Say you bought US residential proxies from GonzoProxy and received this line:

```
pool.gonzoproxy.com:1000:Gonzoj9CiIi_c_US_sd_596_city_Denver_s_30410TGX_ttl_72h:RNW78Fm5
```

Make sure the format is: `ip:port:username:password`



<figure><img src=".gitbook/assets/1 (14).png" alt=""><figcaption></figcaption></figure>



#### 2. In Indigo X, click “Create Profile” and enter:

| Field                   | Recommended Value                 |
| ----------------------- | --------------------------------- |
| Profile Name            | Any friendly name                 |
| Proxy                   | Paste the GonzoProxy string       |
| Protocol                | SOCKS5 or HTTPS                   |
| OS                      | MacOS / Windows / Linux / Android |
| Browser                 | Mimic X or Stealthfox X           |
| Storage                 | Cloud or Local                    |
| Timezone                | Mask                              |
| Browser Language        | Mask                              |
| Start Page              | `https://whoerip.com/indigo/`     |
| WebRTC                  | Mask                              |
| Geolocation             | Ask / Mask                        |
| Screen Resolution       | Mask                              |
| Media Devices           | Mask                              |
| WebGL + WebGPU Metadata | Mask                              |
| WebGL Graphics          | Noise                             |
| Canvas Graphics         | Noise                             |
| AudioContext            | Noise                             |
| Navigator               | Mask                              |
| Port Scanning           | Mask                              |
| Font Data               | Mask                              |

#### After setup, you get:

* A **unique**, realistic browser profile
* **Stable access** to your target sites
* **Complete fingerprint masking** and real geo-IP
* **Strong protection** against anti-fraud systems

***

### 📆 Final thoughts

**Indigo X + GonzoProxy = 🔒 a powerful anti-detect solution** for secure, stable, and flexible online work.

Whether you’re into arbitrage, automation, marketing, or multi-accounting — this combo gives you:

* **Effective fingerprint masking**
* **Customizable profiles for any job**
* **An uncompromising IP solution**

**Start working safely today with Indigo X and GonzoProxy!**

***

### 👾 Try it here: [GonzoProxy.com](https://gonzoproxy.com)

***

### 📱 Stay Connected

* [Telegram Channel](https://t.me/GonzoProxy)
* [Telegram Chat ](https://t.me/GonzoProxy_Chat)
* [Instagram](https://www.instagram.com/gonzoproxy)
* [24/7 Support](https://t.me/GonzoProxy_bot)

💬 Our team is always here for you! Reach out anytime — we’ll solve any issue within minutes.
