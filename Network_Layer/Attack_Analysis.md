# Analyse Network Attacks

## Overview
In this activity, I will consider a scenario involving a customer of the company that I work for who experiences a security issue when accessing the company’s website. I will identify the likely cause of the service interruption. Then, I will explain how the attack occurred and the negative impact it had on the website. 

In this course, I've learned about several common network attacks.  I've learned their names, how they are carried out, and the characteristics of each attack from the perspective of the target. Understanding how attacks impact a network will help me troubleshoot issues on the organization’s network. It will also help me take steps to mitigate damage and protect a network from future attacks. 

## Scenario
You work as a security analyst for a travel agency that advertises sales and promotions on the company’s website. The employees of the company regularly access the company’s sales webpage to search for vacation packages their customers might like. 

One afternoon, you receive an automated alert from your monitoring system indicating a problem with the web server. You attempt to visit the company’s website, but you receive a connection timeout error message in your browser.

You use a packet sniffer to capture data packets in transit to and from the web server. You notice a large number of TCP SYN requests coming from an unfamiliar IP address. The web server appears to be overwhelmed by the volume of incoming traffic and is losing its ability to respond to the abnormally large number of SYN requests. You suspect the server is under attack by a malicious actor. 

You take the server offline temporarily so that the machine can recover and return to a normal operating status. You also configure the company’s firewall to block the IP address that was sending the abnormal number of SYN requests. You know that your IP blocking solution won’t last long, as an attacker can spoof other IP addresses to get around this block. You need to alert your manager about this problem quickly and discuss the next steps to stop this attacker and prevent this problem from happening again. You will need to be prepared to tell your boss about the type of attack you discovered and how it was affecting the web server and employees.

## Supporting Materials
[Wireshark TCP/HTTP log](https://docs.google.com/spreadsheets/d/1enpRzrIao3J2Lp2tOI0hmu1Cu7D7CjLGhFAiTiR9J64/edit?gid=218501934#gid=218501934) \
[How to read a Wiresharl TCP/HTTP log](https://docs.google.com/document/d/1JYyUPhfm2gwDellGRIcgItA3cZ7kz29xdYpVr1L_o9c/template/preview?usp=sharing)

## Incident Report
[Blank Report](https://docs.google.com/document/d/1xEk_arFwlQOto7KEM6gN-sIYriXhP9-lY2ftpBXhS4M/template/preview?resourcekey=0-_ODneeo__mDgK7BTE1FkVA) \
[Completed Report](https://docs.google.com/document/d/1-7tSemyEz8BGl4FFT4nE-L-loXAsa4L4VhjD1OH5-lE/edit?usp=sharing)

## Indentifying the Type of Attack
Network attacks are malicious attempts to disrupt, steal, or compromise data and network resources. In the given scenario, the symptoms of a large number of TCP SYN requests from an unfamiliar IP address indicate a SYN flood attack, a type of Denial of Service (DoS) attack. This attack overwhelms the web server, preventing it from completing the TCP handshake process necessary for legitimate connections, leading to connection timeout errors. Unlike Distributed Denial of Service (DDoS) attacks, which involve multiple sources, a DoS attack comes from a single source, making it easier to trace but still highly disruptive. The overwhelming traffic causes the server to be unable to respond to legitimate user requests, resulting in the website taking a long time to load and eventually timing out. Identifying the type of attack is crucial for implementing mitigation strategies and preventing future incidents.

## How does it work?
The SYN flood attack on the travel agency's website involved a large number of TCP SYN requests from an unfamiliar IP address, overwhelming the web server and causing connection timeouts. This type of Denial of Service (DoS) attack disrupts the normal TCP handshake process, preventing legitimate users from accessing the website. The immediate consequence was downtime, resulting in lost revenue and frustrated customers. If such attacks persist, they could damage the organization's reputation and lead to long-term business impacts. To prevent future incidents, implementing rate limiting, using SYN cookies, deploying advanced firewalls, and considering third-party DDoS protection are essential measures.

## ANSWER
[Report](https://docs.google.com/document/d/19Z9Y8kpgqfYr7Y6I6pvlKtbfJ7o6RDG_wGEJAEpLnys/template/preview?usp=sharing)

### Difference:
Both answers identify the issue as a SYN flood attack, which is a type of DoS attack. Our answer is more concise, while the provided answer includes slightly more detail about the web server's response to the overload.

Both answers provide a detailed explanation of the TCP three-way handshake and the impact of a SYN flood attack. Our answer is more concise, focusing on the essential steps and effects, while the provided answer includes additional details about resource reservation and specific log indications.

