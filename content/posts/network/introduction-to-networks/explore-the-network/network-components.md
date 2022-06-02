+++
date = 2021-10-12T23:07:50+09:30
title = "Network - Components"
slug = "network-components"
aliases = "network-components"
description = "Network - Components"
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

1. [Overview](#overview)
1. [End Devices](#end-devices)
    1. [Examples](#examples)
1. [Intermediary Network Devices](#intermediary-network-devices)
    1. [Examples](#examples-1)
    1. [Functions](#functions)
1. [Network Media](#network-media)
1. [Other Terminologies](#other-terminologies)
1. [Topology Diagrams](#topology-diagrams)

### Overview

The path that a message takes from source to destination can be as simple as a
single cable connecting one computer to another, or as complex as a collection
of networks that literally spans the globe. This network infrastructure provides
the stable and reliable channel over which these communications occur.

The network infrastructure contains three categories of network components:

1. Devices
1. Media
1. Services

**Devices** and **media** are the physical elements, or hardware, of the
network. Hardware is often the visible components of the network platform such
as a laptop, PC, switch, router, wireless access point, or the cabling used to
connect the devices.

**Services** include many of the common network applications people use every
day, like email hosting services and web hosting services. Processes provide the
functionality that directs and moves the messages through the network. Processes
are less obvious to us but are critical to the operation of networks.

### End Devices

    Data originates with an end device, flows through the network, and arrives
    at another end device.

The network devices that people are most familiar with are called end devices
(since they are the end of the network).

In general, they allow us to interface with the network.

An end device is either the source or destination of a message transmitted over
the network.

To distinguish one end device from another, each end device on a
network is identified by an address - *IP address*.

When an end device initiates communication, it uses the address of the
destination end device to specify where the message should be sent.

##### Examples

- Computers (work stations, laptops, file servers, web servers)
- Network printers
- VoIP phones
- Telepresence endpoint
- Security cameras
- Mobile handheld devices (such as smart phones, tablets, PDAs, and wireless
  debit / credit card readers and barcode scanners)

### Intermediary Network Devices

    connect the individual end devices to the network and can connect multiple
    individual networks to form an internetwork.

These intermediary devices provide connectivity and ensure that data flows
across the network.

Intermediary devices use the destination end device address, in conjunction with
information about the network interconnections, to determine the path that
messages should take through the network.

Intermediary devices are not all the same. Some work inside the LAN performing
switching functions, whilst others help route messages between networks.

##### Examples

| Device Type            | Description                                                                                           |
| --                     | --                                                                                                    |
| Network access devices | Connect end users to their network.<br />Examples are hubs, switches, and wireless access points.          |
| Internetwork devices   | Connect one network to one or more other networks.<br />Routers are the main example.                      |
| Communication servers  | Route services such as IPTV and wireless broadband. Modems                                            | Connect users to servers and networks through telephone or cable. |
| Security devices       | Secure the network with devices such as firewalls that analyse traffic exiting and entering networks. |

##### Functions

Intermediary network devices perform some or all of these functions:

- Regenerate and retransmit data signals
- Maintain information about what pathways exist through the network and
  internetwork
- Notify other devices of errors and communication failures
- Direct data along alternate pathways when there is a link failure
- Classify and direct messages according to Quality of Service (QoS) priorities
- Permit or deny the flow of data, based on security settings

### Network Media

Communication across a network is carried on a **medium** which provides the
channel over which the message travels from source to destination.

Modern networks primarily use three types of media to interconnect devices and
to provide the pathway over which data can be transmitted. These media are:

1. **Metallic wires within cables** - data is encoded into *electrical impulses*
and therefore can be affected by outside interference.
    - cheap and common for short distances
    - e.g., twisted-pair cable usually used as LAN media

1. **Glass or plastic fibers (fiber optic cable)** - data is encoded as *pulses
of light* and therefore not affected by outside interference.
    - transmit data at extremely fast speeds
    - good for long distances
    - e.g., glass or plastic fibers in a vinyl coating usually used for long
      runs in a LAN and as a trunk

1. **Wireless transmission** - data is encoded using *wavelengths* from the
*electromagnetic spectrum*.
    - connects local users through the air
    - wireless networks have decreased throughput compared with wired networks

Different types of network media have different features and benefits. Not all
network media have the same characteristics, nor are they all appropriate for
the same purpose.

### Other Terminologies

| Term                   | Explanation                                                                                                                                                                                                 |
| --                     | --                                                                                                                                                                                                          |
| Network Interface Card | A NIC, or LAN adapter, provides the physical connection to the network at the PC or other end device.<br />The media that are connecting the PC to the networking device, plug directly into the NIC. |
| Physical Port          | A connector or outlet on a networking device where the media is connected to an end device or another networking device.                                                                                |
| Interface              | Specialised ports on a networking device that connect to individual networks.<br />Because routers are used to interconnect networks, the ports on a router are referred to as network interfaces.               |

### Topology Diagrams

    provide a visual map of how the network is connected.

There are two types of topology diagrams:

1. **Physical topology diagrams** - identify the physical location of
intermediary devices and cable installation.

1. **Logical topology diagrams** - identify devices, ports, and addressing
scheme.
