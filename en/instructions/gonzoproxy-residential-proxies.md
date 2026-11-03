# 💻 GonzoProxy Residential Proxies

🏠 What are Residential Proxies?<br>
------------------------------------

<figure><img src="../.gitbook/assets/1 (10).png" alt=""><figcaption></figcaption></figure>



**Residential proxies** are IP addresses of real user devices. Your traffic leaves through the home or mobile internet connection of such a device.

Unlike **datacenter proxies**, whose addresses belong to hosting providers, these addresses belong to ordinary consumer connections. When we read our own exit addresses on 17 September 2026, they resolved to household ISP networks: Charter, Comcast, Verizon.

***

### ⚙️ What Follows from the Nature of the Pool

* **The address belongs to someone else's device.** The speed of a session depends on that device and on its channel, not only on our gateway.
* **If a session is slow, recreate the proxy.** You will get a different device, and with it a different channel.
* **A device can go offline at any moment.** An address is yours while the device stays online. The measured numbers are in the Rotation section below.

***

### ✅ Residential Proxies Are Used For:

* Registering and running accounts
* SEO promotion
* Managing ad accounts
* Buying limited-edition items
* Developing and testing software

***

## 💰 How to Start Using Residential Proxies?

### 🔹 Step 1: Buy Traffic

* Buy traffic in gigabytes
* Charging is based on **used traffic**
* Traffic does not expire: the gigabytes you buy stay on your balance until you use them

💲 Price per 1 GB depends on the purchase volume:\
&#x20;      **from $6.50 per GB (minimum purchase 2 GB for $13) down to $2.50 per GB at 1 TB**

<figure><img src="../.gitbook/assets/image_2025-04-21_11-44-48.png" alt=""><figcaption></figcaption></figure>

#### 🔸 Payment Methods

* 💰 **Cryptocurrency**, through Cryptomus

This is the only payment method available today. Bank cards are not accepted: card payments have not worked since July 2026.

<figure><img src="../.gitbook/assets/3 (7).png" alt=""><figcaption></figcaption></figure>

💡 After payment, the purchased traffic will appear **in the top right corner** of your dashboard.

ℹ️ Usage is shown in the dashboard: traffic spent since the start of the day, week and month, the remaining balance (**Traffic Left**), and a **Traffic usage** chart below the generator.



<figure><img src="../.gitbook/assets/4 (6).png" alt=""><figcaption></figcaption></figure>

## 🧩 Step 2. Proxy Setup

In the **Proxy Setup** window, you can generate proxies with custom parameters tailored to your use case.

***

### 🌍 Country

Select the country the exit address will belong to.\
On 14 September 2026 the residential selector listed **198 countries**. That is the number of countries in the selector, not the size of the pool.

***

### 🏙️ City / State / ISP

Fill these fields from the top down: **country first, then region and city, and only then the operator.** Each following field narrows the previous one.

* If the list comes back empty, remove the operator or pick another one. Devices leave the network, so a combination that returned addresses yesterday can return nothing today.
* **ISP (Internet Service Provider)**: the company that provides internet access (e.g., *Comcast, AT\&T, Vodafone*)

Everything you select is written into the login of the connection string. For example, `c_US` is the country, `sd_443` the region (California), `city_Los-Angeles` the city, `isp_74471` the provider.

***

### 🔄 Rotation / IP Change Mode

Decide how frequently the IP address should change:

#### • **Sticky (Sticky Session)**

* The system assigns you one address for the time set in **Limit Session** (up to 7 days) and holds it while the source device stays online
* **Best for:** work tied to a single account
* **What we measured on 14 September 2026:** over an 84-minute horizon, **51 of 90 sessions kept the same address, which is 56.7%** (Wilson interval 46.4% to 66.4%). Half of the losses happened inside the first 35 minutes.
* In a separate 72-hour run from 7 to 10 September 2026, one session held the same address for about 69 hours. That is a single session, not a norm and not a promise.

#### • **Randomize IP**

* Each request is made using a **new IP**
* **Best for:** scraping and automation
* **How it works:** every new request is routed through a random address from your selected pool

***

### 🔧 Protocol

Three protocols work on port **10000**:

* **HTTP**
* **HTTPS** (real TLS to the proxy)
* **SOCKS5**

**SOCKS4 and SOCKS4a do not work.** Checked on 14 September 2026.

***

### ⏳ Limit Session / Session Duration

Sets how long one address stays assigned to you before it changes automatically. Set in seconds, minutes or hours, **up to 7 days** (168 hours).

* After the time expires, a new IP will be assigned
* The value is an upper bound, not a guarantee. The address can change earlier if the device goes offline. See the measured retention in the Rotation section above.

***

### 🖥️ Server / Proxy Server Region

Selects the region of the gateway you connect through. The exit country is set by the **Country** field, not here.

* **Standard**: the server is selected automatically
* **Europe / Asia / USA**: choose the region nearest to you

<figure><img src="../.gitbook/assets/6 (2).png" alt=""><figcaption></figcaption></figure>

#### 🔧 Example Configuration

**Goal:** a proxy with an exit address in **Armenia**.\
**How:** select Armenia in the **Country** field, leave region, city and operator empty, and generate the proxy.\
**Result:** an address in Armenia. You keep it while the device stays online and until the **Limit Session** value runs out, whichever comes first.

***

### 🌐 Step 3: Paste the Proxy into Your Tool

* Paste the generated connection string into the field your tool provides for it. The tools our customers name most often are Octo Browser, then Dolphin Anty and AdsPower, then curl and Python requests.
* Create a **new profile** and set up our proxy
* Check the proxy for functionality

<figure><img src="../.gitbook/assets/7 (5).png" alt=""><figcaption></figcaption></figure>



### 🔎 Step 4: Check the Exit Address

Open an IP-check page through the proxy, for example **whoer.net**, and confirm the address and the country you selected.

<figure><img src="../.gitbook/assets/8 (1).png" alt=""><figcaption></figcaption></figure>

### 🎉 Done!

The proxy is ready to use.

***

## 🧠 Expert Tips for Professionals

Practical recommendations for working with residential proxies.

***

### 🔐 Working with Accounts

* **Golden Rule:**
  **1 proxy = 1 account.** Do not use the same address for several accounts on the same platform.
* **Targeting order:**
  Country first, then region and city, and only then the operator. If the list comes back empty, remove the operator or pick another one.

***

### ⚙️ Performance Optimization

* **Save Bandwidth:**
  Disable loading of images, videos, and heavy scripts. You pay for the traffic you download.
* **Planning Parallel Sessions:**
  Our measured median request time is 1.44 s and the p90 is 2.29 s, which works out to about 40 fetches per minute per worker at the median and about 26 at the p90. Scale by running several sessions in parallel.
* **Slow Session:**
  Recreate the proxy. Speed depends on the device behind the address and on its channel.

***

### 👾 Try it here: [GonzoProxy.com](https://gonzoproxy.com)

***

### 📱 Stay Connected

* [Telegram Channel](https://t.me/GonzoProxy)
* [Telegram Chat ](https://t.me/GonzoProxy_Chat)
* [Instagram](https://www.instagram.com/gonzoproxy)
* [24/7 Support](https://t.me/GonzoProxy_bot)

💬 Our team is always here for you! Reach out anytime.
