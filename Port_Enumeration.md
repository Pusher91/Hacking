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
    <li>cat &lt;nmap scan&gt; | grep open | awk -F/ '{print $1}' ORS=','</li>
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
                    </ul></li>
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
</tr>


</body>
</html>

