---
title: "[Network] Transport Layer 2"
categories: 
  - CS
tags:
  - Computer Network
last_modified_at: 2020-12-15 12:00:00
comments: true
use_math: true # MathJax On
---

Transport Layer 2

#### Pipelined protocols
- Sender allows multiple "in-flight", yet-to-be-acknowledged packets
![1](https://user-images.githubusercontent.com/62474292/114246718-45e6d300-99ce-11eb-889f-69a5ac5ee584.png)
![2](https://user-images.githubusercontent.com/62474292/114246725-497a5a00-99ce-11eb-8dae-5b9ab50f9b98.png)

- Go-back-N (sliding window protocol)
  - Sender can have up to N unacked packets in pipeline (if problem happen, then send N packets)
  - Receiver only sends cumulative ACK (Doesn't ack packet if there's a gap)
  - When Receiver receive Out-of-order packet, then discard(don't buffer)
  - Sender has timer for oldest unacked packet (When timer expires, retransmit all unacked packets)
- Selective Repeat
  - Sender can have up to N unacked packets in pipeline
  - Receiver sends individual ack for each packet
  - Sender maintains timer for each unacked packet (When timer expires, retransmit only that unacked packet)

#### Go-back-N
![1](https://user-images.githubusercontent.com/62474292/114248388-834d5f80-99d2-11eb-84e5-fbfcd1194513.JPG)
![2](https://user-images.githubusercontent.com/62474292/114248391-85afb980-99d2-11eb-9961-589a1a05b341.JPG)
![3](https://user-images.githubusercontent.com/62474292/114248392-86e0e680-99d2-11eb-95cb-5f0159d7cdf2.JPG)
![4](https://user-images.githubusercontent.com/62474292/114248393-88121380-99d2-11eb-913a-20a3529ba53e.JPG)
![5](https://user-images.githubusercontent.com/62474292/114248395-89434080-99d2-11eb-8323-2bc43b84308d.JPG)
![6](https://user-images.githubusercontent.com/62474292/114248396-89dbd700-99d2-11eb-813a-778456b40e13.JPG)
![7](https://user-images.githubusercontent.com/62474292/114248398-8a746d80-99d2-11eb-9653-97164413cb50.JPG)

- Scenario
![1](https://user-images.githubusercontent.com/62474292/114248516-d8897100-99d2-11eb-8d49-69a6c0045594.png)
![2](https://user-images.githubusercontent.com/62474292/114248519-d9ba9e00-99d2-11eb-87ae-7341a043ec73.png)

- Window size problem
![1](https://user-images.githubusercontent.com/62474292/114248893-f1465680-99d3-11eb-876f-a87aedbfba75.png)
![2](https://user-images.githubusercontent.com/62474292/114248897-f3101a00-99d3-11eb-9d48-ed8c9cd6f568.png) 
 
