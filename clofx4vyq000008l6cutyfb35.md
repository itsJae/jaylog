---
title: "[Network] Domain Name System (DNS)"
seoTitle: "[Network & HTTP] Domain Name System (DNS)"
seoDescription: "DNS servers involved in loading a webpage. How DNS translates a domain name into an IP address (Full process of DNS lookup). DNS Cache. DNS Record"
datePublished: Wed Nov 01 2023 15:34:30 GMT+0000 (Coordinated Universal Time)
cuid: clofx4vyq000008l6cutyfb35
slug: network-domain-name-system-dns
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698848363578/9cd4567b-dce0-4892-9fce-e15c9d8f842e.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1698852835440/f8d059fe-0d0a-46a5-9834-ace82e96d4e8.png
tags: dns, web-development, cache, networking, dns-resolver

---

---

## Introduction

In this article, I will be talking about DNS, which works just like a phonebook.

Other minor topics to be covered:

* DNS servers involved in loading a webpage.
    

* How DNS translates a domain name into an IP address (Full process of DNS lookup)
    
* DNS Cache
    

* DNS Record
    

---

## What Is DNS?

When you go to facebook.com, you can do it by entering facebook.com in the URL bar, then the browser will direct you to the page. How can it be done so easily? Well, we are getting help from the Domain Name System (DNS).

DNS is a phonebook of the Internet. For example, you have a phonebook like this:

* Jason - 604-834-2687
    
* Mary - 778-932-1784
    
* Nick - 778-745-2783
    
* Hunter - 778-128-7549
    

Do you memorize all the phone numbers of each person in your contact? - No.

You would go to your contact list on your phone, and then find the person's name that you want to call. DNS works just like this.

If you want to go to facebook.com, you just type that in the URL bar. DNS will translate that domain name into an IP address, which is a language that computers can understand. They can't understand our language.

For example:

* facebook.com - 123.021.123.111
    
* amazon.com - 321.123.021.111
    
* netflix.com - 111.222.111.222
    
* youtube.com - 132.123.189.372
    

Let's compare this one with the phonebook example above. It's not so different.

Without the DNS, we have to memorize all the IP addresses for each website we want to go to.

---

## FOUR(4) DNS Servers for loading a webpage

1. Recursive resolver
    
2. Root nameserver
    
3. Top Level Domain (TLD) server
    
4. Authoritative nameserver
    

![DNS Record Request Sequence - DNS Recursive Resolver gets request from client](https://cf-assets.www.cloudflare.com/slt3lc6tev37/3NOmAzkfPG8FTA8zLc7Li8/8efda230b212c0de2d3bbcb408507b1e/dns_record_request_sequence_recursive_resolver.png align="left")

### Recursive Resolver

The recursive resolver is the first stop in a DNS query. When the browser sends a request for the IP address, the resolver first looks at the cache. If there is nothing about the request in the cache, the resolver sends a new request to a DNS root server. Moreover, the resolver stores the data from the authoritative server in a cache.

Now, **cache** is something that I will briefly explain later, but it is simply a storage. Think of a website that you visit quite often. Maybe YouTube or Amazon.

For those websites, the DNS will store the IP address in a storage, so that it does not have to go through all the steps of a DNS query.

### DNS Root Server

When an uncached DNS query comes in, the first stop is the root server. Once the DNS lookup arrives at the root server, it goes down the hierarchy, which will be TLD server -&gt; servers for specific domains -&gt; (possibly subdomains if any).

![DNS Heirarchy](https://www.cloudflare.com/img/learning/dns/glossary/dns-root-server/dns-root-server.png align="left")

> There are only 13 DNS root servers.

### TLD Server

Top Level Domain Server maintains information like .com, .net, .org, etc. We call them Top Level Domain (TLD). If you want to visit youtube.com for the first time, the DNS resolver will direct you to the root server. The resolver sends information from the DNS root server to the TLD server. Now, the TLD server knows that you want to go to youtube**.com**. The TLD server will then point to the authoritative nameserver for that domain.

### Authoritative Server

The authoritative server provides the IP address for the specific domain name like youtube.com.

---

## DNS Lookup Full Process

![Complete DNS Lookup and Webpage Query - 10 steps](https://cf-assets.www.cloudflare.com/slt3lc6tev37/1NzaAqpEFGjqTZPAS02oNv/bf7b3f305d9c35bde5c5b93a519ba6d5/what_is_a_dns_server_dns_lookup.png align="left")

---

## DNS Cache

Web browsers do caching by default. As I explained previously, caching is storing data in a separate storage, so it can be used later. With caching, we can reduce the amount of time spent on finding an IP address.

When you type in the domain name in the URL bar, the resolver first checks if the information requested is already in the cache. If there is, we do not need to go to the root server, TLD server and authoritative server. A lot of work are reduced. This will also help you to see the webpage more quickly because the IP address is already there. The browser just needs to render the webpage.

---

## DNS Record

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698852792067/dcdf370b-79d1-41f9-8e8c-d23a858ef526.png align="center")