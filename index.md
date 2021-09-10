## Free Knowledge

Comptia A+, Network+, and Security+ | Avidly pursuing OSCP.

### Contents:
- Notes:
  - [Enumeration](/Port_Enumeration.md) (ports and their services)
  - Windows PrivEsc
  - Linux PrivEsc
  - Web application attacks
  - Port Forwarding and Tunnelling
  - Reverse Shells
  - Password Attacks
  - Encryption
  - Antivirus Evasion
  - Client Side Attacks
  - Buffer Overflows (OSCP Style)
- Walkthroughs from:
  - Hack The Box
  - Proving Grounds
  - Vulnhub



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
  
  - Most common attack is brute forcing
    - Tools:
      - Hydra - brute force username:password combinations
      - Crowbar - brute force using private keys
     - Brute forcing can lock you out, possibly for a set period of time.
  - Sometimes password prompt is diabled and login is only allowed by using a private key
  - SSH Key fingerprint
    - Used for easy identification of the keys you are connecting to
  - Usually located /etc/ssh/ssh_host_rsa_key.pub

|||
  | ------------- | ------------- |
  | Connect with different key exchange algorithm | -oKexAlgorithms=+\<algorithm\> |
  |Allow to connect with a different type of key|-oPubkeyAcceptedKeyTypes=+\<key type - example: ssh-dss\>|
  
</details>
