+++
date = 2021-10-27T21:42:13+09:30
title = "Network - Layered Model"
slug = "network-layered-model"
aliases = "network-layered-model"
description = "Network - Layered Model"
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

1. [Benefits of Using Layered Models](#benefits-of-using-layered-models)
1. [The OSI Reference Model](#the-osi-reference-model)
    1. [Layers](#layers)
    1. [Communication Process](#communication-process)
1. [The TCP/IP Protocol Model](#the-tcpip-protocol-model)
    1. [Layers](#layers-1)
    1. [Communication Process](#communication-process-1)
1. [Model Comparision](#model-comparision)

<!-- vim-markdown-toc -->

### Benefits of Using Layered Models

The benefits to using a layered model to describe network protocols and
operations include:

1. Assisting in protocol design because protocols that operate at a specific
   layer have defined information that they act upon and a defined interface to
   the layers above and below.
1. Fostering competition because products from different vendors can work
   together.
1. Preventing technology or capability changes in one layer from affecting other
   layers above and below.
1. Providing a common language to describe networking functions and
   capabilities.

TCP/IP model and the Open Systems Interconnection (OSI) model are the primary
models used when discussing network functionality. They each represent a basic
type of layered networking models:

<table class="table">
  <thead>
    <tr>
      <th scope="col">Protocol model </th>
      <th scope="col">Reference model </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        This type of model closely matches the structure of a particular
        protocol suite. The <b>TCP/IP</b> model is a protocol model because it
        describes the functions that occur at each layer of protocols within the
        TCP/IP suite. TCP/IP is also used as a reference model.
      </td>
      <td>
        This type of model provides consistency within all types of network
        protocols and services by describing what has to be done at a particular
        layer, but not prescribing how it should be accomplished. The <b>OSI</b>
        model is a widely known internetwork reference model, but is also a
        protocol model for the OSI protocol suite.
      </td>
    </tr>
    </tr>
  </tbody>
</table>

Note: Whereas the TCP/IP model layers are referred to only by name, the seven
OSI model layers are more often referred to by number rather than by name. For
instance, the physical layer is referred to as Layer 1 of the OSI model.

### The OSI Reference Model

    describes the entire network communication process in detail.

It is important to know details of the OSI model to understand the entire
network communication process.

The OSI model provides an extensive list of functions and services that can
occur at each layer. It also describes the interaction of each layer with the
layers directly above and below.

##### Layers

Mnemonic:

- Top - Bottom: APSTNDP - All People Seem To Need Data Processing
- Bottom - Top: PDNTSPA - Please Do Not Throw Sausage Pizza Away

Note:

- Layers 6 and 5: not commonly referred to in most instances.
- Layers 7 to 3: primary concern is communications between applications.
- Layers 2 to 1: primary concern is moving raw data cross the network.

<table class="table">
  <thead>
    <tr>
      <th scope="col">#</th>
      <th scope="col">Layer Name</th>
      <th scope="col">Protocols</th>
      <th scope="col">Functional Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">7</th>
      <td>Application</td>
      <td>HTTP, SMTP, FTP, Telnet, DNS</td>
      <td>
        Performs services for the applications used by end users.
      </td>
    </tr>
    <tr>
      <th scope="row">6</th>
      <td>Presentation</td>
      <td>SSL, SSH, IMAP, FTP, MPEG, JPEG</td>
      <td>
        Provides data format information to the application.<br />e.g. tells the
        application layer whether there is an encryption or whether it is a .png
        image.
      </td>
    </tr>
    <tr>
      <th scope="row">5</th>
      <td>Session</td>
      <td>API's, Sockets</td>
      <td>
        Manages data exchange and sessions between users.<br />e.g. synchronises
        multiple web sessions and voice and video data in web conferences.
      </td>
    </tr>
    <tr>
      <th scope="row">4</th>
      <td>Transport</td>
      <td>TCP, UDP, Port Numbers</td>
      <td>
        Defines data segments and numbers them at the source, transfers the
        data, and reassembles the data at the destination.
      </td>
    </tr>
    <tr>
      <th scope="row">3</th>
      <td>Network</td>
      <td>IP Address, ICMP, Routers </td>
      <td>
        Creates and addresses packets for end-to-end delivery through
        intermediary devices in other networks.
      </td>
    </tr>
    <tr>
      <th scope="row">2</th>
      <td>Data Link</td>
      <td>MAC Address, Ethernet, Switches</td>
      <td>
        Creates and addresses frames for host-to-host delivery on the local LANs
        and between WAN devices.
      </td>
    </tr>
    <tr>
      <th scope="row">1</th>
      <td>Physical</td>
      <td>Coax, Cable, Fiber, Wireless, NICs, Hubs</td>
      <td>
        Encodes the binary digits that represent data link layer frames into
        signals and to transmit and receive these signals across the physical
        media (copper wires, optical fiber, and wireless) that connect network
        devices. Physical layer protocols define media specifications.
      </td>
    </tr>
  </tbody>
</table>

##### Communication Process

1. The application data is segmented by the transport layer, placed into packets
   by the network layer, and further encapsulated as frames by the data link
   layer.
1. The physical layer encodes the frames and creates the electrical, optical, or
   radio wave signals that represent the bits in each frame.
1. These signals are then sent on the media one at a time. The destination node
   physical layer retrieves these individual signals from the media, restores
   them to their bit representations, and passes the bits up to the data link
   layer as a complete frame.

### The TCP/IP Protocol Model

    describes the communication process in terms of the TCP/IP protocol suite
    and the way it functions.

It is important to know the TCP/IP model to understand how the process is
implemented in current networks.

##### Layers

The TCP/IP model for internetwork communications is referred to as the
**internet model**.

The TCP/IP model defines the four communication functions that protocols
perform:

<table class="table">
  <thead>
    <tr>
      <th scope="col">#</th>
      <th scope="col">Layer Name</th>
      <th scope="col">Protocols</th>
      <th scope="col">Functional Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">4</th>
      <td>Application</td>
      <td>DNS, BOOTP, DHCP, SMTP, POP, FTP, TFTP, HTTP</td>
      <td>
        Represents application data to the user.<br />e.g. the HTTP protocol
        presents data to the user in a web browser application like Firefox.
      </td>
    </tr>
    <tr>
      <th scope="row">3</th>
      <td>Transport</td>
      <td>UDP, TCP</td>
      <td>
        Supports communication between various devices across diverse networks
        and performs error correction.
      </td>
    </tr>
    <tr>
      <th scope="row">2</th>
      <td>Internet</td>
      <td>IP, NAT, ICMP, OSPF, EIGRP</td>
      <td>
        Finds the best path through the network
      </td>
    </tr>
    <tr>
      <th scope="row">1</th>
      <td>Network Access</td>
      <td>ARP, PPP, Ethernet, Interface Drivers</td>
      <td>
        Controls the hardware devices and media that make up the network.
      </td>
    </tr>
  </tbody>
</table>

##### Communication Process

1. Creation of data at the application layer of the originating source host.
1. Segmentation and encapsulation of data as it passes down the protocol stack
   in the source host.
1. Generation of the data onto the media at the network access layer of the
   stack.
1. Transportation of the data through the internetwork, which consists of media
   and any intermediary devices.
1. Reception of the data at the network access layer of the destination host.
1. De-capsulation and reassembly of the data as it passes up the stack in the
   destination host.
1. Passing this data to the destination application at the application layer of
   the destination host.

### Model Comparision

    The key similarities are in the transport and network layers; however, the
    two models differ in how they relate to the layers above and below each
    layer.


The protocols that make up the TCP/IP protocol suite can also be described in
terms of the OSI reference model. In the OSI model, the network access layer and
the application layer of the TCP/IP model are further divided to describe
discrete functions that must occur at these layers.

At the network access layer, the TCP/IP protocol suite does not specify which
protocols to use when transmitting over a physical medium; it only describes the
handoff from the internet layer to the physical network protocols. OSI Layers 1
and 2 discuss the necessary procedures to access the media and the physical
means to send data over a network.

OSI Layer 3, the network layer, maps directly to the TCP/IP Internet layer. This
layer is used to describe protocols that address and route messages through an
internetwork.

OSI Layer 4, the transport layer, maps directly to the TCP/IP Transport layer.
This layer describes general services and functions that provide ordered and
reliable delivery of data between source and destination hosts.

The TCP/IP application layer includes a number of protocols that provide
specific functionality to a variety of end user applications. The OSI model
Layers 5, 6, and 7 are used as references for application software developers
and vendors to produce products that operate on networks.

Both the TCP/IP and OSI models are commonly used when referring to protocols at
various layers. Because the OSI model separates the data link layer from the
physical layer, it is commonly used when referring to these lower layers.
