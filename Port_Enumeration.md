<!DOCTYPE html>
<html>
<head>
    <title>Enumerating Ports & Services</title>
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
<ul>Output all open ports to comma separated list:
    <li>sudo nmap -p- &lt;ip address&gt; -oA &lt;output name&gt;</li>
    <li>cat &lt;nmap scan&gt;.nmap | grep open | awk -F/ '{print $1}' ORS=','</li>
</ul>


</body>
</html>

