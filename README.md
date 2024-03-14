# PWN-introduction
A beginner's guide to Pwn Challenges

Pwning is a term derived from gaming, referring to dominating or defeating someone or something. In cybersecurity, pwning refers to completely hacking a machine, typically upto the root level.<br/>
These challenges typically demand comprehensive knowledge of programming, computer architecture, and memory management. Players can engage in tasks including but not limited to exploit development, forensics, reverse engineering, binary and web exploitation and many more. Pwn challenges are widely recognised for their ability to hone technical acumen, critical thinking and problem solving abilities, pertaining to the identification and exploitation of vulnerabiilties in a computer system.<br/>
<br/>
Typically a Pwn challenge can be solved through the following steps:
1. Enumeration
2. Exploitation
3. Privilege escalation

## Enumeration
This step is probably the most crucial step and will determine the difficulty of the rest of the challenge to come. It primarily involves scanning a given server or a machine for open ports and finding out information about thr services running on these ports.<br/>

Pwn challenges often involve connecting to the target machine, which can be achieved through netcat. <br/>
```bash
nc 10.10.128.253 4444
```
The syntax is as follows:
```nc [IP] [PORT]```

<br/>
In a pwn challenge, we also will have to find out the functionality of the various binaries, usually by analysing its code through reverse engineering or memory analysis.

## Exploitation
Exploitation refers to exploiting the vulnerabilities found through enumeration. In a pwn challenge this involves exploiting the security or code flaw in the vulnerability. This is usually found through various tools like *gdb*, *hexeditors* and various *disassemblers*. <br/>
![image not loaded](https://media.geeksforgeeks.org/wp-content/uploads/20190228223034/1411.png)

## Scripting solutions
Not all binaries can be exploited by simply passing them to a couple of tools. In these cases, we whave to code various exploits using languages like *C*, *C++* or *Python*. These exploits are usually made to exploit various flaws in the code of the binary found through Enumeration or various tools.

## Binary Search Algorithm
The binary search algorithm is a fast and efficient algorithm for finding an element in a sorted array. It works by repeatedly dividing the array in half. At each step, it compares the target value with the middle element of the array and narrows down the search to the appropriate half. This process continues until the target value is located or the search interval is exhausted, indicating that the target value is not present in the array. 
<br/>

Visualization: <br/>
![image not loaded](https://cdn.analyticsvidhya.com/wp-content/uploads/2023/09/image-17.png)
