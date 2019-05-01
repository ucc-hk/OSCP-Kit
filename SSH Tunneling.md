### SSH Tunneling / Pivoting

sshuttle  
e.g.
sshuttle -vvr user@10.10.10.10 10.1.1.0/24

Local port forwarding  
ssh < gateway > -L < local port to listen >:< remote host >:< remote port >

Remote port forwarding  
ssh < gateway > -R < remote port to bind >:< local host >:< local port >

Dynamic port forwarding  
ssh -D < local proxy port> -p < remote port > < target >

Plink local port forwarding  
plink -l root -pw pass -R 3389 : < localhost > : 3389 < remote host >

#### VPN – sshuttle 介紹  

https://louie023.wordpress.com/2013/07/30/%E7%AA%AE%E4%BA%BA%E7%9A%84-vpn-sshuttle-%E4%BB%8B%E7%B4%B9/

https://www.ivoidwarranties.tech/posts/pentesting-tuts/pivoting/pivoting-basics/  

#### Source  
https://github.com/apenwarr/sshuttle  
  
### Remote Desktop

#### Remote Desktop for windows with share and 85% screen

rdesktop -u username -p password -g 85% -r disk:share=/root/ 10.10.10.10
