+++
date = 2021-10-28T23:27:09+09:30
title = "Network - Data Transfer"
slug = "network-data-transfer"
aliases = "network-data-transfer"
description = "Data Transfer in the Network"
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

1. [Message Segmentation](#message-segmentation)
    1. [Advantages](#advantages)
    1. [Disadvantages](#disadvantages)
1. [Protocol Data Units (PDU)](#protocol-data-units-pdu)
1. [Sending and Receiving Process](#sending-and-receiving-process)
    1. [Sending a Message](#sending-a-message)
    1. [Receiving a Message](#receiving-a-message)
1. [Encapsulation Example](#encapsulation-example)
1. [Network Addresses and Data Link
   Addresses](#network-addresses-and-data-link-addresses)
    1. [Layer 3 Logical Addresses](#layer-3-logical-addresses)
    1. [Layer 2 Physical Addresses](#layer-2-physical-addresses)

<!-- vim-markdown-toc -->

### Message Segmentation

In theory, a single communication, such as a music video or an email message,
could be sent across a network from a source to a destination as one massive,
uninterrupted stream of bits. If messages were actually transmitted in this
manner, it would mean that no other device would be able to send or receive
messages on the same network while this data transfer was in progress. These
large streams of data would result in significant delays. Further, if a link in
the interconnected network infrastructure failed during the transmission, the
complete message would be lost and have to be retransmitted in full.

A better approach is to divide the data into smaller, more manageable pieces to
send over the network. This division of the data stream into smaller pieces is
called **segmentation**.

##### Advantages

1. By sending smaller individual pieces from source to destination, many
   different conversations can be interleaved on the network, called
   multiplexing.
   - *Multiplexing*: the segment of more than two messages shuffle into each
     other and share the medium.
1. Segmentation can *increase the efficiency of network communications*. If part
of the message fails to make it to the destination, due to failure in the
network or network congestion, only the missing parts need to be retransmitted.

##### Disadvantages

The challenge to using segmentation and multiplexing to transmit messages across
a network is the *level of complexity that is added to the process*. Imagine if
you had to send a 100-page letter, but each envelope would only hold one page.
The process of addressing, labeling, sending, receiving, and opening the entire
100 envelopes would be time-consuming for both the sender and the recipient.

In network communications, each segment of the message must go through a similar
process to ensure that it gets to the correct destination and can be reassembled
into the content of the original message.

### Protocol Data Units (PDU)

As application data is passed down the protocol stack on its way to be
transmitted across the network media, various protocol information, or *control
information*, is added at each level. This is known as the **encapsulation**
process.

The form that a piece of data takes at any layer is called a **protocol data
unit (PDU)**. During encapsulation, each succeeding layer encapsulates the PDU
that it receives from the layer above in accordance with the protocol being
used.

At each stage of the process, a PDU has a different name to reflect its new
functions. Since there is no universal naming convention for PDUs, the PDUs
are named according to the protocols of the TCP/IP suite.

    Mnemonic: Do Some People Fear Binary?

<table class="table">
  <thead>
    <tr>
      <th scope="col">#</th>
      <th scope="col">PDU Name</th>
      <th scope="col">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">1</th>
      <td>Data</td>
      <td>Application layer PDU</td>
    </tr>
    <tr>
      <th scope="row">2</th>
      <td>Segment</td>
      <td>Transport layer PDU</td>
    </tr>
    <tr>
      <th scope="row">3</th>
      <td>Packet (or Datagram)</td>
      <td>Internet layer PDU</td>
    </tr>
    <tr>
      <th scope="row">4</th>
      <td>Frame (medium dependent)</td>
      <td>Data link layer PDU</td>
    </tr>
    <tr>
      <th scope="row">5</th>
      <td>Bits</td>
      <td>
        Physical layer PDU<br />Used for the physical transmission of binary
        data over the medium
      </td>
    </tr>
  </tbody>
</table>

### Sending and Receiving Process

The common task of sending an e-mail has many steps in the process.

##### Sending a Message

When sending messages on a network, the encapsulation process works from top to
bottom. At each layer, the upper layer information is considered data within the
encapsulated protocol. For example, the TCP segment is considered data within
the IP packet.

1. An end user, using an e-mail application, creates data. The **application
   layer** codes the data as e-mail and sends the data to the transport layer.
1. The message is segmented for transport. The **transport layer** adds control
   information in a header so that it can be assigned to the correct process and
   all segments put into proper order at the destination. The segment is sent
   down to the internet layer.
1. The **internet layer** adds IP addressing information in an IP header. The
   segment is now an addressed packet that can be handled by routers en route to
   the destination. The internet layer sends the packet down to the network
   access layer.
1. The **network access layer** creates an Ethernet frame with local network MAC
   address information in the header. This enables the packet to get to the
   local rout and out to the web. The frame also contains a trailer with
   error-checking information. After the frame is created, it is encoded into
   bits and sent onto the media to the destination.

##### Receiving a Message

This process is reversed at the receiving host, and is known as
de-encapsulation. **De-encapsulation** is the process used by a receiving device
to remove one or more of the protocol headers. The data is de-encapsulated as it
moves up the stack toward the end-user application.

1. The frame is de-encapsulated to a packet, then to a segment, and then the
   **transport layer** puts all segments into the proper order.
1. When all data has arrived and is ready, it is sent to the **application
   layer**, and then the original application data goes to the receiver’s e-mail
   application.

### Encapsulation Example

In the web server example, we can use the TCP/IP model to illustrate the process
of sending an HTML web page to a client.

1. The application layer protocol, HTTP, begins the process by delivering the
   HTML formatted web page data to the transport layer. There the application
   data is broken into TCP segments.
1. Each TCP segment is given a label, called a **header**, containing
   information about which process running on the destination computer should
   receive the message.
   - It also contains the information that enables the destination process to
     reassemble the data back to its original format.
1. The transport layer encapsulates the web page HTML data within the segment
and sends it to the internet layer, where the IP protocol is implemented.
1. Here the entire TCP segment is encapsulated within an IP packet, which adds
another label, called the IP header.
1. The IP header contains source and destination host IP addresses, as well as
information necessary to deliver the packet to its corresponding destination
process.
1. Next, the IP packet is sent to the network access layer where it is
encapsulated within a frame header and trailer.
    - Each frame header contains a source and destination physical address.
    - The physical address uniquely identifies the devices on the local network.
    - The trailer contains error-checking information.

Finally the bits are encoded onto the media by the server network interface card
(NIC).

### Network Addresses and Data Link Addresses

The network and data link layers are responsible for delivering the data from
the source device to the destination device. Protocols at both layers contain a
source and destination address, but their addresses have different purposes.

- **Network layer source and destination addresses** - responsible for
  delivering the IP packet from the original source to the final destination,
  either on the same network or to a remote network.
- **Data link layer source and destination addresses** – responsible for
  delivering the data link frame from one network interface card (NIC) to
  another NIC on the same network.

##### Layer 3 Logical Addresses

An IP packet contains two IP addresses:

- **Source IP address** - the IP address of the sending device, the original
  source of the packet.
- **Destination IP address** - the IP address of the receiving device, the final
  destination of the packet.
  - Used by routers to forward a packet to its destination.

The network layer addresses, or (layer 3) IP addresses, indicate the original
source and final destination. An IP address contains two parts:

1. **Network prefix** - the left-most part of the address that indicates which
   network the IP address is a member. All devices on the same network will have
   the same network portion of the address.
    - Used by routers to forward the packet to the proper network.
1. **Host part** - The remaining part of the address that identifies a specific
device on the network. The host portion is unique for each device on the
network.
    - used by the last router in the path to deliver the packet to the
      destination device.

When the sender and receiver of the IP packet are on the same network, the
network portion of both the source IP address and destination IP address are the
same.

When the sender of the packet is on a different network from the receiver, the
source and destination IP addresses will represent hosts on different networks.
This will be indicated by the network portion of the IP address of the
destination host.

##### Layer 2 Physical Addresses

As the IP packet travels from host-to-router, router-to-router, and finally
router-to-host, at each point along the way the IP packet is encapsulated in a
new data link frame.

A data link frame contains two data link addresses.

1. **Source data link address** - the physical address of the device’s NIC that
   is sending the data link frame.
1. **Destination data link address** - the physical address of the device's NIC
   that is receiving the data link frame.
   - This address is either the next hop router or of the final destination
     device.

The layer 2, data link protocol is only used to deliver the packet from
NIC-to-NIC on the same network. The router removes the layer 2 information as it
is received on one NIC and adds new data link information before forwarding out
the exit NIC on its way towards the final destination.

When the sender and receiver of the IP packet are on the same network, the data
link frame is sent directly to the receiving device. On an Ethernet network, the
data link addresses are known as Ethernet (Media Access Control) addresses. MAC
addresses are physically embedded on the Ethernet NIC.

1. **Source MAC address** - this is the data link address, or the Ethernet MAC
   address, of the device that sends the data link frame with the encapsulated
   IP packet. The MAC address of the Ethernet NIC of PC1 is AA-AA-AA-AA-AA-AA,
   written in hexadecimal notation.
1. **Destination MAC address** - when the receiving device is on the same
   network as the sending device, this is the data link address of the receiving
   device. In this example, the destination MAC address is the MAC address of
   the FTP server: CC-CC-CC-CC-CC-CC, written in hexadecimal notation.

When the sender and receiver of the IP packet are on different networks, the
Ethernet data link frame cannot be sent directly to the destination host because
the host is not directly reachable in the network of the sender. The Ethernet
frame must be sent to another device known as the *router* or *default gateway*.

- **Source MAC address** - the Ethernet MAC address of the sending device.
- **Destination MAC address** - when the receiving device, the destination IP
  address, is on a different network from the sending device, the sending device
  uses the Ethernet MAC address of the default gateway or router.

The Ethernet frame with the encapsulated IP packet can now be transmitted to the
default gateway. The default gateway forwards the packet to the destination.
This may mean that the default gateway forwards the packet to another router or
directly to destination host if the host is on a network connected to the
default gateway.

It is important that the IP address of the default gateway be configured on each
host on the local network. All packets to a destination on remote networks are
sent to the default gateway.
