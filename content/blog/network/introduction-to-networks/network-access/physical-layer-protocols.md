+++
date = 2021-11-01T14:29:24+09:30
title = "Physical Layer Protocols"
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
draft = false
+++

### Table of Contents

<!-- vim-markdown-toc GFM -->

1. [Types of Connections](#types-of-connections)
1. [Network Interface Cards (NICs)](#network-interface-cards-nics)
1. [Performance Level](#performance-level)
1. [OSI Physical Layer](#osi-physical-layer)
1. [Physical Layer Media](#physical-layer-media)

<!-- vim-markdown-toc -->

### Types of Connections

Whether connecting to a local printer in the home or a website in another
country, before any network communications can occur, a physical connection to a
local network must be established. A physical connection can be a wired
connection using a cable or a wireless connection using radio waves. The type of
physical connection used is dependent upon the set-up of the network.

For example, in many corporate offices employees have desktop or laptop
computers that are physically connected, via cable, to a shared switch. This
type of setup is a **wired network**. Data is transmitted through a *physical
cable*.

In addition to wired connections, many businesses also offer **wireless
connections** for laptops, tablets, and smartphones. With wireless devices, data
is transmitted using *radio waves*. To bring wireless capability to a wired
network, devices on a wireless network must be connected to a wireless **access
point (AP)**.

Switch devices (wired) and access points (wireless) are often two separate
dedicated devices within a network implementation. However, there are also
networking devices that offer both wired and wireless connectivity. In many
homes, for example, individuals are implementing home **integrated service
routers** (ISR, IP router, or network router). ISRs offer a switching component
with multiple ports, allowing multiple devices to be connected to the LAN using
cables. Additionally, many ISRs also include an AP, which allows wireless
devices to connect as well.

### Network Interface Cards (NICs)

    connect a device to the network.

**Ethernet NICs** are used for a wired connection. An end-user device may
include one or both types of NICs. For instance, a network printer may only have
an Ethernet NIC and therefore must connect to the network using an Ethernet
cable. Other devices, such as tablets and smartphones, might only contain a
**WLAN NIC** and therefore must use a wireless connection.

### Performance Level

    Not all physical connections are equal, in terms of the performance level,
    when connecting to a network.

For example, a wireless device will experience degradation in performance based
on its distance from an AP. The further the device is from the AP, the weaker
the wireless signal it receives. This can mean less bandwidth or no wireless
connection at all.

All wireless devices must share access to the airwaves connecting to the AP.
This means slower network performance may occur as more wireless devices access
the network simultaneously. A wired device does not need to share its access to
the network with other devices. Each wired device has a separate communications
channel over its Ethernet cable. This is important when considering some
applications, such as online gaming, streaming video, and video conferencing,
which require more dedicated bandwidth than other applications.

For wireless connections, to strengthen the signal, a wireless **range
extender** can be used to regenerate the wireless signal to other parts that are
too far from the AP. Alternatively, a wired connection will not degrade in
performance no matter how far the device is from the AP.

### OSI Physical Layer

    defines the means of transmitting a stream of raw bits over a physical data
    link connecting network nodes.

It accepts a complete frame from the data link layer and encodes it as a series
of signals, called bits, that are transmitted onto the local media. The encoded
bits that comprise a frame are received by either an end device or an
intermediary device.

The process that data undergoes from a source node to a destination node is:

1. The user data is segmented by the transport layer, placed into packets by the
   network layer, and further encapsulated into frames by the data link layer.
1. The physical layer encodes the frames and creates the electrical, optical, or
   radio wave signals that represent the bits in each frame.
1. These signals are then sent on the [media](#physical-layer-media), one at a
   time.
1. The destination node's physical layer retrieves these individual signals from
   the media, restores them to their bit representations, and passes the bits up
   to the data link layer as a complete frame.

### Physical Layer Media

There are three basic forms of network media. The physical layer produces the
representation and groupings of bits for each type of media as:

1. **Copper cable**: The signals are patterns of electrical pulses.
1. **Fiber-optic cable**: The signals are patterns of light.
1. **Wireless**: The signals are patterns of microwave transmissions.
