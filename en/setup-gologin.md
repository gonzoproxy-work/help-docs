# 🥸 Setup GoLogin

GoLogin is an anti-detect browser that keeps each account in its own profile, and a proxy is what gives every profile a separate IP address. This page shows where to paste a GonzoProxy connection string.

***

### 🔧 Setting Up GoLogin with GonzoProxy

#### 1. Choose Your Proxy Type

**Mobile IPs (3G/4G):**

* Account registration
* Mobile apps and behavior emulation

**Residential IPs:**

* SEO promotion
* Ads (Google Ads, Facebook)
* Quick checkouts (sneakers, PS5, etc.)
* Software testing

***

#### 2. IP Rotation (for residential proxies)

* **Sticky IP.** The session hold time is set in the dashboard. In our own measurement on 14 September 2026, 51 of 90 sessions kept the same address over an 84-minute horizon, that is 56.7% (confidence interval 46.4% to 66.4%), and half of the losses happened inside the first 35 minutes. We have not measured retention beyond that horizon and do not promise it. Used for social media, crypto and warm-up sessions.
* **Random IP.** A new address for every request. Used for scraping, parsing and automation.

***

### 📦 How to Add Proxies in GoLogin

Let’s say you bought US residential proxies from GonzoProxy and received this string:

`Gonzoj9CiIi_c_US_sd_443_s_663698TEC_ttl_72h:RNW78Fm5@connect.gonzoproxy.app:10000`



<figure><img src=".gitbook/assets/7 (2).png" alt=""><figcaption></figcaption></figure>



Here's what you use:

* Protocols: HTTPS / SOCKS5
* Host: `connect.gonzoproxy.app`
* Port: `10000`
* Login: `Gonzoj9CiIi_c_US_sd_443_s_663698TEC_ttl_72h`
* Password: `RNW78Fm5`

Paste this data into your anti-detect browser.



<figure><img src=".gitbook/assets/0 (2).png" alt=""><figcaption></figcaption></figure>



Click **Check Proxy**.



<figure><img src=".gitbook/assets/00 (1).png" alt=""><figcaption></figcaption></figure>



✅ Proxy passed: United States • US • Fresno

***

### 🧠 Fine-Tune Your GoLogin Profile

#### 🌍 WebRTC



<figure><img src=".gitbook/assets/1 (5).png" alt=""><figcaption></figcaption></figure>



* Enable it and spoof it to the proxy IP
* Do not switch it off completely

***

#### ⏰ Timezone



<figure><img src=".gitbook/assets/2 (4).png" alt=""><figcaption></figcaption></figure>



* Enable auto-detection by IP

***

#### 📍 Geolocation



<figure><img src=".gitbook/assets/3 (3).png" alt=""><figcaption></figcaption></figure>



* Allow when a site requests it

***

#### 📋 "Other Settings" in GoLogin

| Setting                                             | Recommended Value                                                          |
| --------------------------------------------------- | -------------------------------------------------------------------------- |
| **User-Agent**                                      | Match proxy (Android UA for mobile, Windows/macOS for residential)         |
| **Screen Resolution**                               | 360×740 (mobile) / 1920×1080 (desktop)                                     |
| **Languages**                                       | Based on IP (e.g. `fr-FR, en-US`)                                          |
| **Platform**                                        | `Android`, `Win32`, `MacIntel`                                             |
| **CPU Threads**                                     | <p>Mobile: 4-8</p><p>Desktop: 8-16</p>                                     |
| **RAM**                                             | <p>Mobile: 3-6 GB</p><p>Desktop: 8-16 GB</p>                               |
| **Fonts**                                           | <p>Enable font spoofing</p><p>Roboto (mobile) / Segoe UI (desktop)</p>     |
| **Media Device Masking**                            | Enable                                                                     |
| **Canvas**                                          | Enable noise                                                               |
| **ClientRects**                                     | Enable noise                                                               |
| **AudioContext**                                    | Enable noise                                                               |
| **WebGL Image**                                     | Enable noise                                                               |
| **WebGL Vendor**                                    | `Qualcomm` (mobile) / `Intel`, `NVIDIA` (desktop)                          |
| **WebGL Renderer**                                  | `Adreno 650`, `Mali-G78`, `Intel UHD`, `GT 1030`, etc.                     |
| **Local Storage**                                   | Enable                                                                     |
| **Extension Storage**                               | Enable                                                                     |
| **Vulnerable Browser Plugins**                      | Disable                                                                    |
| **Block Active Sessions**                           | Enable                                                                     |
| **Enable Google Services**                          | Enable                                                                     |
| **Save Bookmarks / History / Passwords / Sessions** | All enabled                                                                |
| **System Extensions**                               | Disable                                                                    |

***

#### 🔌 Extensions



<figure><img src=".gitbook/assets/4 (2).png" alt=""><figcaption></figcaption></figure>



Install extensions in advance if your workflow requires them.

***

### 👾 Try it here: [GonzoProxy.com](https://gonzoproxy.com)

***

### 📱 Stay Connected

* [Telegram Channel](https://t.me/GonzoProxy)
* [Telegram Chat ](https://t.me/GonzoProxy_Chat)
* [Instagram](https://www.instagram.com/gonzoproxy)
* [24/7 Support](https://t.me/GonzoProxy_bot)

💬 Our team is always here for you! Reach out anytime.
