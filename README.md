# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system

## OUTPUT:
![image](https://github.com/user-attachments/assets/73405760-ad32-4fb2-add9-ab3a415cb0b4)

Invoke msfconsole:
## OUTPUT:
![image](https://github.com/user-attachments/assets/b7c4d56a-4597-40fc-964d-596cbdc1c3dd)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![image](https://github.com/user-attachments/assets/8bc8c535-75fa-412f-8b1a-d87ba25509e0)


Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000
## OUTPUT:
![image](https://github.com/user-attachments/assets/429eb460-d90d-4f8e-b27a-89e6cdd2d6ca)

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:
![image](https://github.com/user-attachments/assets/cfbf38b4-0299-4d9d-bc9a-d851f572e4d9)

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:
![image](https://github.com/user-attachments/assets/0d947f82-5676-40c3-87da-fc4c8608072d)


Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
![image](https://github.com/user-attachments/assets/58444f10-7a6d-4e4b-ab1c-712c6a237819)








## OUTPUT:

The info command provides information regarding a module or platform,

![image](https://github.com/user-attachments/assets/1c809366-7675-4785-9271-87a79b12a155)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
##MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>
![image](https://github.com/user-attachments/assets/bfaca975-7af4-4384-ad53-572766eab1d4)

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql

![image](https://github.com/user-attachments/assets/bfecee6e-e181-465f-a890-a2ff5fbaeab6)

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version

![image](https://github.com/user-attachments/assets/d170e807-65b4-469e-9d01-efb7a9d99554)


Use the set rhosts command to set the parameter and run the module, as follows:
![image](https://github.com/user-attachments/assets/96655608-d273-4068-97c6-8970c713ba32)


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
![image](https://github.com/user-attachments/assets/860fbb46-b2da-4cfe-a5fe-33aa71aa9677)


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true

![image](https://github.com/user-attachments/assets/e7d842a2-68c6-4031-894a-d64fe82c8465)


## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
