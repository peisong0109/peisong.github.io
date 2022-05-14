---
layout: post
read_time: true
show_date: true
title: "What is Edge Computing?"
date: 2022-04-05
img: posts/20220405/Title.jpg
tags: [Edge computing]
category: Research
author: Peisong Li
description: "Intorduction to Edge Conputing"
---

## Concept
Industry investment and research interest in edge computing, in which computing and storage nodes are placed at the Internet’s edge in close proximity to mobile devices or sensors, have grown dramatically in recent years. This emerging technology promises to deliver highly responsive cloud services for mobile computing, scalability and privacy-policy enforcement for the Internet of Things, and the ability to mask transient cloud outages [1].

## Origin and Background
1. **1990s**, when Akamai introduced content delivery networks (CDNs) to accelerate web performance. A CDN uses nodes at the edge close to users to prefetch and cache web content. These edge nodes can also perform some content customization, such as adding location-relevant advertising. CDNs are especially valuable for video content, because the bandwidth savings from caching can be substantial [2].
2. In **1997**, Brian Noble and his colleagues first demonstrated edge computing’s potential value to mobile computing. They showed how speech recognition could be implemented with acceptable performance on a resource-limited mobile device by offloading computation to a nearby server [3]. In **1999**, Jason Flinn and Satyanarayanan extended this approach to improve battery life [4]. In a **2001** article that generalized these concepts, Satyanarayanan introduced the term cyber foraging for the amplification of a mobile device’s computing capabilities by leveraging nearby infrastructure  [5].
3. Cloud computing’s emergence in the **mid-2000s** led to the cloud becoming the most obvious infrastructure to leverage from a mobile device.
4. In **2009**, Satyanarayanan coauthored with Paramvir Bahl, Rámon Cáceres, and Nigel Davies that laid the conceptual foundation for edge computing. We advocated a two-level architecture: the first level is today’s unmodified cloud infrastructure; the second level consists of dispersed elements called **cloudlets** with state cached from the first level. Using persistent caching instead of hard state simplifies the management of cloudlets despite their physical dispersal at the Internet edge  [6].
5. In **2012**, Flavio Bonomi and his colleagues introduced the term fog computing to refer to this dispersed cloud infrastructure [7].

### Research directions

### My current work

## Reference
[1] Satyanarayanan, Mahadev. "The emergence of edge computing." _Computer_ 50.1 (2017): 30-39.

[2] Dilley, John, et al. "Globally distributed content delivery." _IEEE Internet Computing_ 6.5 (2002): 50-58.

[3] Noble, Brian D., et al. "Agile application-aware adaptation for mobility." _ACM SIGOPS Operating Systems Review_ 31.5 (1997): 276-287.

[4] Flinn, Jason, and Mahadev Satyanarayanan. "Energy-aware adaptation for mobile applications." _ACM SIGOPS Operating Systems Review_ 33.5 (1999): 48-63.

[5] Satyanarayanan, Mahadev. "Pervasive computing: Vision and challenges." _IEEE Personal communications_ 8.4 (2001): 10-17.

[6] Satyanarayanan, Mahadev, et al. "The case for vm-based cloudlets in mobile computing." _IEEE pervasive Computing_ 8.4 (2009): 14-23.

[7] Bonomi, Flavio, et al. "Fog computing and its role in the internet of things." _Proceedings of the first edition of the MCC workshop on Mobile cloud computing_. 2012.

![Edge computing](./assets/img/posts/20220405/Edge.jpg)
