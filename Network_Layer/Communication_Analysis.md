# Analyze Network Layer Communication

## Overview
In this activity, I will analyze DNS and ICMP traffic in transit using data from a network protocol analyzer tool. I will identify which network protocol was utilized in assessment of the cybersecurity incident. 

In the internet layer of the TCP/IP model, the IP formats data packets into IP datagrams. The information provided in the datagram of an IP packet can provide security analysts with insight into suspicious data packets in transit.

Knowing how to identify potentially malicious traffic on a network can help cybersecurity analysts assess security risks on a network and reinforce network security.

## Scenario
You are a cybersecurity analyst working at a company that specializes in providing IT services for clients. Several customers of clients reported that they were not able to access the client company website www.yummyrecipesforme.com, and saw the error “destination port unreachable” after waiting for the page to load. 

You are tasked with analyzing the situation and determining which network protocol was affected during this incident. To start, you attempt to visit the website and you also receive the error “destination port unreachable.” To troubleshoot the issue, you load your network analyzer tool, tcpdump, and attempt to load the webpage again. To load the webpage, your browser sends a query to a DNS server via the UDP protocol to retrieve the IP address for the website's domain name; this is part of the DNS protocol. Your browser then uses this IP address as the destination IP for sending an HTTPS request to the web server to display the webpage  The analyzer shows that when you send UDP packets to the DNS server, you receive ICMP packets containing the error message: “udp port 53 unreachable.” 

## tcpdump Log
![image](https://github.com/user-attachments/assets/6a860257-a939-46d1-b8bd-efad8925877a)

In the tcpdump log, you find the following information:

1. The first two lines of the log file show the initial outgoing request from your computer to the DNS server requesting the IP address of yummyrecipesforme.com. This request is sent in a UDP packet.

2. The third and fourth lines of the log show the response to your UDP packet. In this case, the ICMP 203.0.113.2 line is the start of the error message indicating that the UDP packet was undeliverable to port 53 of the DNS server.

3. In front of each request and response, you find timestamps that indicate when the incident happened. In the log, this is the first sequence of numbers displayed: 13:24:32.192571. This means the time is 1:24 p.m., 32.192571 seconds.

4. After the timestamps, you will find the source and destination IP addresses. In the first line, where the UDP packet travels from your browser to the DNS server, this information is displayed as: 192.51.100.15 > 203.0.113.2.domain. The IP address to the left of the greater than (>) symbol is the source address, which in this example is your computer’s IP address. The IP address to the right of the greater than (>) symbol is the destination IP address. In this case, it is the IP address for the DNS server: 203.0.113.2.domain. For the ICMP error response, the source address is 203.0.113.2 and the destination is your computers IP address 192.51.100.15.

5. After the source and destination IP addresses, there can be a number of additional details like the protocol, port number of the source, and flags. In the first line of the error log, the query identification number appears as: 35084. The plus sign after the query identification number indicates there are flags associated with the UDP message. The "A?" indicates a flag associated with the DNS request for an A record, where an A record maps a domain name to an IP address. The third line displays the protocol of the response message to the browser: "ICMP," which is followed by an ICMP error message.

6. The error message, "udp port 53 unreachable" is mentioned in the last line. Port 53 is a port for DNS service. The word "unreachable" in the message indicates the UDP message requesting an IP address for the domain "www.yummyrecipesforme.com" did not go through to the DNS server because no service was listening on the receiving DNS port.

7. The remaining lines in the log indicate that ICMP packets were sent two more times, but the same delivery error was received both times.
   
## Incident Report
[Blank Incident Report](https://docs.google.com/document/d/1hwjSRYalxGd-qyRIXWz8LBVuSAgEq0AHXOF_BB7DdrI/template/preview?usp=sharing) \
[Completed Incident Report](https://docs.google.com/document/d/1YfBeVcu0BHabKR4Rp3omLd4MCTYoa47Hy5cgyofq6Ds/edit?usp=sharing) \
[Example Incident Report](https://docs.google.com/document/d/17-l7_zLY9fWiS4lGemxqgbnfSe8KG_OqM_PMfZA_gp4/template/preview)

## Summary of Problem
The UDP protocol revealed that the message requesting an IP address for the domain "www.yummyrecipesforme.com" did not reach the DNS server. Network analysis showed that the ICMP echo reply returned the error message: "UDP port 53 unreachable." This indicates that port 53, used for DNS services, was not responding because no service was listening on the receiving DNS port.

## Analysis of Problem
The incident occurred at 13:24:32.192571 (1:24 p.m.). The IT team became aware of the issue when several customers reported being unable to access the client company's website. An IT analyst attempted to access the site to confirm the error, then analyzed the tcpdump logs to identify the problem. Key findings revealed that port 53 was affected and the DNS server was unreachable. The most likely cause was that the DNS server was either down or misconfigured.

## ANSWER
[Incident Report](https://docs.google.com/document/d/11YIrN6R3fTqw7AWeh_4YCB4QXK8VnO4_CYPSK2MU5xc/edit?usp=sharing) \
[Explanation](https://docs.google.com/document/d/19kE466MVHdIRk86EOkUFvbepahRIMMIu5lDDgCBkg0E/template/preview#heading=h.rkogpw759h9x)

## Differences
The report provided by Google offers a more detailed and comprehensive summary of the problem found in the tcpdump log. I didn't focus on the bigger picture and instead went straight to identifying the root cause that the DNS server is not responding, rather than explaining what is happening. The analysis was similar to mine but more concise and well-worded.
