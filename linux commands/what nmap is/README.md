Nmap (Network Mapper) is a powerful open-source tool used for network discovery and security auditing. It can help you discover hosts and services on a computer network, thus providing you with information about your network infrastructure and potential vulnerabilities.

### Basic Nmap Command Usage

#### 1. *Scan a Single Host*
To scan a single host, you can simply specify its IP address or hostname:
bash
nmap 192.168.1.1


#### 2. *Scan a Range of IPs*
You can scan a range of IP addresses by specifying a range:
bash
nmap 192.168.1.1-50

Alternatively, use CIDR notation for the range:
bash
nmap 192.168.1.0/24


#### 3. *Scan Multiple Hosts*
You can scan multiple specific hosts by separating them with spaces:
bash
nmap 192.168.1.1 192.168.1.5 192.168.1.10


#### 4. *Scan All Hosts in a Subnet*
Use CIDR notation for the entire subnet:
bash
nmap 192.168.1.0/24


### Common Nmap Options

#### 1. *Port Scanning*
To scan the most common 1,000 ports:
bash
nmap 192.168.1.1

For scanning specific ports, use the -p flag:
bash
nmap -p 22,80,443 192.168.1.1

To scan a range of ports:
bash
nmap -p 1-1000 192.168.1.1


#### 2. *Service Version Detection*
To detect versions of services running on open ports:
bash
nmap -sV 192.168.1.1


#### 3. *Operating System Detection*
To try to detect the operating system of a remote host:
bash
nmap -O 192.168.1.1


#### 4. *Aggressive Scan*
An aggressive scan combines several scan techniques, including OS detection, version detection, script scanning, and traceroute:
bash
nmap -A 192.168.1.1


#### 5. *Scan with Ping Only*
To see if hosts are online without scanning ports:
bash
nmap -sn 192.168.1.0/24


#### 6. *Scan Using TCP Connect Scan*
A TCP Connect Scan completes the full TCP handshake. It's a less stealthy scan, but it's useful when stealth isn't a concern:
bash
nmap -sT 192.168.1.1


#### 7. *SYN Scan (Stealth Scan)*
A SYN scan sends a SYN packet and waits for a response. It is faster and more stealthy because it doesn't complete the handshake:
bash
nmap -sS 192.168.1.1


#### 8. *UDP Scan*
To scan for open UDP ports, use the -sU option:
bash
nmap -sU 192.168.1.1


#### 9. *Scan for Specific Service/Protocol*
To search for a specific service (e.g., HTTP), you can use:
bash
nmap -p 80 --open 192.168.1.1


#### 10. *Scan with Timing Options*
You can adjust the speed of your scan by using timing templates. The range is from 0 (slowest, stealthiest) to 5 (fastest):
bash
nmap -T4 192.168.1.1

This uses a faster scan but is still relatively safe.

#### 11. *Disable DNS Resolution*
If you don't want Nmap to resolve hostnames, use the -n flag:
bash
nmap -n 192.168.1.1


#### 12. *Using Nmap Scripts*
Nmap has a scripting engine (NSE) that lets you run various scripts to gather information or check for vulnerabilities:
bash
nmap --script=default 192.168.1.1

You can specify a particular script:
bash
nmap --script=http-vuln-cve2021-22947 192.168.1.1


#### 13. *Output to a File*
You can save the output of a scan to a file in different formats:
- Normal output:
  bash
  nmap -oN output.txt 192.168.1.1
  
- XML output (good for further processing):
  bash
  nmap -oX output.xml 192.168.1.1
  
- Grepable output:
  bash
  nmap -oG output.gnmap 192.168.1.1
  

#### 14. *Verbose Output*
To get more detailed output, use the -v flag:
bash
nmap -v 192.168.1.1


#### 15. *Scan a Website*
You can scan a website (host) using its domain name:
bash
nmap example.com


#### 16. *Scan for Firewall or IDS/IPS Detection*
Nmap has various techniques for scanning through firewalls or Intrusion Detection/Prevention Systems (IDS/IPS). The -sS (SYN scan) is often effective at bypassing simple firewalls or packet filters.

### Combining Multiple Options
You can combine multiple Nmap options for a more advanced scan:
bash
nmap -sS -sV -O -p 1-1000 192.168.1.1

This command will perform a SYN scan, detect service versions, perform OS detection, and scan ports 1 through 1000 on the host 192.168.1.1.

### Example of a Full Scan with Multiple Options:
bash
nmap -A -p 1-65535 -T4 -v 192.168.1.1

This command performs an aggressive scan (-A), scans all ports (-p 1-65535), uses timing template 4 for faster results (-T4), and outputs detailed information (-v).

---

### Nmap Scan Types Explained:
1. *TCP Connect Scan (-sT)*: Initiates a full TCP connection.
2. *SYN Scan (-sS)*: Fast and stealthy scan. It only sends SYN packets to the target.
3. *UDP Scan (-sU)*: Scans for open UDP ports.
4. *Stealth Scan (-sN, -sF, -sX)*: Sends unusual or fragmented packets to avoid detection.
5. *TCP ACK Scan (-sA)*: Used for mapping firewall rulesets.
6. *Window Scan (-sW)*: Uses window size to identify open ports (used for firewall evasion).
7. *Maimon Scan (-sM)*: A stealthy scan that can bypass some firewalls.
8. *FIN Scan (-sF)*: Sends a FIN flag to open ports, often bypassing firewalls or filtering devices.
9. *Idle Scan (-sI)*: An advanced stealth scan where an intermediate host is used to send probes.

---

### Notes:
- *Ethical Use*: Nmap should only be used on networks and systems for which you have explicit permission to scan. Unauthorized scanning is illegal and unethical.
- *Scanning Speed*: Some scans can be very slow, especially with large networks or extensive port ranges. Use options like -T4 for faster scans.
- *Stealth*: Some Nmap options, such as -sS (SYN scan), are designed to be more discreet, but determined systems or network security tools may still detect these scans.

For more detailed information, you can always refer to Nmap's man page:
bash
man nmap

Or use the help command:
bash
nmap --help
