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
  
```
https://docs.google.com/document/d/1xZ8YLNCmJalc-poug1nDn4ppX0WbqnT4Pzn2QXe3ib0/edit?usp=sharing
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




### Exploitation

The Red Team was able to penetrate `Target 1` and retrieve the following confidential data:
- Target 1
  - `flag1.txt`:flag1{b9bbcb33e11b80be759c4e844862482d}
    - **Exploit Used**
      - Using inspector tool on the 192.168.1.110/service.html page. 
      -
  - `flag2.txt`: flag2{fc3fd58dcdad9ab23faca6e9a36e581c}
    - **Exploit Used**
      - Used "Wpscan --url http://raven.local/wordpress --enumerate u" to discover usernames for the website, then guessed at the password for user michael in order to SSH into webserver. Once in, flag2 was under var/www- `flag2.txt`:
    - **Exploit Used**
      - flag3{afc01ab56b50591e7dccf93122770cd2}
      - Cat out the wp-config.php file to find the mysql password: R@v3nSecurity.
      - Use the root:R@v3nSecurity to access the mysql db: mysql -u root -p
      - use wordpress > select * from wp_users: provides the flag.
    - **Exploit Used**
      - flag4{715dea6c055b9fe3337544932f2941ce}
      - ran john the ripper against the hashed versions of Michael and Steven's passwords to determine steven's. michael:$P$$8jRvZQ.VQcGZ1DeiKToCQd.cPw5XCe0
steven:$P$8kJVD9jsxx/loJoqNsURgHiaB23j7W/

      - Check sudo privledges with sudo -l. we have ability to use python
      - Using GTFObin and other resources for privledge escalation, sudo python -c ‘import pty;pty.spawn(“/bin/bash”)’ works for us.
      - once operating as root, find flag4.txt
   
