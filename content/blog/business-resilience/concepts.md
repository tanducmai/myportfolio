+++
date = 2022-07-25T22:43:05+09:30
title = "Concepts"
slug = "business-resilience-concepts"
aliases = "business-resilience-concepts"
description = "Business Resilience Concepts"
thumbnail = "images/tn.png"
tags = [
    "business resilience",
]
categories = [
    "business resilience",
]
draft = false
+++

### Table of Contents

<!-- vim-markdown-toc GFM -->

1. [Business Resilience Definition](#business-resilience-definition)
1. [Business Continuity Definition](#business-continuity-definition)
1. [Information Security in Business Resilience](#information-security-in-business-resilience)
    1. [Confidentiality](#confidentiality)
    1. [Integrity](#integrity)
    1. [Availability](#availability)
1. [Roles and responsibilities](#roles-and-responsibilities)

<!-- vim-markdown-toc -->

### Business Resilience Definition

The term **resilience** is defined as:

    the ability to survive, adapt, and flourish in the face of turbulent change.

Applying this to a business gives us the concept of **business resilience** -

    the ability of a business to withstand, adapt and thrive in the face of
    turbulent change that originates from both internal and external sources as
    well as anticipated or unanticipated events.

A resilient business can adapt to disruptions and keep operating while looking
after its people, assets, and brand equity.

It is important to know that Information Security is not Business Resilience.
Business Resilience drives the need for Information Security as todays
businesses are heavily reliant on technology and the interconnected world we
live in.

We will look at Business Resilience from two different perspectives.

1. **Business Continuity Management System (BCMS)**: a reactive system which
   assumes a threat has occurred and a Business Continuity Plan is in place to
   deal with it.
1. **Information Security Management System (ISMS) - ISO 27001**: a preventative
   plan that does not assume a threat has occurred as yet.

### Business Continuity Definition

    To achieve business resilience, an organisation must be able to resume
    operations in the aftermath of a disaster.

This requires a **business continuity plan** -

    provides procedures for returning critical business functions, the people
    and systems that support them, and the facilities where the work is done to
    a state where the organisation can fulfill its commitments and obligations.

Here is an overview of *Business Continuity*:

1. **Identifying Potential Risks**: Look at the business and decide what are the
   risks to continuity should what you have identified become unavailable.
1. **Understanding Business Impacts**: What impact would an attack or
   significant event have on your assets and the running of the business.
1. **Recovery Time Objectives**: Decide on an acceptable timeframe that critical
   assets are restored.
1. **Incident Response Plan**: An incident response plan is a documented,
   written plan with distinct phases that helps IT professionals and staff
   recognize and deal with a cybersecurity incident.
1. **Organisation-wide Communications**: All user communication is critical to
   keep staff and customers advised on current events.
1. **Dummy Testing**: The testing phase of your plan to see if the implemented
   strategies work.
1. **Timely Updates**: Ensure all systems and software are updated on a regular
   basis.

### Information Security in Business Resilience

It is important to understand that information security is one of the main
concepts to consider when thinking about how to avoid and/or recover from
disaster.

Consider how many businesses are reliant on technology to enable their business
processes. This can include email, banking, ordering, shipping, client accounts,
communications, etc.

Any cybersecurity threat that results in exposure of data also exposes the
company to a significant reputational risk that threatens the company’s ongoing
operations.

Information Security often involves using the [CIA
Triad](https://tanducmai.com/blog/security/cia-triad/) to apply protection
techniques to the information assets of a business.

##### Confidentiality

Applying the tenet of Confidentiality to an asset involves the following techniques:

1. Limiting access through Access Control that uses AAA
    1. Authentication (requires the validation of a users identity)
    1. Authorisation (matches authenticated users to an access level of an
       asset)
    1. Accounting (ensures an action on an asset can be attributed to an
       authenticated identity)
1. Encrypting data in transit and at rest
1. Secure storage
1. End user education on how they should use the data

##### Integrity

Integrity of Information assets is ensuring the asset has not been modified in
transit or at rest.

This can be achieved via:

1. Hashing assets
1. Backup and Restore procedures

##### Availability

Availability means to ensure the information asset is only available to
authorised users as needed.

This can be achieved via:

1. Firewalls
1. Intrusion Detection Systems
1. DDoS protection

### Roles and responsibilities

Information security is no longer the role the sole responsibility of a small,
dedicated group of professional in the company. It is now the responsibility of
all employees.

Following is a brief list of roles in an organisation and their main
responsibilities.

- Chief Information Security Officer (CISO): Primarily responsible for the
  assessment, management, and the implementation of the program that secures the
  organisation’s information.
- Information Security Manager: Accountable for day-to-day operations of the
  infosec program.
- Network Security Engineer: These people take policies or security requirements
  and engineer or design technical solutions that will make these policies an
  enforceable methodology.
- Network Security Analysts: These people mostly analyse logs (log analysis),
  tweak IDS rules, decide when there’s a breach or potential breach and other
  similar functions.
