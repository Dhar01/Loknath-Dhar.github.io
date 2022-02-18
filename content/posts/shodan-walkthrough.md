---
title: "Shodan.io Walk-through [Tryhackme]"
date: 2020-10-09T01:34:53+06:00
draft: false
---  

[Shodan.io ](https://www.shodan.io/)is a search engine for the internet of things. There is a room about Shodan in Tryhackme and this walk-through is about that.

> Due to the nature of Shodan and its scanning services, the answer is changing all the time. So keep trying.


# Task 01


An autonomous system number (ASN) is a global identifier of a range of IP addresses. Basically, large companies like Google, Microsoft have their own ASN for all of the IP addresses they own.

To find out ASN, first, we can search their IP address: `ping google.com`

We can put the IP address into an **ASN lookup tool** such as [ultralools/asninfo](https://www.ultratools.com/tools/asnInfo)

Though, we can put the company name here to find the ASN, using the IP address seems the easiest one to me.

![asn-lookup](https://user-images.githubusercontent.com/25137893/95559728-0a2c7a00-0a3a-11eb-8b81-3e8023b32974.png)

On shodan, we can search using the ASN filter. The filter is: `ASN:[number]`
here, the number is marked on the picture.

![ASN-01](https://user-images.githubusercontent.com/25137893/95559662-ed904200-0a39-11eb-8943-24109ca82302.png)


# Task 02


* What is Google's ASN number?

**Ans:** You know it now. ;)

* When it was allocated?

**Ans:** Again, look at the details.

* Where are most of the machines on this ASN number, physically in the world?

**Ans:** United States.

![top_country](https://user-images.githubusercontent.com/25137893/95559902-4bbd2500-0a3a-11eb-9690-608daff9d461.png)

* What is Google's top service across all their devices on this ASN?

**Ans:** SSH.

![ssh](https://user-images.githubusercontent.com/25137893/95559968-61324f00-0a3a-11eb-8915-4625e04b23bc.png)

* What SSH product does Google use?

**Ans:** OpenSSH.

* What is Google's most used Google product, according to this search? Ignore the word "Google".

**Ans:** Cloud.

![product](https://user-images.githubusercontent.com/25137893/95560023-760ee280-0a3a-11eb-88c6-248639c576c3.png)


# Task 03


Here is a list of filters for shodan:
1. product: _product Name_ (_ex: MySQL_)
2. city
3. country
4. Geo (*co-ordinates*)
5. Hostname
6. net (*based on IP/CIDR*)
7. os (*find operating systems*)
8. port
9. before/after (*time-frames*)


# Task 04


* What is the top operating system for MYSQL servers in Google's ASN?

**Ans:** 5.6.40–84.0-log

![server](https://user-images.githubusercontent.com/25137893/95560134-a5255400-0a3a-11eb-95ee-ff5d4a388c27.png)

* What is the 2nd most popular country for MYSQL servers in Google's ASN?

**Ans:** Netherlands.

![netherlands](https://user-images.githubusercontent.com/25137893/95560162-b3737000-0a3a-11eb-9080-dfca6f920155.png)

* Under Google's ASN, which is more popular for nginx, Hypertext Transfer Protocol, or Hypertext Transfer Protocol(s)?

**Ans:** HyperText Transfer Protocol.

![port_80_1](https://user-images.githubusercontent.com/25137893/95560211-c2f2b900-0a3a-11eb-9478-7f3f1adac102.png)

![port_80](https://user-images.githubusercontent.com/25137893/95560237-ce45e480-0a3a-11eb-9589-4944832f1d89.png)

**Port 80** stands for **HTTP**; **port 443** stands for **HTTPs**.

* Under Google's ASN, what is the most popular city?

**Ans:** Mountain View. (*answer changes time to time*)

* Under Google's ASN in Los Angeles, what is the top operating system according to Shodan?

**Ans:** PAN-OS. (*answer changes time to time*)

![city](https://user-images.githubusercontent.com/25137893/95612628-85ffe400-0a85-11eb-9f4b-9886b9691023.png)

![pan-os](https://user-images.githubusercontent.com/25137893/95612653-8f894c00-0a85-11eb-8b3b-5e68749d0caa.png)

* Using the top Webcam search from the explore page, does Google's ASN have any webcams? Yay / nay.

**Ans:** Nay.


# Task 05


Shodan has a limit on the free user account. It has an API, use it for more searches.

