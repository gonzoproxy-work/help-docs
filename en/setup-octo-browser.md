# 🦑 Setup Octo Browser

[**Octo Browser**](https://octobrowser.net/) is an anti-detect browser that keeps each account in its own profile, and a proxy is what gives every profile a separate IP address.

This guide shows how to put [**GonzoProxy**](/introduction.md) residential proxies into Octo Browser profiles.

***

## 📌 Key features of Octo Browser

### 1️⃣ Human-like typing simulation

The **"Paste as Human Typing"** feature pastes text character by character, simulating typing on a keyboard.

#### How to use it

* Copy the text you need to your clipboard.
* In Octo Browser, right-click in a text input field and select **"Type text from clipboard."**
* Or use the hotkey: **CTRL + SHIFT + E**.
* Octo then types the text out at a variable speed.



<figure><img src=".gitbook/assets/type_as_human2.gif" alt=""><figcaption></figcaption></figure>



***

### 2️⃣ Installing extensions

Extensions are add-ons that expand the browser’s capabilities. You can install any Chrome extension in Octo Browser from the regular Chrome Web Store.



{% embed url="https://youtu.be/1kgsAaRfU8I?si=-48uuoKqEDm3qUpR" %}



***

### 3️⃣ Trash bin

Deleted a profile by mistake? Octo Browser has a **Trash Bin** where deleted profiles are stored for up to **48 hours** and can be restored from it.

{% hint style="info" %}
After 48 hours, profiles are permanently deleted and can’t be recovered.
{% endhint %}



{% embed url="https://youtu.be/Xv7vBpPxU9o?si=W771h-9FNLfI56X-" %}



***

### 4️⃣ Cookie robot

The **Cookie Robot** in Octo Browser visits the URLs you provide and collects cookies and pixels into the profile.

#### How the Cookie Robot works

* The more URLs you load, the longer the robot will run.
* Once done, all collected cookies are saved to the profile.
* You can view the collected cookies here: `chrome://settings/content/all`.



{% embed url="https://youtu.be/Ne9SEnkmnrY?si=TEOX2xB_T_dDeWi8" %}



***

### 5️⃣ Webcam stream replacement

This feature replaces the webcam feed with a pre-recorded video. It is available on Windows.

#### Video file requirements

* Formats: `.mp4` or `.mov`
* Codec: `h264`
* Max size: **50 MB**



{% embed url="https://youtu.be/FIKZQL0JLpg?si=prsVtIfiAVKVkqeM" %}



***

### 6️⃣ Team collaboration

Octo Browser has a set of features for teamwork:

* ✅ Share profiles, cookies, and proxies
* ✅ Fine-grained control over roles and access
* ✅ Track activity history for each team member
* ✅ Create tasks, assign team members, and set deadlines



{% embed url="https://youtu.be/ThAd0ylIkF8?si=FXuBnKnZuc-ZAJPN" %}



***

### 7️⃣ Profile templates

**Templates** let you pre-configure profile settings, so new profiles can be created quickly:

* Proxies, extensions, tags, profile icons and start pages are all set in advance.
* You can edit all profile settings except the selected operating system.
* Templates are available with all subscription plans and can be password-protected.



{% embed url="https://youtu.be/rhN3IZcX1HY?si=2TkdlNNJjlQMVPe4" %}



***

## 🛠️ Creating 20 profiles with GonzoProxy residential proxies

### 📍 Step 1: Prepare proxies in [GonzoProxy](https://gonzoproxy.com/?utm_source=gitbook\&utm_medium=octobrowser\&utm_content=eng)



<figure><img src=".gitbook/assets/резиденсткие (1).png" alt=""><figcaption></figcaption></figure>



* Create **20 residential proxies** (for example, US-based).
* Your proxy format will look like this:

```
Gonzoj9CiIi_c_US_s_204976RWZ_ttl_72h:RNW78Fm5@connect.gonzoproxy.app:10000
```

* Add `socks5://` or `https://` before the proxy string:

```
socks5://Gonzoj9CiIi_c_US_s_204976RWZ_ttl_72h:RNW78Fm5@connect.gonzoproxy.app:10000
```

* Paste the proxies into Octo Browser.



<figure><img src=".gitbook/assets/прокси (2).png" alt=""><figcaption></figcaption></figure>



***

### 📍 Step 2: Create and configure a profile template

* Set a profile name and choose an icon.
* Assign the 20 proxies from Step 1.
* Add tags, start pages, and bookmarks.
* Enable the noise options: **WebGL, Canvas, Audio, Client Rects**.
* Set language, timezone, and geolocation to **"Based on IP."**
* Install any required extensions.



<figure><img src=".gitbook/assets/шаблон.png" alt=""><figcaption></figcaption></figure>



***

### 📍 Step 3: Bulk profile creation

* Go to the **Bulk Profile Creation** mode.



<figure><img src=".gitbook/assets/профили.png" alt=""><figcaption></figcaption></figure>



* Set quantity: **20 profiles**. Click **"Add"** and save.



<figure><img src=".gitbook/assets/профили 2 (1).png" alt=""><figcaption></figcaption></figure>



🎉 Done. The 20 profiles are created, each with its own proxy.



<figure><img src=".gitbook/assets/профили 3.png" alt=""><figcaption></figcaption></figure>



***

### 👾 Try it here: [GonzoProxy.com](https://gonzoproxy.com/?utm_source=gitbook\&utm_medium=octobrowser\&utm_content=eng)

***

### 📱 Stay Connected

* [Telegram Channel](https://t.me/GonzoProxy)
* [Telegram Chat ](https://t.me/GonzoProxy_Chat)
* [Instagram](https://www.instagram.com/gonzoproxy)
* [24/7 Support](https://t.me/GonzoProxy_bot)

💬 Our team is always here for you! Reach out anytime.
