---
layout: post
read_time: true
show_date: true
title: "Fog Computing, Cloudlet and Mobile Edge Computing"
date: 2022-05-29
img: posts/20220405/Title.jpg
tags: [Edge computing]
category: Research
author: Peisong Li
description: "Fog Computing, Cloudlet and Mobile Edge Computing"
---
# Abstract
Comparison of three Edge Computing (**EC**) Implementations: Fog Computing, Cloudlet and Mobile Edge Computing

# EC implementation architectures
### Fog Computing:
The Fog Computing implementation is a decentralized Computing infrastructure based on **Fog Computing Nodes (FCNs)** placed at any point of the architecture between the end devices and the cloud. The FCNs are heterogeneous in nature and thus can be based on different kinds of **elements including but not limited to routers, switches, access points, IoT gateways as well as set-top boxes**.

### Mobile Edge Computing:
MEC can be defined as an implementation of Edge Computing to bring computational and storage capacities to the edge of the network within the **Radio Access Network** to reduce latency and improve context awareness.
The MEC nodes or servers are usually co-located with the Radio Network Controller or a macro base-station.
Extension：[What is a Radio Access Network?](https://en.wikipedia.org/wiki/Radio_access_network)

### Cloudlet Computing:
A Cloudlet can be **defined as a trusted cluster of computers**, well connected to the Internet, with resources available to use for nearby mobile devices. A Cloudlet can be treated as **”data center in a box”** running a virtual machine capable of provisioning resources to enddevices and users in real time over a WLAN network.

# Comparison
| | Fog Computing |  Mobile Edge Computing | Cloudlet Computing
|--|--|--|--
Node devices| Routers, Switches, Access Points, Gateways | Servers running in base stations | Data Center in a box 
Node location | Varying between End Devices and Cloud | Radio Network Controller/Macro Base Station | Local/Outdoor installation
Software Architecture |Fog Abstraction Layer based | Mobile Orchestrator based | Cloudlet Agent based
Proximity |One or Multiple Hops | One Hop | One Hop
Access Mechanisms |Bluetooth, Wi-Fi, Mobile Networks | Mobile Networks | Wi-Fi


# Reference:
[1] Dolui, Koustabh, and Soumya Kanti Datta. "Comparison of edge computing implementations: Fog computing, cloudlet and mobile edge computing." _2017 Global Internet of Things Summit (GIoTS)_. IEEE, 2017.
