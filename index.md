---
layout: default
---
**!! THIS PROJECT IS STILL IN BETA !!**

Welcome to the Albion Data Project!

The goal of this project is to collect and distribute realtime information for Albion Online. This is achieved with a downloadable client that monitors network traffic specifically for Albion Online, identifies the relevant information, and then ships it off to a central server which distributes the information to anyone who wants it.

[Click here to download the client.](https://github.com/Regner/albiondata-client/releases)

### Player Information
If you would like to help the Albion Data Project, and all the web sites and applications that use the data provided by it, then the best thing you can do is download our client and run it whenever you're playing Albion Online.

The most recent releases can be found here: [https://github.com/Regner/albiondata-client/releases](https://github.com/Regner/albiondata-client/releases)

### Developer Information
If you're building something to consume the data published by the
Albion Data Project here are some things you will need to know:
- NATS Connection String: nats://public:notsecure@ingest.albion-data.com:4222
- NATS Topics:
  - goldprices.deduped
  - marketorders.deduped
  - mapdata.deduped
- Structure of data messages: [albiondata-client/lib](https://github.com/Regner/albiondata-client/tree/master/lib)

A note on duplicate messages. As information comes into the NATS Server it is looked at and deduplicated over a 5 minute window. As a subscriber the goal is that you should only get the same message once every 5 minutes. This is of course open for change as we go however. The reason we are sending the same message at all is two fold.
 
New people connecting to the network may have missed previous messages. Along with that however we don’t have a good way of noticing things like market orders completing. To remove market orders from your application the current best idea around is to keep track of the last time an order was seen, and then after not seeing it for X hours remove it as probably having been completed.

### Related Projects
- [albiondata-client](https://github.com/Regner/albiondata-client)
- [albiondata-deduper](https://github.com/Regner/albiondata-deduper)
- [albiondata-sql](https://github.com/pcdummy/albiondata-sql)
- [albiondata-api](https://github.com/pcdummy/albiondata-api)

### Contact Us
The best way to get in touch with us is on the Albion Online Fansites Discord server in either the #proj-albiondata or the #developers channel. A permanent invite link can be found here: [https://discord.gg/8DDSjTs](https://discord.gg/8DDSjTs)

### Is This Allowed
> Our position is quite simple. As long as you just look and analyze we are ok with it. The moment you modify or manipulate something or somehow interfere with our services we will react (e.g. perma-ban, take legal action, whatever).

~MadDave, Technical Lead at Sandbox Interactive for Albion Online, [source](https://forum.albiononline.com/index.php/Thread/51604-Is-it-allowed-to-scan-your-internet-trafic-and-pick-up-logs/?postID=512670#post512670)
