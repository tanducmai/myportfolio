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
draft = true
+++

### Table of Contents

<!-- vim-markdown-toc GFM -->

* [OSI Data Link Layer](#osi-data-link-layer)

<!-- vim-markdown-toc -->

### OSI Data Link Layer

The data link layer of the OSI model (Layer 2) is responsible for:

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

The data link layer effectively separates the media transitions that occur as the packet is forwarded from the communication processes of the higher layers. The data link layer receives packets from and directs packets to an upper layer protocol, in this case IPv4 or IPv6. This upper layer protocol does not need to be aware of which media the communication will use.
