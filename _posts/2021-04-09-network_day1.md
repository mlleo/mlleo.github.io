---
title: "[Network] Transport Layer 1"
categories: 
  - CS
tags:
  - Computer Network
last_modified_at: 2020-12-15 12:00:00
comments: true
use_math: true # MathJax On
---

Transport Layer 1

#### Transport services and protocols

- logical communication between application processes running on different hosts(end system)
- Sender : breaks application messages into segments (packets) and passes to network layer
- Receiver : reassembles segments into messages, passes to application layer
- Protocol : TCP, UDP, SCTP, DCCP

![transport1](https://user-images.githubusercontent.com/62474292/114241439-1632cd80-99c4-11eb-8ef8-5c006a6c4cda.png)


- Reliable, in-order delivery : TCP
  - Congestion control (control data flow even if application layer try to send lots of data)
  - Flow control (send data to receiver as they can receive)
  - Connection setup

- Unreliable, unordered delivery : UDP
  - Just send data between processes

- Services not available
  - Delay guarantees (network layer problem)
  - Bandwidth gurantees (network layer problem)

![transport2](https://user-images.githubusercontent.com/62474292/114241607-63af3a80-99c4-11eb-84d6-0be0a9a3a4f6.JPG)


