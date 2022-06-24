+++
date = 2021-10-14T15:28:52+09:30
title = "Network Architecture"
slug = "network-architecture"
aliases = "network-architecture"
description = "Network Architecture"
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

1. [Network Architecture](#network-architecture)
1. [Fault Tolerance](#fault-tolerance)
1. [Scalability](#scalability)
1. [Quality of Service](#quality-of-service)
1. [Security](#security)
1. [Network Architecture Requirements](#network-architecture-requirements)

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

    limits the impact of a failure, so that the fewest number of devices are
    affected.

The expectation is that the Internet is always available to the millions of
users who rely on it. This requires a network architecture that is built to be
fault tolerant. It is also built in a way that allows quick recovery when such a
failure occurs. These networks depend on multiple paths between the source and
destination of a message. If one path fails, the messages can be instantly sent
over a different link. Having multiple paths to a destination is known as
**redundancy**.

One way reliable networks provide redundancy is by implementing a
**packet-switched network**. Packet switching splits traffic into packets that
are routed over a shared network. A single message, such as an email or a video
stream, is broken into multiple message blocks, called **packets**. Each packet
has the necessary addressing information of the source and destination of the
message. The routers within the network switch the packets based on the
condition of the network at that moment. This means that all the packets in a
single message could take very different paths to the destination.

Reasons for packet-switched technology to be chosen for the development of the
Internet:

1. Network devices dynamically decide on the best available path to forward each
   packet.
1. It can rapidly adapt to the failure of network devices and communication
   links.
1. Data packets can travel though the network using multiple different paths.

This is not the case in circuit-switched networks traditionally used for voice
communications. A **circuit-switched network** is one that establishes a
dedicated circuit between the source and destination before the users may
communicate. If the call is unexpectedly terminated, the users must initiate a
new connection.

### Scalability

    ability to expand quickly to support new users and applications without
    degrading the performance of the service being delivered to existing users.

Networks are scalable because the designers follow accepted standards and
protocols. This allows software and hardware vendors to focus on improving
products and services without worrying about designing a new set of rules for
operating within the network.

### Quality of Service

    managed by the router, ensures that priorities are matched with the type of
    communication and its importance to the organisation.

New applications available to users over internetworks, such as voice and live
video transmissions, create higher expectations for the quality of the delivered
services. As data, voice, and video content continue to converge onto the same
network, QoS becomes a primary mechanism for managing congestion and ensuring
reliable delivery of content to all users.

Congestion occurs when the demand for bandwidth exceeds the amount available.
**Network bandwidth** is measured in the number of bits that can be transmitted
in a single second, or bits per second (bps). When simultaneous communications
are attempted across the network, the demand for network bandwidth can exceed
its availability, creating network congestion.

When the volume of traffic is greater than what can be transported across the
network, devices queue, or hold, the packets in memory until resources become
available to transmit them.

For example, one user is requesting a web page and another is on a phone call.
With a QoS policy in place, the router can manage the flow of data and voice
traffic, giving priority to voice communications if the network experiences
congestion.

Examples of priority decisions for an organisation might include:
1. **Time-sensitive communication** - increase priority for services like
   telephony or video distribution.
1. **Non time-sensitive communication** - decrease priority for web page
   retrieval or email.
1. **High importance to organisation** - increase priority for production
   control or business transaction data.
1. **Undesirable communication** - decrease priority or block unwanted activity,
   like peer-to-peer file sharing or live entertainment.

### Security

The network infrastructure, services, and the data contained on network-attached
devices are crucial personal and business assets. There are two types of network
security concerns that must be addressed: network infrastructure security and
information security.

**Network infrastructure security** refers to the physical securing of devices
that provide network connectivity, and preventing unauthorised access to the
management software that resides on them.

**Information security** refers to protecting the information contained within
the packets being transmitted over the network and the information stored on
network attached devices. In order to achieve the goals of network security,
there are three primary requirements for data:

1. Confidentiality - only the intended and authorised recipients can access and
   read data.
1. Integrity - having the assurance that the information has not been altered in
   transmission, from origin to destination.
1. Availability - having the assurance of timely and reliable access to data
   services for authorised users.

### Network Architecture Requirements

<table class="table">
  <thead>
    <tr>
      <th scope="col">Requirement</th>
      <th scope="col">Fault Tolerence</th>
      <th scope="col">Scalability</th>
      <th scope="col">Quality of Service</th>
      <th scope="col">Security</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Networks should always be available.</td>
      <td style="text-align: center; vertical-align: middle;">:heavy_check_mark:</td>
      <td></td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>Priority queues are implemented when demand for network bandwidth exceeds supply.</td>
      <td></td>
      <td></td>
      <td style="text-align: center; vertical-align: middle;">:heavy_check_mark:</td>
      <td></td>
    </tr>
    <tr>
      <td>Business and personal data must be protected.</td>
      <td></td>
      <td></td>
      <td></td>
      <td style="text-align: center; vertical-align: middle;">:heavy_check_mark:</td>
    </tr>
    <tr>
      <td>Developing a plan for priority queuing is a strategy for quality delivery of information.</td>
      <td></td>
      <td></td>
      <td style="text-align: center; vertical-align: middle;">:heavy_check_mark:</td>
      <td></td>
    </tr>
    <tr>
      <td>Networks can grow or expand with minimal impact on performance.</td>
      <td></td>
      <td style="text-align: center; vertical-align: middle;">:heavy_check_mark:</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>Data can travel through more than one route for delivery from a remote source</td>
      <td style="text-align: center; vertical-align: middle;">:heavy_check_mark:</td>
      <td></td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>Common network standards allow hardware and software vendors to focus on product improvements and services.</td>
      <td></td>
      <td style="text-align: center; vertical-align: middle;">:heavy_check_mark:</td>
      <td></td>
      <td></td>
    </tr>
  </tbody>
</table>
