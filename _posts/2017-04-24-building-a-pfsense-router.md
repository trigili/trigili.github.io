---
layout: post
title:  "Building a pfSense Router"
date:   2017-04-24
categories: guide pfsense
---
## Building a pfSense Router
*Dec 2020 Update: I've been moving my old blog posts that I wrote during undergrad to my new website since they were getting a fair amount of traffic. I quickly regretted my decision to purchase a cheap SSD since it, unsurprisingly, died rather quickly. Fortunately, I keep frequent config backups. Otherwise, this router still does great and can handle any CPU and memory-intensive task I throw at it, such as Snort or Suricata. I've also found Squid to be largely useless with most traffic being encrypted.*  
<br>
For the past few years, I’ve been using a T-Mobile Cellspot Router (or rather, a T-Mobile branded ASUS RT-AC68U… same thing, but cheaper from T-Mobile) as my primary router. It’s been holding up fine and doing everything I really need it to, especially so after [putting DD-WRT on it](http://www.dd-wrt.com/wiki/index.php/Asus_T-Mobile_Cellspot) a few months ago.  
<br>
That said, I’ve recently been wanting to try out PFSense for a number of reasons. For one, PFSense has a number of packages that can be added to further increase its functionality. What better way to learn how Snort, Squid, Suricata, or other tools work than to try setting them up on my home network? Additionally, because PFSense is FreeBSD based, I could get an opportunity to get some experience working with FreeBSD, something I could certainly use.  
<br>
The most obvious issue with using PFSense as a router is that it’s geared toward x86 architectures… certainly not what one would expect to find on most consumer routers (including my Cellspot). As a result, I’ve decided to build my own!  
<br>
I’ve considered a lot of options as far as hardware goes. I wanted something inconspicuous and roughly consumer router-sized. I decided to look into about the size of [Intel Mini PCs](http://www.intel.com/content/www/us/en/mini-pc/mini-pc-overview.html) – various computer OEMs have picked up the term and seem to have reached a consensus on what size a “Mini PC” should be. I knew I was going to need something that had at least two Ethernet adapters on it; with PFSense, that’s a given (for what I want to do with it, at least).  
<br>
As far as specifications went, I decided to refer to the [PFSense official requirements page](https://www.pfsense.org/hardware/#requirements) as a guide. I would either be on the upper end of the 21-100 Mbps range, or the lower end of the 101-500 Mbps. I opted for the latter option since it would give me more options to choose from, and since I anticipate installing plenty of packages. The recommended processor for this range is, “No less than a modern Intel or AMD CPU clocked at 2.0 GHz”. I felt that an i3 would be good for this task.  
<br>
What I wanted boiled down to something small, has two Ethernet adapters, and an i3. ZOTAC makes Mini PCs with what I’m looking for, and of the many options I was considering, I went for the [ZOTAC ZBOX-RI531](https://www.zotac.com/us/product/mini_pcs/ri531). There are plenty of features this computer has that I won’t be using, such as wireless connectivity and RAID. I’ll probably still use my Cellspot as a bridge since it’s my understanding that PFSense is picky when it comes to creating a Wireless AP. As for RAID, I may implement RAID 1 later, but for the time being I’ll save money and see if I can set up PFSense to schedule regular backups to my NAS.  
<br>
Since I’m not using some of the best features of this computer, it’s probably overkill to say the least. That said, it was about the best option I could find that had everything I was looking for. Since the computer doesn’t include any storage or memory, I purchased a [Crucial 8GB DDR3L stick](https://www.amazon.com/gp/product/B006YG8X9Y/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1) and a [cheap 60GB SSD](https://www.amazon.com/gp/product/B01K1W7JNW/).  
<br>
Once the hardware arrived, it was as simple as putting everything together and using a flash drive to install PFSense. I was surprised with how intuitive it is, compared to custom router firmwares such as DD-WRT, and even some official router firmwares, like the ones included on Verizon Actiontec routers. The versatility of PFSense impressed me as well, even for home users. In less than ten minutes I was able to configure a OpenVPN server and am able to download preconfigured installation tools for a multitude of operating systems. Of the ones I’ve tried (Windows, Linux, and Android) they seem to work pretty well.  
<br>
Since I’m sharing an apartment with three others with a very poor downlink, I set up my new router to use [Squid](http://www.squid-cache.org/) as well. This caches commonly requested web resources (even YouTube videos, etc., if properly configured), reducing not only the bandwidth to the ISP consumed but also speeding up the times to retrieve those resources from the device.  
<br>
All-in-all, I’m glad to have chosen to do this project, as not only was it beneficial to my (and my roommates) computers, phones, and other WiFi connected devices, but I am getting experience working with PFSense and various firewall tools as well.  
