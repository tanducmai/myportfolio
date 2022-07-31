+++
date = 2022-07-25T21:25:28+09:30
title = "CIA Triad"
slug = "cia-triad"
aliases = "cia-triad"
description = "CIA Triad"
thumbnail = "images/tn.png"
tags = [
    "security",
]
categories = [
    "security",
]
draft = false
+++

### Table of Contents

<!-- vim-markdown-toc GFM -->

1. [Definition](#definition)
1. [Confidentiality](#confidentiality)
1. [Integrity](#integrity)
1. [Availability](#availability)
1. [How a Hacker sees a network](#how-a-hacker-sees-a-network)
    1. [Confidentiality](#confidentiality-1)
    1. [Integrity](#integrity-1)
    1. [Availability](#availability-1)
1. [How an Admin sees a network](#how-an-admin-sees-a-network)
    1. [Confidentiality](#confidentiality-2)
    1. [Integrity](#integrity-2)
    1. [Availability](#availability-2)

<!-- vim-markdown-toc -->

### Definition

    Confidentiality, Integrity and Availability, aka the CIA triad, is a model
    designed to guide policies for information security within an organisation.

The Goal of the Triad?

    when we want to protect a network and the data contained within it.

The How?

    use a security model like the CIA Triad to design our security plan.

### Confidentiality

    ability of a system to ensure that the information asset is viewed only by
    authorised entities.

Providing this assurance can be described using three major steps:

**Step 1**

Information must have controls that are capable of preventing some users from
accessing the information.

These controls must be sufficiently
[granular](https://www.merriam-webster.com/dictionary/granular) depending on the
rationale for the access control. The requirement for granularity is based
partially on technical requirements and partially on benefits to the business.

Examples of how to achieve Confidentiality:

1. Data at rest and in transit uses data encryption
1. Access Control Lists
1. Non technical – Physical Security
1. Role-based access control (RBAC)

Risks to Confidentiality:

1. Privilege Escalation
1. Employee Negligence
1. Bring your own device (BYOD)
1. Man in the Middle Attacks (MITM Attack)
   [:link:](https://www.csoonline.com/article/3340117/man-in-the-middle-attack-definition-and-examples.html)

**Step 2**

It must be possible to limit access to information to authorised users.

Authorisation is defined as:

    access privileges granted to a user, program, or process or the act of
    granting those privileges.

**Step 3**

An authentication system must be in place to validate the identity of those
requesting access to data.

Authentication is defined as:

    the process of verifying the identity or other attributes claimed by or
    assumed of an entity (user, process, or device), or to verify the source and
    integrity of data.

Authentication generally prefaces authorisation decisions (i.e. the system must
identify the user before it can determine which authorisations the user holds).

Examples:

1. Biometrics
1. 2FA / MFA - the best way to secure any network, yet it is difficult
   (time-consuming) to implement.
1. Something you know (username/password)
1. Something you have (smart card)
1. Something you are (fingerprint)

Risks:

1. Social Engineering
1. Phishing
1. Shoulder Surfing
1. Theft

### Integrity

    ability of a system to ensure that the information asset is modified only by
    authorised entities.

A more comprehensive definition is:

    guarding against improper information modification or destruction, and
    includes ensuring information non-repudiation and authenticity.

Data is commonly made available for viewing by users, however they should not
have the ability to change the data. Your course grades on the student portal is
an example.

Questions to ask could be:

1. How correct is the information sent and/or received?
1. Has the data been modified during transit, retrieval, or at rest?
1. If data has been modified without permission, do you have
   **non-repudiation**?

    Assurance the sender of data is provided with proof of delivery and the
    recipient is provided with proof of the sender's identity, so neither can
    later deny having processed the information.

Example – Hacker imitates a lecturer to request a grade change for a student.

So what can be used to guarantee the correctness of data? Hashing can be used.
Here are three examples:

**MD5**

    An MD5 hash function encodes a string of information and encodes it into a
    128-bit fingerprint.

MD5 is often used as a checksum to verify data integrity. However, due to its
age, MD5 is also known to suffer from extensive hash collision vulnerabilities,
but it is still one of the most widely used algorithms in the world.

For example, Cisco routers clear text password:

    enable password cisco123

The same password hashed using the MD5 hash:

    enable secret 5 $1$mERr$5.a6P4JqbNiMKOlusIfka/

**SHA-2**

    developed by the National Security Agency (NSA); a cryptographic hash
    function.

The SHA-2 family consists of six hash functions with digests (hash values) that
are 224, 256, 384 or 512 bits.

Is it secure? Here is the hash value for [Password123].

    008c70392e3abfbd0fa47bbc2ed96aa99bd49e159727fcba0f2e6abeb3a9d601

Copy the hash above and paste it into this [website](https://md5decrypt.net/en/Sha256/).

**CRC32**

    a cyclic redundancy check (CRC) is an error-detecting code often used for
    detection of accidental changes to data.

Cyclic Redundancy Check is a number mathematically calculated for a packet by
its source computer, and then recalculated by the destination computer. If the
original and recalculated versions at the destination computer differ, the
packet is corrupt and needs to be resent or ignored.

### Availability

    ability of a system to ensure that the information asset is always
    accessible and useable upon the demand of authorised entities.

There is limited utility in having a confidential and integral system if it is
not available to authorised users.

This is the reason that '[pulling the
plug](https://dictionary.cambridge.org/dictionary/english/pull-the-plug)' during
a cyberattack is rarely an option.

**Denial-of-service (DoS) attacks**, and its variants, are one of the most
common attacks that affect availability.

Examples of how to provide Availability:

1. Increase redundancy
1. Backup strategies
1. Disaster recovery plan

Risks to availability:

1. Hardware Failure
1. Denial-of-service (DoS) attacks
1. Distributed denial-of-service (DDoS) attacks

### How a Hacker sees a network

##### Confidentiality

1. **Packet Capturing** - These tools allow the attacker to view the data passing
   across a network [Ten Packet Sniffers](https://www.dnsstuff.com/packet-sniffers).
    - Packet Capture (sniffer) video - [Packet Sniffers](https://www.youtube.com/watch?v=r0l_54thSYU)
    - Learn Wireshark - [Wireshark Tutorial](https://www.youtube.com/watch?v=lb1Dw0elw0Q)
1. **Keylogging** - Installing a key logger will allow an attacker to attempt to
   capture login credentials [Key Logging Tool](https://www.offensive-security.com/metasploit-unleashed/keylogging/).
    - Key Logging video - [Key Logging](https://www.youtube.com/watch?v=L8169DHNeQ0)
1. **Access files** - Once within a target system the attacker will attempt to
   locate sensitive files.
1. **Exfiltrate Data** - Once data has been identifed the attacker could choose to
   exfiltrate for offsite inspection.
1. **Delete data** - If the attackers intent is disruption then they may choose to
   delete discovered files.

##### Integrity

1. **Encrypt data** - If the intent is Ransomware an attacker may encrypt data
   and demand a ransom for the decryption keys. Ransomware defined -
   [Ransomware](https://www.youtube.com/watch?v=Vkjekr6jacg)
1. **Man-in-the-middle attacks** - An attacker will place themselves between two
   hosts and capture the data flow. ARP Poisoning (Man-In-The-Middle Attack) -
   [MITM Attack](https://www.youtube.com/watch?v=A7nih6SANYs)
1. **Delete data** - A form of denial of service can be the attacker deleting or
   threatening to delete data.

##### Availability

1. **Disrupt services (DoS, DDoS)** - any attack that prevents legitimate users
   of a resource from accessing that resource. Can be performed by bandwidth
   saturation (flooding) or service disruption.
    - Denial Of Service Explained - [Denial of Service](https://www.youtube.com/watch?v=YcH7qx6HTII)
1. **Deny access (Account manipulation)** - Stealing or changing a users login
   details to prevent access.

### How an Admin sees a network

##### Confidentiality

1. **Protect data** - From the perspective of the CIA Triad this would involve
   encrypting data both at rest and in transit. If an attacker were to gain
   access the encryption would render the data unreadable unless they had the
   relevant decryption keys.
    - Data at Rest [article](https://en.wikipedia.org/wiki/Data_at_rest)
    - Data in Transit [article](https://en.wikipedia.org/wiki/Data_in_transit)
1. **Restrict access** - A big part of providing confidentiality of data is
   controlling who has access to it. Providing access to only those who are
   authorised to use it and need to use it. This can be achieved through strong
   share permissions and multifactor authentication.

##### Integrity

1. **Backup data** - A backup is the process of making a copy of your systems
   data and storing it on a separate device, drive or physical location. A
   backup will protect your data from attacks on the integrity of your
   information. If an attack on integrity was to be performed and the data was
   encrypted a simple restore will mitigate the impact.
1. **Restore plan** - Data restoration is the process of retrieving the
   encrypted, lost or corrupted data from your storage, media or files. A
   restore plan must be in place and tested to ensure it restores correctly and
   in a timely manner.
1. **Update** - System or software update are critical in patching potential
   security holes in Operating Systems and applications. Left unpatched an
   application or OS could leave an open door into your network via exploits or
   vulnerabilities.

##### Availability

1. **Firewalls** - Watch this video for a simple explanation on what a Firewall
   does. [The Firewall](https://www.youtube.com/watch?v=5geL5yHpa2Q)
1. **IDS** - Watch the following video on Intrusion Detection Systems work, both
   Host based and Network Based. [The
   IDS](https://www.youtube.com/watch?v=YTWO7Q5iWzE)
1. **DDoS Protection Services** - DDoS mitigation refers to the technique of
   protecting a targeted service or network from a distributed denial-of-service
   (DDoS) attack. By deploying specially designed network equipment or a
   cloud-based protection service, a targeted victim is able to mitigate the
   threat.
1. **Pen Test** - Known as a Penetration test this form of auditing a network is
   designed to identify any "holes" in your network's perimeter. A specially
   trained ethical hacker will run a series of test to see if there are any
   vulnerabilities on the network and report back the results.
