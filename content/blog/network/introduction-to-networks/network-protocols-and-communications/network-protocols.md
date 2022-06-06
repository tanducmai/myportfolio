+++
date = 2021-10-26T18:32:44+09:30
title = "Network - Protocols"
slug = "network-protocols"
aliases = "network-protocols"
description = "Network Protocols"
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

1. [Protocols](#protocols)
    1. [Protocol Suite](#protocol-suite)
    1. [Protocol Stack](#protocol-stack)
    1. [Network Protocols](#network-protocols)
1. [Protocol Interaction](#protocol-interaction)
    1. [HTTP](#http)
    1. [TCP](#tcp)
    1. [IP](#ip)
    1. [Ethernet](#ethernet)
1. [Communication Process](#communication-process)

<!-- vim-markdown-toc -->

### Protocols

    rules that govern communications.

Protocols define standardised formats for data packets, techniques for detecting
and correcting errors, and so on.

##### Protocol Suite

    a set of protocols that work together to provide comprehensive network
    communication services.

Protocol suites are implemented by hosts and networking devices in software,
hardware, or both.

One of the best ways to visualise how the protocols within a suite interact is
to view the interaction as a stack.

##### Protocol Stack

    shows how the individual protocols within a suite are implemented.

The protocols are viewed in terms of **layers**, with each higher level service
depending on the functionality defined by the protocols shown in the lower
levels. The lower layers of the stack are concerned with moving data over the
network and providing services to the upper layers, which focus on the content
of the message being sent.

##### Network Protocols

    define a common format and set of rules for exchanging messages between
    devices.

Some common networking protocols:

- Hypertext Transfer Protocol (HTTP)
- Transmission Control Protocol (TCP)
- Internet Protocol (IP)

Some processes performed by networking protocols:

- How the message is formatted or structured.
- The process by which networking devices share information about pathways with
  other networks.
- How and when error and system messages are passed between devices.
- The setup and termination of data transfer sessions.

### Protocol Interaction

Communication between a web server and web client is an example of an
interaction between several protocols.

##### HTTP

An application protocol that governs the way a web server and a web client
interact. HTTP defines the content and formatting of the requests and responses
that are exchanged between the client and server. Both the client and the web
server software implement HTTP as part of the application. HTTP relies on other
protocols to govern how the messages are transported between the client and
server.

##### TCP

A transport protocol that manages the individual conversations. TCP divides the
HTTP messages into smaller pieces, called segments. These segments are sent
between the web server and client processes running at the destination host. TCP
is also responsible for controlling the size and rate at which messages are
exchanged between the server and the client.

##### IP

An Internet protocol that is responsible for taking the formatted segments from
TCP, encapsulating them into packets, assigning them the appropriate addresses,
and delivering them to the destination host.

##### Ethernet

A network access protocol that describes two primary functions: communication
over a data link and the physical transmission of data on the network media.
Network access protocols are responsible for taking the packets from IP and
formatting them to be transmitted over the media.

### Communication Process

Let's demonstrate the complete communication process using an example of a web
server transmitting data to a client.

1. The web server preparing the Hypertext Markup Language (HTML) page as data to
   be sent.
2. The application protocol HTTP header is added to the front of the HTML data.
   The header contains various information, including the HTTP version the
   server is using and a status code indicating it has information for the web
   client.
3. The HTTP application layer protocol delivers the HTML-formatted web page data
   to the transport layer. The TCP transport layer protocol is used to manage
   individual conversations, in this example between the web server and web
   client.
4. The IP information is added to the front of the TCP information. IP assigns
   the appropriate source and destination IP addresses. This information is
   known as an IP packet.
5. The Ethernet protocol adds information to both ends of the IP packet, known
   as a data link frame. This frame is delivered to the nearest router along the
   path towards the web client. This router removes the Ethernet information,
   analyzes the IP packet, determines the best path for the packet, inserts the
   packet into a new frame, and sends it to the next neighboring router towards
   the destination. Each router removes and adds new data link information
   before forwarding the packet.
6. This data is now transported through the internetwork, which consists of
   media and intermediary devices.
7. The client receiving the data link frames that contain the data. Each
   protocol header is processed and then removed in the opposite order it was
   added. The Ethernet information is processed and removed, followed by the IP
   protocol information, the TCP information, and finally the HTTP information.
8. The web page information is then passed on to the client’s web browser
   software.
