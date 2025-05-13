## Starting Point Tier 0

### Meow

Q1:  What does the acronym VM stand for?   
A1: virtual machine

Q2: What tool do we use to interact with the operating system in order to issue commands via the command line, such as the one to start our VPN connection? It's also known as a console or shell.   
A2: terminal

Q3: What service do we use to form our VPN connection into HTB labs?  
A3: openvpn

Q4: What tool do we use to test our connection to the target with an ICMP echo request?  
A4: ping

Q5: What is the name of the most common tool for finding open ports on a target?  
A5: nmap

Q6: What service do we identify on port 23/tcp during our scans?  
A6: telnet

Q7: What username is able to log into the target over telnet with a blank password?  
A7: root

Q8: Submit root flag   
A8: Login with credentials `Q7` to get `flag` 

### Fawn

```bash
┌──(kali㉿kali)-[~]
└─$ nmap -sCV 10.129.168.12               
Starting Nmap 7.94 ( https://nmap.org ) at 2025-05-12 23:44 EDT
Nmap scan report for 10.129.168.12
Host is up (0.74s latency).
Not shown: 999 closed tcp ports (conn-refused)
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_-rw-r--r--    1 0        0              32 Jun 04  2021 flag.txt
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to ::ffff:10.10.16.12
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 3
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
Service Info: OS: Unix

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 78.64 seconds
```

Q1: What does the 3-letter acronym FTP stand for?  
A1: File Transfer Protocol

Q2: Which port does the FTP service listen on usually?  
A2: 21

Q3: FTP sends data in the clear, without any encryption. What acronym is used for a later protocol designed to provide similar functionality to FTP but securely, as an extension of the SSH protocol?  
A3: sftp 

Q4: What is the command we can use to send an ICMP echo request to test our connection to the target?  
A4: ping

Q5: From your scans, what version is FTP running on the target?   
A5: vsftpd 3.0.3

Q6: From your scans, what OS type is running on the target?   
A6: Unix

Q7: What is the command we need to run in order to display the 'ftp' client help menu?  
A7: ftp -?

Q8: What is username that is used over FTP when you want to log in without having an account?   
A8: anonymous

Q9: What is the response code we get for the FTP message 'Login successful'?   
A9: 230

Q10: There are a couple of commands we can use to list the files and directories available on the FTP server. One is dir. What is the other that is a common way to list files on a Linux system.   
A10: ls

Q11: What is the command used to download the file we found on the FTP server?  
A11: get

Q12: Submit root flag   
A12: using `get` to download `flag.txt` file after connect `ftp` with `anonymous`

### Dancing

```bash
┌──(kali㉿kali)-[~]
└─$ nmap -sCV 10.129.175.250
Starting Nmap 7.94 ( https://nmap.org ) at 2025-05-13 00:12 EDT
Nmap scan report for 10.129.175.250
Host is up (0.69s latency).
Not shown: 997 closed tcp ports (conn-refused)
PORT    STATE SERVICE       VERSION
135/tcp open  msrpc         Microsoft Windows RPC
139/tcp open  netbios-ssn   Microsoft Windows netbios-ssn
445/tcp open  microsoft-ds?
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb2-time: 
|   date: 2025-05-13T08:16:21
|_  start_date: N/A
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled but not required
|_clock-skew: 4h02m30s

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 108.12 seconds
```

Q1: What does the 3-letter acronym SMB stand for?  
A1: Server Message Block

Q2: What port does SMB use to operate at?  
A2: 445

Q3: What is the service name for port 445 that came up in our Nmap scan?  
A3: microsoft-ds

Q4: What is the 'flag' or 'switch' that we can use with the smbclient utility to 'list' the available shares on Dancing?  
A4: -L

Q5: How many shares are there on Dancing?  
A5: 4

Q6: What is the name of the share we are able to access in the end with a blank password?  
A6: using `smbclient -L //10.129.175.250/` to list shares, got `WorkShares`

Q7: What is the command we can use within the SMB shell to download the files we find?  
A7: get

Q8: Submit root flag  
A8: using `smbclient //10.129.175.250/WorkShares` enter your `kali` password got shell at `\\10.129.175.250\WorkShares\`, `get flag.txt` from directory `James.P`

### Redeemer

```bash
┌──(kali㉿kali)-[~/htb/startingpoint/redeemer]
└─$ nmap -Pn -p- --min-rate=1000 -T4 10.129.164.131
Starting Nmap 7.94 ( https://nmap.org ) at 2025-05-13 04:08 EDT
Warning: 10.129.164.131 giving up on port because retransmission cap hit (6).
Nmap scan report for 10.129.164.131
Host is up (0.26s latency).
Not shown: 65507 closed tcp ports (conn-refused), 27 filtered tcp ports (no-response)
PORT     STATE SERVICE
6379/tcp open  redis

Nmap done: 1 IP address (1 host up) scanned in 80.62 seconds
```

Q1: Which TCP port is open on the machine?  
A1: 6379

Q2: Which service is running on the port that is open on the machine?  
A2: redis

Q3: What type of database is Redis? Choose from the following options: (i) In-memory Database, (ii) Traditional Database 
A3: In-memory Database

Q4: Which command-line utility is used to interact with the Redis server? Enter the program name you would enter into the terminal without any arguments. 
A4: redis-cli

Q5: Which flag is used with the Redis command-line utility to specify the hostname?  
A5: redis-cli -h

Q6: Once connected to a Redis server, which command is used to obtain the information and statistics about the Redis server?  
A6: INFO

Q7: What is the version of the Redis server being used on the target machine?  
A7: using `redis-cli -h <IP>` and using command `info` after connected shell, check the `redis_version`

Q8: Which command is used to select the desired database in Redis?  
A8: select

Q9: How many keys are present inside the database with index 0?  
A9: using `select 0` after that using `dbsize` to get key inside db

Q10: Which command is used to obtain all the keys in a database?  
A10: keys *

Q11: Submit root flag  
A11: `select 0` => `keys *` ==> `get flag`
