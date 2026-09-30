# 👾 Setup Indigo X

With the upgrade from Indigo 6 to the new Indigo X, the anti-detect browser has received a major overhaul: it is more flexible, has more features and is aimed at professional use. Indigo X creates separate browser profiles and lets you run many accounts from one application.

The proxy for a profile is taken from the GonzoProxy dashboard: a residential proxy, pasted into the Proxy field of the profile.

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

In this mode the browser presents itself as an Android device.

***

### ⚙️ 3. Android profile settings

Some settings are locked for stability and can't be changed. Here's what’s preset and what’s recommended:

**🔒 Default fixed settings**

| Setting                 | Default Value | Notes                 |
| ----------------------- | ------------- | --------------------- |
| Font Data               | Mask          | Needed for stability  |
| WebGL + WebGPU Metadata | Mask          | Cannot be set to Real |
| Media Devices           | Mask          | For performance       |
| Navigator               | Mask          | System requirement    |
| Screen Resolution       | Mask          | Must be configured    |

**📈 Recommended values**

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
| **Mimic X**      | Based on Chromium. |
| **Stealthfox X** | Based on Firefox.  |

***

### 🧠 Using Indigo X Agent

Indigo X Agent is a helper app that runs in the background and handles launching browser profiles.

ℹ️ Without the agent, you can create, edit, and move profiles but not launch them.

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
connect.gonzoproxy.app:10000:Gonzoj9CiIi_c_US_sd_596_city_Denver_s_30410TGX_ttl_72h:RNW78Fm5
```

Make sure the format is: `ip:port:username:password`



<figure><img src=".gitbook/assets/1 (14).png" alt=""><figcaption></figcaption></figure>



2. In Indigo X, click “Create Profile” and enter:

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

***

### 📆 Final thoughts

In Indigo X the GonzoProxy connection string goes into the Proxy field of a profile, in the `ip:port:username:password` format, with the protocol set to SOCKS5 or HTTPS.

***

### 👾 Try it here: [GonzoProxy.com](https://gonzoproxy.com)

***

### 📱 Stay Connected

* [Telegram Channel](https://t.me/GonzoProxy)
* [Telegram Chat ](https://t.me/GonzoProxy_Chat)
* [Instagram](https://www.instagram.com/gonzoproxy)
* [24/7 Support](https://t.me/GonzoProxy_bot)

💬 Our team is always here for you! Reach out anytime.
