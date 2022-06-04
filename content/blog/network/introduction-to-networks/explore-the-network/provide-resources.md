+++
date = 2021-10-11T20:54:40+09:30
title = "Network - Provide Resources"
slug = "provide-resources-in-a-network"
aliases = "provide-resources-in-a-network"
description = "Network - Provide Resources"
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

1. [Network of Many Sizes](#network-of-many-sizes)
    1. [Small Home Networks](#small-home-networks)
    1. [Small Office/Home Office (SOHO)
    Networks](#small-officehome-office-soho-networks)
    1. [Medium to Large Networks](#medium-to-large-networks)
    1. [World Wide Networks](#world-wide-networks)
1. [Clients and Servers](#clients-and-servers)
    1. [Host Roles](#host-roles)
    1. [Servers](#servers)
    1. [Clients](#clients)
    1. [Examples](#examples)
1. [Peer-to-Peer (P2P) Networking](#peer-to-peer-networking)

### Network of Many Sizes

Networks come in all sizes, ranging from simple networks consisting of two
computers to complex ones connecting millions of devices.

##### Small Home Networks

    connect a few computers to one another and to the internet.

Simple networks installed in homes enable sharing of resources, such as
printers, documents, pictures and music between a few local computers.

##### Small Office/Home Office (SOHO) Networks

    allow computers in a home office or a remote office to connect to a
    corporate network, or access centralised, shared resources.

Home office networks and small office networks are often set up by individuals
that work from a home or a remote office and need to connect to a corporate
network or other Centralised resources. Additionally, many self-employed
entrepreneurs use home office and small office networks to advertise and sell
products, order supplies and communicate with customers.

##### Medium to Large Networks

    can have many locations with hundreds or thousands of interconnected hosts.

In businesses and large organisations, networks can be used on an even broader
scale to provide consolidation, storage, and access to information on network
servers. Networks also allow for rapid communication such as email, instant
messaging, and collaboration among employees. In addition to internal benefits,
many organisations use their networks to provide products and services to
customers through their connection to the Internet.

##### World Wide Networks

    (Internet) - a network of networks that connects hundreds of millions of
    computers world-wide.

The Internet is the largest network in existence. In fact, the term Internet
means a 'network of networks'. The Internet is literally a collection of
interconnected private and public networks, such as those described above.

### Clients and Servers

##### Host Roles

In order for a computer to be a part of a global online community, it first must
be connected to a network which then must be connected to the Internet.
- All computers connected to a network and participate directly in network
  communication (send or receive messages on the network) are classified as
  **nodes**, **hosts**, or **end devices**.
- In modern networks, a host can act as a client, a server, or both. The
  software installed on the computer determines which role the host plays.

##### Servers

    hosts with software installed that enable them to provide information, like
    email or web pages, to other hosts on the network.

1. A server can provide services to one or many clients simultaneously.
1. Each service requires separate server software.
1. For example, a server requires web server software in order to provide web
   services to the network.
1. Additionally, a single host can run multiple types of server software.

In a home or small business, it may be necessary for one computer to act as a
file server, a web server, and an email server.

##### Clients

    hosts with software installed that enable them to request and display the
    information obtained from the server.

1. A client can can connect to multiple servers or request multiple services
   simultaneously.
1. Each service requires separate client software.
1. For example, a client requires web client software, such as Firefox, in order
   to access any website through the Internet.
1. Additionally, a single host can run multiple types of client software.

For example, a user can check emails and view a web page while instant messaging
and listening to Internet radio.

##### Examples

| Software | Server                                                                 | Client                                                                                         |
| --       | --                                                                     | --                                                                                             |
| Email    | The Email Server runs email server software.                           | Clients use mail client software, such as Microsoft Outlook, to access email on the server.    |
| Web      | The Web Server runs web server software.                               | Clients use browser software, such as Firefox, to access web pages on the server.              |
| File     | The File Server stores corporate and user files in a central location. | The client devices access these files with file management software, such as Windows Explorer. |

### Peer-to-Peer (P2P) Networking

    One computer functions as both servers and clients on the network.

Client and server software usually runs on separate computers, but it is also
possible for one computer to carry out both roles at the same time on the
network, usually in small businesses and homes. This type of network is called a
peer-to-peer (P2P) network.

In a P2P network, each node on the network can communicate directly with every
other node on the network. Thus, all nodes are peers (equals).

The simplest P2P network consists of two directly connected computers using a
wired or wireless connection.

Multiple computers can also be connected to create a larger P2P network, but
this requires a network device, such as a hub, to interconnect the computers.

| Advantages                                                                   | Disadvantages                                                                    |
| --                                                                           | --                                                                               |
| Easy to set up                                                               | No centralised administration
| Less complexity                                                              | Not as secure
| Lower cost since network devices and dedicated servers may not be required   | Not scalable
| Can be used for simple tasks such as transferring files and sharing printers | All devices may act as both clients and servers which can slow their performance
