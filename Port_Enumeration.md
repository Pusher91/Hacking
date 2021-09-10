# Port and Service Enumeration


<details>
  <summary>21 TCP / FTP</summary>
  
- ftp
  | | |
  | ------------- | ------------- |
  | Connect to server  | ftp <ip address> |
  | Upload file | ftp> put \<file\>  |
  | Download file  | ftp> get \<file\>  |
  | Upload multiple files | ftp> mput *[.txt/.php/etc..] |
  | Download multiple files | ftp> mget *[.txt/.php/etc..] |
  | Turn off prompt while downloading files | ftp> prompt off |
  | Set mode to binary | ftp> binary |
  
- wget
|||
  | ------------- | ------------- |
  | Recursively download FTP contents  | wget -r ftp://\<user\>@\<ip address\> --password=\<password\><br> wget -r ftp://\<user\>:\<password\>@\<ip address\> |
  | Mirror FTP | wget --mirror ftp://\<user\>:\<password\>@\<ip address\>  |
  
- Proftp
  - Can copy file to/from directories over FTP using write permissions
  | | |
    | ------------- | ------------- |
    | Connect to FTP Server  | telnet \<ip address\> \<port\> |
    | Select file to copy | telnet> site cpfr \<file to copy\>  |
    | Select file to copy | telnet> site cpto \<directory to copy to\>  |
  
</details>
<details>
  <summary>22 TCP / SSH</summary>
  
| Connect to server  | ftp <ip address> |
| ------------- | ------------- |
| Upload file | ftp> put \<file\>  |
  
</details>

#### 25 TCP / SMTP
#### 53 TCP / DNS
#### 69 UDP / TFTP
#### 80 TCP / HTTP
#### 88 TCP / Kerberos
#### 110 TCP / POP3
#### 111 TCP / rpcbind / NFS
#### 113 TCP / ident
#### 119 TCP / NNTP
#### 135 TCP / msrpc
#### 139 TCP / netbios
#### 143 TCP / IMAP
#### 161 UDP / SNMP
#### 389 TCP / LDAP
#### 443 TCP / HTTPS
#### 445 TCP / SMB
#### 464 TCP / kpasswd5
#### 500 UDP / ISAKMP
#### 636 TCP / LDAPS
#### 837 TCP / rsync
#### 1025 TCP / msrpc
#### 1433 TCP / Microsoft SQL
#### 1521 TCP / Oracle TNS Listener
#### 2049 TCP / mountd (NFS)
#### 3000 TCP / Express.js Node
#### 3268 TCP / LDAPS
#### 3306 TCP / MySql
#### 3389 TCP / RDP
#### 3690 TCP / SVN
#### 5432 TCP / Postregsql
#### 5985 TCP / WinRM
#### 6379 TCP / redis
#### 6697 TCP / irc
#### 27107 TCP / mongodb
#### 11211 TCP / memcache
