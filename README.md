# My Cybersecurity Internship - Task 1

So for the first task of my internship I had to scan my local network
using Nmap to find open ports. I ran this on Kali Linux inside VMware.

## How I Started

First I found my IP address by running "ip a" in the terminal.
My Kali machine was on 192.168.50.129 so I scanned the whole
192.168.50.0/24 range.

## Command I Used

sudo nmap -sS 192.168.50.0/24 -oN scan_results.txt

The -sS flag does a TCP SYN scan which is faster and quieter than
a normal scan.

## What Nmap Found

Total 4 devices were found on the network.

My Windows PC (192.168.50.1) had the most open ports:
- 135, 139, 445 - these are Windows file sharing ports
- 3306 - this is MySQL database which was surprising to see open
- 902, 912 - VMware ports

There was also a DNS server at 192.168.50.2 with port 53 open.
The gateway at 192.168.50.254 had everything filtered which is good.
My own Kali machine showed all ports filtered too.

## What Worried Me

Port 445 being open is actually dangerous. This is the same port
that WannaCry ransomware used to spread. Also MySQL running on
port 3306 means someone on the network could try to access the database.

## What I Learned

Honestly this task was really eye opening. I never realized how many
ports are open on a normal Windows machine. It makes sense why
attackers do reconnaissance first before any attack - you can learn
a lot just from an Nmap scan without even touching the target machine.

Saving my scan results in scan_results.txt file which is also
uploaded here.
