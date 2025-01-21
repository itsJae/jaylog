---
title: "[Network] TCP Three-Way Handshake & TLS Handshake"
seoTitle: "[Network & HTTP] TCP Three-Way Handshake & TLS Handshake"
seoDescription: "In this article, I will be talking about what are TCP/IP, three-way handshake, and TLS handshake."
datePublished: Wed Nov 08 2023 23:27:14 GMT+0000 (Coordinated Universal Time)
cuid: cloqe3si0000208ld0dlm3wwf
slug: network-http-tcp-three-way-handshake-tls-handshake
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1699482321828/de320ef2-7b31-4b9b-9848-2afe47935704.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1699486019662/d156aa55-7ff9-43ff-9afc-8a2353e5ec5c.png
tags: network, tls, tcp, tcpip-model, 3-way-handshake

---

---

## Introduction

In this article, I will be talking about what are TCP/IP, three-way handshake, and TLS handshake.

---

## TCP/IP

Transmission Control Protocol (TCP) is a protocol that is used to send data to someone just like a message. TCP is similar to a puzzle, where the entire puzzle is broken down into smaller pieces, and we combine them to make it one. In TCP, the data is chopped into pieces and travels through different routes, some of which can take a longer time than others.

The Internet Protocol (IP) ensures that those puzzles (smaller pieces of data) arrive at the correct destination.

TCP is used in conjunction with IP in order to maintain a connection between the sender and the target (destination) and to ensure packet order.

**TCP Characteristics:**

* Uses a 3-way handshake to establish a connection and a 4-way handshake to terminate the connection.
    
* Reliable (data is not duplicated, lost, etc)
    
* Slower than UDP
    

---

## TCP Three-way Handshake

A three-way handshake is used to verify the data and establish a connection. It is to ensure that both sides (client & server) are ready to communicate and send/receive data. Whenever the data is transmitted via TCP, a 3-way handshake occurs.

![TCP handshake diagram](https://www.cloudflare.com/img/learning/cdn/tls-ssl/tcp-handshake-diagram.png align="left")

**Three-way handshake process:**

1. The source sends an SYN “initial request” packet to the target server to start the dialogue.
    
    * PORT status:
        
    * client: `CLOSED` --&gt; `SYN_SENT`
        
    * server: `LISTEN`
        
2. The target server sends a SYN-ACK packet to agree to the process.
    
    * PORT status:
        
    * client: `CLOSED`
        
    * server: `SYN_RCV`
        
3. The source sends an ACK packet to the target to confirm the process, after which the message contents can be sent.
    
    * PORT status:
        
    * client: `ESTABLISHED`
        
    * server: `SYN_RCV` --&gt; `ACK` --&gt; `ESTABLISHED`
        

---

## TLS Handshake

![the TLS Handshake](https://cf-assets.www.cloudflare.com/slt3lc6tev37/5aYOr5erfyNBq20X5djTco/3c859532c91f25d961b2884bf521c1eb/tls-ssl-handshake.png align="left")

A TLS handshake is the process that starts a communication session that uses TLS. TLS is an encryption and authentication protocol. Just like the three-way handshake was to establish a connection and verify the data, TLS "handshake" is also used to acknowledge each other, verify each other, establish the cryptographic algorithms and agree on session keys.

---

## Reference

[https://www.cloudflare.com/learning/ddos/glossary/tcp-ip/](https://www.cloudflare.com/learning/ddos/glossary/tcp-ip/)

[https://www.cloudflare.com/learning/ssl/what-happens-in-a-tls-handshake/](https://www.cloudflare.com/learning/ssl/what-happens-in-a-tls-handshake/)