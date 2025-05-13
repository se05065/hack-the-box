## Starting Point 2

### APpointment

```bash
┌──(kali㉿kali)-[~/htb/startingpoint/redeemer]
└─$ nmap -sCV 10.129.167.73 -T4                    
Starting Nmap 7.94 ( https://nmap.org ) at 2025-05-13 04:53 EDT
Nmap scan report for 10.129.167.73
Host is up (0.44s latency).
Not shown: 999 closed tcp ports (conn-refused)
PORT   STATE SERVICE VERSION
80/tcp open  http    Apache httpd 2.4.38 ((Debian))
|_http-title: Login
|_http-server-header: Apache/2.4.38 (Debian)

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 69.46 seconds
```

Q1: What does the acronym SQL stand for?  
A1: Structured Query Language

Q2: What is one of the most common type of SQL vulnerabilities?  
A2: SQL Injection 

Q3: What is the 2021 OWASP Top 10 classification for this vulnerability?  
A3: A03:2021-Injection

Q4: What does Nmap report as the service and version that are running on port 80 of the target?  
A4: Apache httpd 2.4.38 ((Debian))

Q5: What is the standard port used for the HTTPS protocol?  
A5: 443

Q6: What is a folder called in web-application terminology?  
A6: directory

Q7: What is the HTTP response code is given for 'Not Found' errors?  
A7: 404

Q8: Gobuster is one tool used to brute force directories on a webserver. What switch do we use with Gobuster to specify we're looking to discover directories, and not subdomains? 
A8: 
