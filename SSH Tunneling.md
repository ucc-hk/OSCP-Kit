###SSH Tunneling / Pivoting

sshuttle

sshuttle -vvr user@10.10.10.10 10.1.1.0/24
Local port forwarding

ssh <gateway> -L <local port to listen>:<remote host>:<remote port>
Remote port forwarding

ssh <gateway> -R <remote port to bind>:<local host>:<local port>
Dynamic port forwarding

ssh -D <local proxy port> -p <remote port> <target>
Plink local port forwarding

plink -l root -pw pass -R 3389:<localhost>:3389 <remote host>
