+++
date = 2021-10-25T00:19:48+09:30
title = "Network - Rules of Communication"
slug = "network-rules-of-communication"
aliases = "network-rules-of-communication"
description = "Network - Rules of Communication"
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

1. [Communication Fundamentals](#communication-fundamentals)
1. [Rule Establishment](#rule-establishment)
1. [Message Encoding](#message-encoding)
1. [Message Formatting and Encapsulation](#message-formatting-and-encapsulation)
1. [Message Size](#message-size)
1. [Message Timing](#message-timing)
    1. [Access Method](#access-method)
    1. [Flow Control](#flow-control)
    1. [Response Timeout](#response-timeout)
1. [Message Delivery Options](#message-delivery-options)
    1. [Unicast (one-to-one)](#unicast-one-to-one)
    1. [Multicast (one-to-many)](#multicast-one-to-many)
    1. [Broadcast (one-to-all)](#broadcast-one-to-all)

### Communication Fundamentals

A network can be as complex as devices connected across the Internet, or as
simple as two computers directly connected to one another with a single cable,
and anything in-between. Networks can vary in size, shape, and function.
However, simply having a wired or wireless physical connection between end
devices is not enough to enable communication. For communication to occur,
devices must know "how" to communicate.

People exchange ideas using many different communication methods. However,
regardless of the method chosen, all communication methods have three elements
in common.

1. The message source, or sender. The source are people, or electronic devices,
   that need to send a message to other individuals or devices.
1. The message destination, or receiver, of the message. The destination
   receives the message and interprets it.
1. A channel, consists of the media that provides the pathway over which the
   message travels from source to destination.

Communication begins with a message, or information, that must be sent from a
source to a destination. The sending of this message, whether by face-to-face
communication or over a network, is governed by rules called **protocols**.
These protocols are specific to the type of communication method occurring.

### Rule Establishment

Before communicating with one another, individuals must use established rules or
agreements to govern the conversation. These rules, or protocols, must be
followed in order for the message to be successfully delivered and understood.

Protocols must account for the following requirements:

1. An identified sender and receiver
1. Common language and grammar
1. Speed and timing of delivery
1. Confirmation or acknowledgement requirements

The protocols used in network communications share many of these fundamental
traits. In addition to identifying the source and destination, computer and
network protocols define the details of how a message is transmitted across a
network.

Common computer protocols include the following requirements:

1. Message Encoding
1. Message Formatting and Encapsulation
1. Message Size
1. Message Timing
1. Message Delivery Options

### Message Encoding

    Encoding is the process of converting information into another acceptable
    form, for transmission.
    Decoding reverses this process in order to interpret the information.

Encoding between hosts must be in an appropriate format for the medium. Messages
sent across the network are first converted into bits by the sending host. Each
bit is encoded into a pattern of sounds, light waves, or electrical impulses
depending on the network media over which the bits are transmitted. The
destination host receives and decodes the signals in order to interpret the
message.

### Message Formatting and Encapsulation

    Message formats, or structures, depend on the type of message and the
    channel that is used to deliver the message.

A message sent over a computer network follows specific format rules for it to
be delivered and processed. Just as a letter is encapsulated in an envelope for
delivery, so too are computer messages. Each computer message is
[encapsulated](https://www.oxfordlearnersdictionaries.com/definition/english/encapsulate?q=encapsulate)
in a specific format, called a **frame**, before it is sent over the network. A
frame, acting like an envelope, provides the address of the destination and the
address of the source host.

The format and contents of a frame are determined by the type of message being
sent and the channel over which it is communicated. Messages that are not
correctly formatted are not successfully delivered to or processed by the
destination host.

### Message Size

    When a long message is sent from one host to another over a network, it is
    necessary to break the it into smaller pieces.

The rules that govern the size of the pieces, or frames, communicated across the
network are very strict. They can also be different, depending on the channel
used. Frames that are too long or too short are not delivered.

The size restrictions of frames require the source host to break a long message
into individual pieces that meet both the minimum and maximum size requirements.
The long message will be sent in separate frames, with each frame containing a
piece of the original message. Each frame will also have its own addressing
information. At the receiving host, the individual pieces of the message are
reconstructed into the original message.

### Message Timing

    affects how well a message is received and understood.

##### Access Method

    determines when someone is able to send a message.

If two people talk at the same time, a collision of information occurs and it is
necessary for the two to back off and start again. Likewise, it is necessary for
computers to define an access method for hosts on a network to know when to
begin sending messages and how to respond when collisions occur.

For example, when a device wants to transmit on a wireless LAN, it is necessary
for the WLAN network interface card (NIC) to determine whether the wireless
medium is available.

##### Flow Control

    prevents packets from being dropped because too much data is being sent too
    quickly.

Timing affects how much information can be sent and the speed that it can be
delivered. If one person speaks too quickly, it is difficult for the other
person to hear and understand the message. In network communication, source and
destination hosts use flow control methods to negotiate correct timing for
successful communication.

##### Response Timeout

    specifies how long to wait for responses and what action to take if a
    response timeout occurs.

If a person asks a question and does not hear a response within an acceptable
amount of time, the person assumes that no answer is coming and reacts
accordingly. The person may repeat the question, or may go on with the
conversation. Hosts on the network also have rules that specify how long to wait
for responses and what action to take if a response timeout occurs.

### Message Delivery Options

    A message can be sent a single individual, to a group at the same
    time, or even to all people in the same area.

There are also times when the sender of a message needs to be sure that the
message is delivered successfully to the destination. In these cases, it is
necessary for the recipient to return an **acknowledgment** to the sender. If no
acknowledgment is required, the delivery option is referred to as
**unacknowledged**.

##### Unicast (one-to-one)

    Information is being transmitted to a single host or destination.

##### Multicast (one-to-many)

    Information is being transmitted to a group of hosts or destinations
    simultaneously.

##### Broadcast (one-to-all)

    Information is being transmitted to all hosts simultaneously.

Some protocols use a special multicast message that is sent to all devices,
making it essentially the same as a broadcast.

Hosts may be required to acknowledge the receipt of some messages while not
needing to acknowledge others.
