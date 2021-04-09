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

#### Multiplexing
- handle data from multiple sockets, add transport header

#### Demultiplexing
- use header info to deliver received segments to correct socket 

![multi](https://user-images.githubusercontent.com/62474292/114242284-960d6780-99c5-11eb-9d27-47f668ea5b3d.png)

#### How demultiplexing works
- Host receives IP datagrams
  - Each datagram has source IP address, destination IP address
  - Each datagram carries one transport-layer segment
  - Each segment has source(who send), destination(who receive) port numbers
- Host uses IP addresses(which computer) & port numbers(which process) to direct segment to appropriate socket 

![segment](https://user-images.githubusercontent.com/62474292/114242675-42e7e480-99c6-11eb-84e7-bc35ba721a60.png)

#### Reliable data transfer

![rdt](https://user-images.githubusercontent.com/62474292/114243055-e638f980-99c6-11eb-87f3-4fe525b13382.png)

- Sender side
![sender](https://user-images.githubusercontent.com/62474292/114243256-3adc7480-99c7-11eb-9fdc-c4fde94b292c.png)

  - rdt_send() : called from above(application layer), passed data to deliver to receiver upper layer
  - udt_send() : called by rdt, to transfer packet over unreliable channel to receiver
- Receiver side
![receiver](https://user-images.githubusercontent.com/62474292/114243261-3b750b00-99c7-11eb-85cb-63641cd96019.png)

  - deliver_data() : called by rdt to deliver data to upper
  - rdt_rcv(): called when packet arrives on rcv_side of channel
  
