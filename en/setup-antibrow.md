# ✍️ Setup AntiBrow

[**AntiBrow**](https://antibrow.com/) is an anti-detect browser for Windows, macOS and Linux. Every account lives in its own environment with a separate device fingerprint, its own cookies and its own proxy. The data is spoofed inside the browser engine itself, not by a script running on top of the page.

This guide shows how to connect [**GonzoProxy**](https://gonzoproxy.com/?utm_source=gitbook\&utm_medium=antibrow\&utm_content=en) residential proxies to AntiBrow and build several environments where each one has its own IP address.

***

## 📌 Key features of AntiBrow

### 1️⃣ Free local profiles

You can create as many profiles as you like, with no bank card. They are stored on your own disk and never leave it until you turn on cloud sync for a particular profile.

Paid plans add something else: more simultaneous launches, cloud sync and Live View.

| Plan       | Price per month | Simultaneous browsers | Cloud profiles |
| ---------- | --------------- | --------------------- | -------------- |
| Free       | $0              | 1                     | none           |
| Basic      | $9.99           | 5                     | 20             |
| Pro        | $19.99          | 20                    | 100            |
| Team       | $49.99          | 100                   | 1,000          |
| Enterprise | $499            | unlimited             | 10,000         |

> ℹ️ Prices and limits can change, so check the [AntiBrow website](https://antibrow.com/) before you buy.

***

### 2️⃣ Real device fingerprints

Each profile is built as a whole from one real device: Canvas, WebGL, audio, fonts and the other parameters match each other. The app checks the identity for contradictions on its own, and the **“Regenerate”** button creates a fresh variant.

You choose the browser core version for every profile separately. If an account was warmed up on one version, it stays on that version even after a newer one comes out.

***

### 3️⃣ Passkeys

Every environment has its own virtual authenticator. When a website registers a passkey, AntiBrow saves it into the profile and replays it automatically on the next login. This is on by default, and you can switch it off in the profile dialog.

***

### 4️⃣ Proxies without an extension

The proxy login and password are handled inside the engine. No helper extension is installed, so the `chrome://extensions` page stays empty.

***

### 5️⃣ Android profile without a phone

When you create an environment, choose the **Android** device type and AntiBrow imitates a phone right on your computer: user agent, touch input and screen. It works on every plan, including the free one.

> ⚠️ The device type is set once, at creation. You cannot change it on an existing profile. Android needs core version 151 or newer, and the app downloads it for you.

***

### 6️⃣ Groups, tags and color labels

Profiles can be sorted into groups, marked with tags and searched in the table. The address bar of an open window always shows the profile name and its color, so mixing up two tabs is hard.

***

### 7️⃣ Recycle bin and export

A deleted profile goes to the recycle bin and stays there for **30 days**, then it is removed for good. Any local profile can be exported to a `.antibrow.zip` file and opened on another computer. The fingerprint, cookies, storage, bookmarks and passkeys travel with it.

***

## 🛠️ Connecting GonzoProxy to AntiBrow

### 📍 Step 1: Install and sign in

* Download the app from the [AntiBrow website](https://antibrow.com/): `.exe` for Windows 10 and newer, `.dmg` for macOS (separate builds for Apple Silicon and Intel) or `.AppImage` for Linux.
* On Linux, make the file executable with `chmod +x` before you run it.
* Open AntiBrow and enter your email. No password is needed: a six-digit code arrives in your inbox.
* On the first launch of any environment the app downloads the browser core by itself, about 200 MB. This happens once for each version.

***

### 📍 Step 2: Create a proxy in GonzoProxy

Open your [GonzoProxy](https://gonzoproxy.com/?utm_source=gitbook\&utm_medium=antibrow\&utm_content=en) dashboard and set the parameters in the **Proxy Setup** window:

<figure><img src=".gitbook/assets/1 (1).jpg" alt=""><figcaption></figcaption></figure>

* **Country**: the country of the exit IP. If you need more precision, add a region and a city. Pick the ISP last, and if the result comes back empty, simply remove it.
* **Rotation**: choose **Sticky**. A browser profile needs the same address for as long as it works.
* **Limit Session**: how long the address stays assigned to you, up to 7 days. 72 hours suits a permanent account.
* **Protocol**: HTTP, HTTPS or SOCKS5. The port is the same for all of them, 10000.

The generator builds the string. Add the protocol in front of it:

```
http://Gonzoxxxxxx_c_US_s_ab12cd_ttl_72h:password@connect.gonzoproxy.app:10000
```

Your settings are encoded in the login: `c_US` is the country, `s_ab12cd` is the session ID and `ttl_72h` is the session lifetime. A new ID gives you a new address, and the old ID brings back the same one for as long as the device behind it stays online.

> ⚠️ **Randomize IP** is not suitable for environments. The address would change with every connection, and the profile time zone would drift away from the place the pages are actually reached from.

***

### 📍 Step 3: Add the proxy to AntiBrow

* Open the **Proxies** page in the side menu.

<figure><img src=".gitbook/assets/2 (19).png" alt=""><figcaption></figcaption></figure>

* Add your own proxy and paste the string from the previous step. If the app asks for the values one by one, enter the type, the host `connect.gonzoproxy.app`, the port `10000`, the login and the password.

<figure><img src=".gitbook/assets/3.jpg" alt=""><figcaption></figcaption></figure>

* Run the connection check. The exit region and the latency will appear in the list.

<figure><img src=".gitbook/assets/4.jpg" alt=""><figcaption></figcaption></figure>

> ℹ️ Your own proxies do not count against the monthly quota of AntiBrow managed proxies, so their number is not limited.

***

### 📍 Step 4: Create an environment

* Go to **Environments** and click **New profile**.

<figure><img src=".gitbook/assets/5.jpg" alt=""><figcaption></figcaption></figure>

* On the **Overview** tab set the name, the group and the tags. Leave the storage mode on **Local** if you do not need sync.
* Choose the device type: **Desktop** or **Android**.

<figure><img src=".gitbook/assets/6.jpg" alt=""><figcaption></figcaption></figure>

* The fingerprint is generated automatically. If you do not like the result, click **Regenerate**.
* Keep passkey capture turned on.

<figure><img src=".gitbook/assets/7.jpg" alt=""><figcaption></figcaption></figure>

* In the **Proxy** block select the address you added in the previous step.

<figure><img src=".gitbook/assets/8.jpg" alt=""><figcaption></figcaption></figure>

* The time zone, language and geolocation adjust to the exit country, so you do not need to change them by hand.
* In the **Defined identity** panel on the right, check that the external IP and the time zone match the country you want, then save the profile.

***

### 📍 Step 5: Launch and check

* Click **Open** in the profile row. The status column will show **Running**.

<figure><img src=".gitbook/assets/9.jpg" alt=""><figcaption></figcaption></figure>

* In that window open any IP check page, for example **whoer.net**, and make sure the country and the time zone match what you chose in GonzoProxy.

<figure><img src=".gitbook/assets/10.jpg" alt=""><figcaption></figcaption></figure>

* If the address is wrong, close the window, wait a little and launch the profile again. A sticky session sometimes changes ahead of schedule, because the donor device can drop offline.

🎉 **Done!** The profile now works through a GonzoProxy residential address.

***

### 📍 Step 6: Several environments

Every account needs its own address, so do it like this:

* Create as many proxies in GonzoProxy as you have accounts. The session IDs must all be different.
* Add each of them on the **Proxies** page.
* Set up one profile all the way through, then open the `⋯` menu, choose **Duplicate** and put a different proxy into the copy.
* Arrange the profiles by groups and tags so you can find the right one quickly later.

***

## 💻 For developers: Playwright and MCP

AntiBrow is controlled through the ordinary Playwright API, so there is no separate SDK to learn. The API key is created in your AntiBrow dashboard.

TypeScript:

```ts
import { AntiDetectBrowser } from "anti-detect-browser"

const ab = new AntiDetectBrowser({ key: "your-api-key" })

const { browser, page } = await ab.launch({
  profile: "acc-01",
  proxy: "http://Gonzoxxxxxx_c_US_s_ab12cd_ttl_72h:password@connect.gonzoproxy.app:10000",
})

await page.goto("https://example.com")
```

Python:

```python
from antibrow import launch

browser = launch(
    profile="acc-01",
    proxy="http://Gonzoxxxxxx_c_US_s_ab12cd_ttl_72h:password@connect.gonzoproxy.app:10000",
)

page = browser.new_page()
page.goto("https://example.com")
```

To connect an AI agent to the browser, start the MCP server:

```
npx -y -p anti-detect-browser -p @modelcontextprotocol/sdk anti-detect-browser --mcp
```

Put your key into the `ANTI_DETECT_BROWSER_KEY` environment variable. The agent gets tools for launching the browser, opening links, clicking, typing, reading the page and taking screenshots.

***

## 🧠 Expert tips for professionals

### 🔐 Working with accounts

* **1 proxy = 1 account.** Do not run two accounts of the same service through one address.
* **Do not change the country of a warmed-up account.** A website remembers where you usually log in from, and a sudden jump to another place looks suspicious.
* **Compare the IP after every launch.** It takes a few seconds, and a mismatch is visible right away.
* **Financial websites** are closed in the GonzoProxy pool by default.

***

### ⚙️ Optimization

* **Save traffic.** In GonzoProxy you pay for the gigabytes you download, so turn off extra images, video and heavy scripts wherever you do not need them.
* **Slow session.** Recreate the proxy: you will get a different device and a different connection.
* **Core version.** Do not update the core of working accounts without a reason. Let them stay on the version where they started.

***

### ⚠️ Good to know

No anti-detect browser can promise that you will never be blocked. A lot depends on the quality of the proxy, your behavior on the site and the history of the account itself. Before you trust a profile with anything valuable, run it through public fingerprint checks and see the result yourself. The free plan is enough to do that at no cost.

***

### 👾 You can try it here: [GonzoProxy.com](https://gonzoproxy.com/?utm_source=gitbook\&utm_medium=antibrow\&utm_content=en)

***

### 📱 Stay in touch

* [Telegram channel](https://t.me/GonzoProxy)
* [Telegram chat](https://t.me/GonzoProxy_Chat)
* [Instagram](https://www.instagram.com/gonzoproxy)
* [24/7 support](https://t.me/GonzoProxy_bot)

💬 Our team is always available! Contact us at any time of day.
