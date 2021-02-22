# nmapAutomator

A script that you can run in the background!
  
![nmapAutomator](https://i.imgur.com/3cMJIPr.gif)
  
## Summary

The main goal for this script is to automate the process of enumeration & recon that is run every time, and instead focus our attention on real pentesting.  
  
This will ensure two things:  
1. Automate nmap scans. 
2. Always have some recon running in the background. 

Once initial ports are found '*in 5-10 seconds*', we can start manually looking into those ports, and let the rest run in the background with no interaction from our side whatsoever.  
  
  
## Features:
1. **Quick:** Shows all open ports quickly (~15 seconds)  
1. **Basic:** Runs Quick Scan, then runs a more thorough scan on found ports (~5 minutes)  
1. **UDP:** Runs "Basic" on UDP ports (~5 minutes)  
1. **Full:** Runs a full range port scan, then runs a thorough scan on new ports (~5-10 minutes)  
1. **Vulns:** Runs CVE scan and nmap Vulns scan on all found ports (~5-15 minutes)  
1. **Recon:** Runs "Basic" scan "if not yet run", then suggests recon commands "i.e. gobuster, nikto, smbmap" based on the found ports, then prompts to automatically run them  
1. **All:** Runs all the scans consecutively (~20-30 minutes)  
  
  -----
  
## Requirements:
[Gobuster](https://github.com/OJ/gobuster) '*v3.0 or higher*', which we can install with:  
```bash
sudo apt update
sudo apt install gobuster
```

or [ffuf](https://github.com/ffuf/ffuf), which we can install with:
```bash
sudo apt update
sudo apt install ffuf
```

Other Recon tools used within the script include:
* [nmap Vulners](https://github.com/vulnersCom/nmap-vulners)
* [sslscan](https://github.com/rbsec/sslscan)
* [nikto](https://github.com/sullo/nikto)
* [joomscan](https://github.com/rezasp/joomscan)
* [wpscan](https://github.com/wpscanteam/wpscan)
* [droopescan](https://github.com/droope/droopescan)
* [smbmap](https://github.com/ShawnDEvans/smbmap)
* [enum4linux](https://github.com/portcullislabs/enum4linux)
* [dnsrecon](https://github.com/darkoperator/dnsrecon)
* [odat](https://github.com/quentinhardy/odat)
* [smtp-user-enum](https://github.com/pentestmonkey/smtp-user-enum)
  
*Most of these should be installed by default in [Parrot OS](https://www.parrotsec.org) and [Kali Linux](https://www.kali.org).*
  
## Installation:
```bash
git clone https://github.com/21y4d/nmapAutomator.git
sudo ln -s $(pwd)/nmapAutomator/nmapAutomator.sh /usr/local/bin/
```

## Examples of use:
```
./nmapAutomator.sh -h
Usage: ./nmapAutomator.sh -H/--host <TARGET-IP> -t/--type <TYPE> [-d/--dns <DNS SERVER>]

Scan Types:
	Quick: Shows all open ports quickly (~15 seconds)
	Basic: Runs Quick Scan, then runs a more thorough scan on found ports (~5 minutes)
	UDP  : Runs "Basic" on UDP ports "requires sudo" (~5 minutes)
	Full : Runs a full range port scan, then runs a thorough scan on new ports (~5-10 minutes)
	Vulns: Runs CVE scan and nmap Vulns scan on all found ports (~5-15 minutes)
	Recon: Suggests recon commands, then prompts to automatically run them
	All  : Runs all the scans (~20-30 minutes)
```

**Example commands**:
```
./nmapAutomator.sh --host 10.1.1.1 --type All
./nmapAutomator.sh -H 10.1.1.1 -t Basic
./nmapAutomator.sh -H www.github.com -t Recon -d 1.1.1.1
```

------

## TODO features list
**Feel free to send your pull requests and contributions :)**
- [x] ~~Support DNS resolution "use of urls/domains instead of IPs"~~ - Done, thanks @KatsuragiCSL
- [x] ~~Properly identify url extensions "testing index extensions for code 200"~~
- [x] ~~Add an nmap progress bar~~


## Add more recon options
- If you would like to suggest or add more port-based recon options, you can base your pull request on the [following lines](https://github.com/21y4d/nmapAutomator/blob/17377bb42e0b2e99bd7d4b20efc878a0a0051025/nmapAutomator.sh#L422-L428).
- If you would like to suggest more options for an existing port, you can add the new command under its port, similar to this [example line](https://github.com/21y4d/nmapAutomator/blob/17377bb42e0b2e99bd7d4b20efc878a0a0051025/nmapAutomator.sh#L447).
