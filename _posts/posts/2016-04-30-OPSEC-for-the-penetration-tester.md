---
layout: post
title: Avoiding VPN leaks
date: 2016-11-18 12:00:00
categories: posts
comments: true
en: true
description: A simple article on how to keep your ass safe.
---

 Operations security (OPSEC) is a term originating in U.S. military jargon, as a process that identifies critical information to determine if friendly actions can be observed by enemy intelligence, determines if information obtained by adversaries could be interpreted to be useful to them, and then executes selected measures that eliminate or reduce adversary exploitation of friendly critical information. 
 A more detailed explanation you can find on wikipedia [here].
 
 OPSEC is very important to a penetration tester and security professional, in this line of work leaking metadata can have bad consequences. Here at BlackSheep we value privacy and understand that our sensitive work can only be done only if we respect a certain guidelines.
 
### VPN

 A good vpn is the first line of defense, we use [NordVPN] here at BlackSheep, it has a non logging policy, servers anywhere in world and is dead cheap. Of course non logging policy should never be trusted, but we try to stay safe from other people not from law enforcement. There are hundrets of VPN providers or hacked servers for sale online if you want to tunnel traffic trough them so feel free to use what you think is best for you.
 A problem that appears while using VPN is VPN leak, when your real ip is leaked to a 3-rd party server:
 
#### VPN disconnects and you don't notice

For situations like this we found a nice script online that will prevent your computer to make any connections while disconnected from VPN. We adapted it a little because it didn't work with openvpn you can find it [here .]

#### Other VPN tips

* Disable IPv6 (If your isp supports ipv6 and VPN not, when you will connect to a ipv6 server it will connect via ISP connection not trough tunnel)
* Disable WebRTC in your browser (Can leak real ip)
* Use dnscrypt or public DNS Servers (GOOGLE etc). Never use ISP DNS.

We will try to come back with manny posts on opsec as is a very sensitive subject and people tend to overlook.

[here]: https://en.wikipedia.org/wiki/Operations_security
[NordVPN]: https://nordvpn.com/profile/
[here .]: https://github.com/blacksheepvision/onlyVPN
