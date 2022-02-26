# offensive
final project offensive report
# Red Team: Summary of Operations

## Table of Contents
- Exposed Services
- Critical Vulnerabilities
- Exploitation

### Exposed Services
_TODO: Fill out the information below._

Nmap scan results for each machine reveal the below services and OS details:

```bash
$ nmap ... nmap -sC -sV --reason -p 22,80,139,445 192.168.1.110
  https://docs.google.com/document/d/1xZ8YLNCmJalc-poug1nDn4ppX0WbqnT4Pzn2QXe3ib0/edit?usp=sharing
```

This scan identifies the services below as potential points of entry:
- Target 1
  - Port 22 SSH is open
  - port 80 HTTP is running (apache 2.4.10)
  - port 111 runing rpcbind
  - ports 139 and 445 have netbios-ssn/microsoft-ds 

The following vulnerabilities were identified on each target:
- Target 1
  - rpcbind - CVE-2017-8779
  - apache 2.4.10 -CVE-2017-7668, CVE-2017-3169
  - 



### Exploitation
_TODO: Fill out the details below. Include screenshots where possible._

The Red Team was able to penetrate `Target 1` and retrieve the following confidential data:
- Target 1
  - `flag1.txt`: _TODO: Insert `flag1.txt` hash value_
    - **Exploit Used**
      - _TODO: Identify the exploit used_
      - _TODO: Include the command run_
  - `flag2.txt`: _TODO: Insert `flag2.txt` hash value_
    - **Exploit Used**
      - _TODO: Identify the exploit used_
      - _TODO: Include the command run_
