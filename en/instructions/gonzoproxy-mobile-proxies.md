# 📱 GonzoProxy Mobile Proxies

### 📲 What are mobile proxies?



<figure><img src="../.gitbook/assets/Mobile.png" alt=""><figcaption></figcaption></figure>



Mobile proxies are IP addresses that cellular carriers issue to their own subscribers. A request sent through one of them reaches the site from a carrier address.

The mobile pool is one of the three pools on the account, next to residential and datacenter. One account, one gateway and one login shape cover all three.

***

### 🔌 Connection

* Gateway: `connect.gonzoproxy.app:10000`
* Protocols answering on that port: SOCKS5, SOCKS5h, HTTP and HTTPS (real TLS to the proxy)
* SOCKS4 and SOCKS4a do not work

Paste the connection string into the proxy field of the tool you work in. The tools our customers name most often are Octo Browser, then Dolphin Anty and AdsPower equally, then curl and Python requests.

***

### 🌍 Choosing a country

The country selector of the mobile pool listed 134 countries when we read the dashboard on 14 September 2026. That is a count of countries in the selector, not a count of addresses.

Selection works at country level. A city can be picked in the dashboard, but that choice does not reach the connection string, so the exit is set by country only. A customer has also reported that the carrier choice does not hold: the first page load showed the selected operator, and a reload ten seconds later showed a different access technology. We have not reproduced this ourselves.

***

### 🔁 Rotation

Two modes are available:

* **A new IP for every request**: the address changes on each request
* **Sticky session**: the address is held for the length of the session

This is what we measured on our own account on 14 September 2026. Over a horizon of 84 minutes, 51 sessions out of 90 kept the same IP, which is 56.7%, with a confidence interval of 46.4% to 66.4%. Half of the losses happened inside the first 35 minutes. Taken on its own the mobile pool gave 53.3%, but the per pool intervals overlap, so we do not claim that any pool holds an address better than another.

We publish nothing beyond the 84 minutes we measured. In a separate run of 7 to 10 September 2026 a single session changed its IP three times during the first 2.5 hours and then held the same address for about 69 hours. That is one session and an existence proof, not a rate to plan against.

Size a job against the measured retention: with 56.7% (51 of 90) still holding at minute 84, you open about 1.8 sessions for each one you need alive at that point, and about 2.2 if you plan against the lower bound of 46.4%.

***

### ⏱️ Speed

In the same run of 14 September 2026 the median response time of the mobile pool was 1.60 s, against 1.33 s for residential and 1.44 s for datacenter. These are medians from a single run and we publish no interval for them. Where the speed of the request matters more than the kind of address, residential or datacenter is the better fit.

***

### 💳 Traffic and payment

* Traffic is paid by the gigabyte from the account balance, and the mobile pool draws on the same balance as the other two. The published price table is on [GonzoProxy.com](https://GonzoProxy.com); there is no separate per gigabyte price for the mobile pool.
* Payment goes through Cryptomus, in cryptocurrency. Card payments have not worked since July 2026.
* Unused traffic balance carries over to the new package.

***

### ⚠️ What the product does not do yet

* The dashboard has no live traffic counter. After 1,523 requests in our run of 14 September 2026 it still read 0.00 GB.
* There are no per port, per geo or per subaccount usage statistics.
* A working proxy is not proof of a funded balance: at a zero balance 35 requests out of 36 still went through.
* When a limit is reached the connection closes silently: TCP is accepted and then closed with no SOCKS5 reply. In our run it took about 25 minutes before connections worked again.

***

### 👾 Try it here: [GonzoProxy.com](https://gonzoproxy.com)

***

### 📱 Stay Connected

* [Telegram Channel](https://t.me/GonzoProxy)
* [Telegram Chat ](https://t.me/GonzoProxy_Chat)
* [Instagram](https://www.instagram.com/gonzoproxy)
* [24/7 Support](https://t.me/GonzoProxy_bot)

💬 Our team is always here for you! Reach out anytime.
