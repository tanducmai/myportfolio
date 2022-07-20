+++
date = 2021-11-03T23:42:49+09:30
title = "Data Link Layer Protocols"
slug = "data-link-layer-protocols"
aliases = "data-link-layer-protocols"
description = "Data Link Layer Protocols"
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

1. [OSI Data Link Layer](#osi-data-link-layer)
1. [Data Link Sublayers](#data-link-sublayers)
1. [Providing Access to Media](#providing-access-to-media)

<!-- vim-markdown-toc -->

### OSI Data Link Layer

    accepts a packet from the network layer and prepares it for transport on the physical media.

The data link layer of the OSI model (layer 2) is responsible for:

- Allowing the upper layers to access the media
- Accepting Layer 3 packets and packaging them into frames
- Preparing network data for the physical network
- Controlling how data is placed and received on the media
- Exchanging frames between nodes over a physical network media, such as UTP or
  fiber-optic
- Receiving and directing packets to an upper layer protocol
- Performing error detection

The Layer 2 notation for network devices connected to a common media is called a
**node**. Nodes build and forward frames. The OSI data link layer is responsible
for the exchange of Ethernet frames between source and destination nodes over a
physical network media.

The data link layer effectively separates the media transitions that occur as
the packet is forwarded from the communication processes of the higher layers.
The data link layer receives packets from and directs packets to an upper layer
protocol (IPv4 or IPv6). This upper layer protocol does not need to be aware of
which media the communication will use.

### Data Link Sublayers

To facilitate its purpose, the data link layer consists of two sublayers:

1. **Logical Link Control (LLC)** - This upper sublayer communicates with the
   network layer. It places information in the frame that identifies which
   network layer protocol is being used for the frame. This information allows
   multiple Layer 3 protocols, such as IPv4 and IPv6, to utilise the same
   network interface and media.
1. **Media Access Control (MAC)** - This lower sublayer defines the media access
   processes performed by the hardware. It provides data link layer addressing
   and access to various network technologies.

The LLC communicates with the network layer while the MAC sublayer allows
various network access technologies. For instance, the MAC sublayer communicates
with Ethernet LAN technology to send and receive frames over copper or
fiber-optic cable. The MAC sublayer also communicates with wireless technologies
such as Wi-Fi and Bluetooth to send and receive frames wirelessly.

### Providing Access to Media

Different media access control methods may be required during a single
communication. Each network environment that packets encounter as they travel
from a local host to a remote host can have different characteristics. For
example, an Ethernet LAN consists of many hosts contending to access the network
medium. Serial links consist of a direct connection between only two devices.

Router interfaces encapsulate the packet into the appropriate frame, and a
suitable media access control method is used to access each link. In any given
exchange of network layer packets, there may be numerous data link layers and
media transitions.

At each hop along the path, a router:

1. Accepts a frame from a medium
1. De-encapsulates the frame
1. Re-encapsulates the packet into a new frame
1. Forwards the new frame appropriate to the medium of that segment of the
   physical network

For example, a router has an Ethernet interface to connect to the LAN and a
serial interface to connect to the WAN. As the router processes frames, it will
use data link layer services to receive the frame from one medium,
de-encapsulate it to the Layer 3 PDU, re-encapsulate the PDU into a new frame,
and place the frame on the medium of the next link of the network.
