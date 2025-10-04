## Reconnisance

```nmap -p1-9000 -Pn -sU -sV 10.10.11.87 -oA basic 
Starting Nmap 7.95 ( https://nmap.org ) at 2025-10-04 18:30 IST
Stats: 0:32:56 elapsed; 0 hosts completed (1 up), 1 undergoing UDP Scan
Nmap scan report for 10.10.11.87
Host is up (0.39s latency).
Not shown: 8993 closed udp ports (port-unreach)
PORT     STATE         SERVICE       VERSION
68/udp   open|filtered dhcpc
69/udp   open          tftp          Netkit tftpd or atftpd
500/udp  open          isakmp?
4007/udp open|filtered pxc-splr
4401/udp open|filtered ds-srvr
4500/udp open|filtered nat-t-ike
5424/udp open|filtered beyond-remote
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port500-UDP:V=7.95%I=7%D=10/4%Time=68E1409C%P=x86_64-pc-linux-gnu%r(IPS
SF:EC_START,9C,"1'\xfc\xb08\x10\x9e\x89\xba\xc3APh\x82\xb7K\x01\x10\x02\0\
SF:0\0\0\0\0\0\0\x9c\r\0\x004\0\0\0\x01\0\0\0\x01\0\0\0\(\x01\x01\0\x01\0\
SF:0\0\x20\x01\x01\0\0\x80\x01\0\x05\x80\x02\0\x02\x80\x04\0\x02\x80\x03\0
SF:\x03\x80\x0b\0\x01\x80\x0c\x0e\x10\r\0\0\x0c\t\0&\x89\xdf\xd6\xb7\x12\r
SF:\0\0\x14\xaf\xca\xd7\x13h\xa1\xf1\xc9k\x86\x96\xfcwW\x01\0\r\0\0\x18@H\
SF:xb7\xd5n\xbc\xe8\x85%\xe7\xde\x7f\0\xd6\xc2\xd3\x80\0\0\0\0\0\0\x14\x90
SF:\xcb\x80\x91>\xbbin\x08c\x81\xb5\xecB{\x1f");

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 9896.21 seconds```

### the nmap result for udp port scan gives two unfiltered open ports
### **Note:** Port **500/udp (ISAKMP/IKE)** is open and **needs to be studied further** (use `ike-scan`, `nmap --script=ike-version`, and packet captures).

# Recommended commands for deeper analysis of port 500
# 1) Nmap scripts
nmap -sU -p 500 --script=ike-version,ike-probe -Pn 10.10.11.87

# 2) ike-scan (fingerprinting)
ike-scan -A 10.10.11.87

# 3) Packet capture while probing
sudo tcpdump -i eth0 host 10.10.11.87 and udp port 500 -w ike_probe.pcap
# Open ike_probe.pcap in Wireshark to inspect IKE/ISAKMP exchanges.
