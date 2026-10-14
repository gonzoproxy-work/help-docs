---
icon: toggle-off
---

# Proxy Stopped Working: Why It Happens and What to Do

Our proxies run on real devices belonging to people who rent out their IP addresses. These are "live" addresses, but this approach has a quirk: a device can turn off, lose its connection, go to sleep, or overload its channel at any moment.

When that happens, you see one of two things: the proxy stops responding because the device went offline, or the connection keeps dropping because of an unstable link. The proxy itself is technically fine. The device it was tied to has simply become unavailable.

The more detailed your GEO settings are, the fewer devices match them. The provider filter narrows the choice the most: there may be very few devices from a specific operator in the region you need, and some of them are switched off at the moment. That is why the selected provider is most often the cause of the problem.

### What to Do

1. Create a new proxy. It will connect to a different device, and the problem tied to the old one will go away.
2. Don't select a provider. Keep the country and region, and leave the "Provider" field empty. Many more devices will match, and you are more likely to get a stable one.
3. If you need a specific city, start by widening the filter to the region. You can add the city later if your task really requires it.
4. Send a screenshot of your new proxy's GEO settings to[ @GonzoProxy\_bot](https://t.me/GonzoProxy_bot). We will look at which parameters you choose and suggest what to change, for example removing the provider or widening the region.
