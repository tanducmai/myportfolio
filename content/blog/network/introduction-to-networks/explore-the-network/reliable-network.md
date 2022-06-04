+++
date = 2021-10-14T15:28:52+09:30
title = "Network - Reliability"
slug = "reliable-network"
aliases = "reliable-network"
description = "Reliable Network"
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

<!-- vim-markdown-toc -->

### Network Architecture

    the technologies that support the infrastructure and the programmed services
    and rules, or protocols, that move data across the network.

Networks must support a wide range of applications and services, as well as
operate over many different types of cables and devices, which make up the
physical infrastructure.

There are four basic characteristics that the underlying architectures need to
address in order to meet user expectations:

1. Fault Tolerance
1. Scalability
1. Quality of Service (QoS)
1. Security

### Fault Tolerance

The expectation is that the Internet is always available to the millions of
users who rely on it. This requires a network architecture that is built to be
fault tolerant. A fault tolerant network is one that limits the impact of a
failure, so that the fewest number of devices are affected. It is also built in
a way that allows quick recovery when such a failure occurs. These networks
depend on multiple paths between the source and destination of a message. If one
path fails, the messages can be instantly sent over a different link. Having
multiple paths to a destination is known as redundancy.

One way reliable networks provide redundancy is by implementing a
packet-switched network. Packet switching splits traffic into packets that are
routed over a shared network. A single message, such as an email or a video
stream, is broken into multiple message blocks, called packets. Each packet has
the necessary addressing information of the source and destination of the
message. The routers within the network switch the packets based on the
condition of the network at that moment. This means that all the packets in a
single message could take very different paths to the destination. In the
figure, the user is not aware and is unaffected by the router dynamically
changing the route when a link fails.

This is not the case in circuit-switched networks traditionally used for voice
communications. A circuit-switched network is one that establishes a dedicated
circuit between the source and destination before the users may communicate. If
the call is unexpectedly terminated, the users must initiate a new connection.

