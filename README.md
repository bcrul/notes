# WORK IN PROGRESS, CONSOLIDATING OLD NOTES

## Recon

### Useful Recon Wordlists

/usr/share/wordlists/dirb/common.txt  
/usr/share/seclists/Discovery/Web-Content/directory-list-1.0.txt  
/usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-5000.txt  
/usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-0.txt

### **Nmap**

Basic Examples  
nmap [Target] -p [specific port(s)]  
nmap [Target] --top-ports [#]

Scan all 65535 ports  
nmap -p- [Target]

Fast TCP scan of top 100 ports  
nmap -Pn -sT -F [Target] -oA [Output]

M's default scan config Scan  
nmap -Pn -n -sS -p- -sV --min-hostgroup 255 --min-rtt-timeout 25ms --max-rtt-timeout 100ms --max-retries 1 --max-scan-delay 0 --min-rate 1000 -oA [Output] -vvv --open -iL [Target List]

SSL Scan  
nmap -Pn --script ssl-enum-ciphers -iL [Target List] -p 443 --min-hostgroup 255 --max-scan-delay 0 --min-rate 1000 -oA [Output]

Flags  
-Pn                 no ping  
-n                  no dns resolution  
-sS                 Syn (stealth) Scan  
-p-                 all ports  
-sV                 service and version detection  
--min-hostgroup     specifigy min # of tgts to scan in parallel  
--min-rtt-timout    adjust probe timeout  
--max-rtt-timeout   adjust probe timeout  
--max-retries       specify number of probe retrans  
--max-scan-delay    adjust time between probes  
--min-rate          directly control scanning rate  
-oA                 All output formats  
-vvv                verbosity  
--open              only show hosts with an open port  
-iL                 target list

### Gobuster

Subdomain Enumeration  
gobuster dns -d [Target Domain] -w [Wordlist] -o [Output]

Directory Enumeration  
gobuster dir -u [Target URL] -w [Wordlist] -o [Output]

Directory Enumeration, follow redirects and ignore size 74 (website does not exist response for this particular site)  
gobuster dir -u [Target URL] -r -w [Wordlist] -o [Output] --exclude-length 74 --wildcard

### FFuF

Basic Usage  
ffuf -w [Wordlist] -u [Target]

Target Examples  
https://[Target Host]/FUZZ  
https://FUZZ.[Target Host]/  
https://[Target Host]/directory/FUZZ

## Shells

## Cracking

### Useful Password Cracking Wordlists
/usr/share/wordlists/rockyou.txt
david-palma - passwords-WPA/wpa-over200k.txt

### Hash Identification

Use hashid to try to identify hash type  
hashid file.hash

### Hashcat

Crack NTLM Hash  
hashcat -m 1000 [Hashfile] [Wordlist] -r [Rules] --force

Crack WPA2 Hashes  
hashcat -m 22000 [Hashfile] -r [Rules] [Wordlist]

Flags  
-m 1000             ntlm hash  
-m 2200             wpa2 hash  
--force             Force Hashcat to start even if it detects system might not work correctly

Helpful Hashcat Rules  
rules/best64.rule

### John the Ripper

Add this later

## Privilege Escalation

## Mobile