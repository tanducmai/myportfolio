+++
date = 2021-11-01T14:29:24+09:30
title = "Network - Physical Layer Protocols"
slug = "physical-layer-protocols"
aliases = "physical-layer-protocols"
description = "Network - Physical Layer Protocols"
thumbnail = "images/tn.png"
tags = [
    "network",
]
categories = [
    "network",
]
draft = true
+++

### Table of Contents

<!-- vim-markdown-toc GFM -->

* [Types of Connections](#types-of-connections)
* [Network Interface Cards (NICs)](#network-interface-cards-nics)

<!-- vim-markdown-toc -->

### Types of Connections

Whether connecting to a local printer in the home or a website in another
country, before any network communications can occur, a physical connection to a
local network must be established. A physical connection can be a wired
connection using a cable or a wireless connection using radio waves. The type of
physical connection used is dependent upon the setup of the network.

For example, in many corporate offices employees have desktop or laptop
computers that are physically connected, via cable, to a shared switch. This
type of setup is a **wired network**. Data is transmitted through a *physical
cable*.

In addition to wired connections, many businesses also offer **wireless
connections** for laptops, tablets, and smartphones. With wireless devices, data
is transmitted using *radio waves*. To offer wireless capability, devices on a
wireless network must be connected to a *wireless access point (AP)*.

Switch devices and wireless access points are often two separate dedicated
devices within a network implementation. However, there are also devices that
offer both wired and wireless connectivity. In many homes, for example,
individuals are implementing home *integrated service routers (ISRs)*. ISRs
offer a switching component with multiple ports, allowing multiple devices to be
connected to the LAN using cables. Additionally, many ISRs also include an AP,
which allows wireless devices to connect as well.

### Network Interface Cards (NICs)

    connect a device to the network.

Ethernet NICs are used for a wired connection. An end-user device may include
one or both types of NICs. A network printer, for example, may only have an
Ethernet NIC, and therefore, must connect to the network using an Ethernet
cable. Other devices, such as tablets and smartphones, might only contain a WLAN
NIC and must use a wireless connection.

Not all physical connections are equal, in terms of the performance level, when
connecting to a network.

For example, a wireless device will experience degradation in performance based
on its distance from a wireless access point. The further the device is from the
access point, the weaker the wireless signal it receives. This can mean less
bandwidth or no wireless connection at all. Figure 2 shows that a wireless range
extender can be used to regenerate the wireless signal to other parts of the
house that are too far from the wireless access point. Alternatively, a wired
connection will not degrade in performance.

All wireless devices must share access to the airwaves connecting to the
wireless access point. This means slower network performance may occur as more
wireless devices access the network simultaneously. A wired device does not need
to share its access to the network with other devices. Each wired device has a
separate communications channel over its Ethernet cable. This is important when
considering some applications, such as online gaming, streaming video, and video
conferencing, which require more dedicated bandwidth than other applications.
