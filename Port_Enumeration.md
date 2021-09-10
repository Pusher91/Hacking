<!DOCTYPE html>
<html>
<head>
    <title>Enumerating Ports & Services</title>
</head>

<hr>

<body>

    <h1>Enumerating Ports & Services</h1>

<hr>

    <p>Port Scanning</p>
    <pre>
    - If tools can't find service version then use wireshark.
    - Running scan with -sV and -sC at the same time or each separately can give different responses in some cases.
    - If UDP shows open|filtered then run scripts with sC.  This will be more likely to get a response from the port to confirm if it is open or not
Sometimes open ports only show up while using -sT (rare.  Maybe only an ISAKMP/ipsec issue?)
</pre>

</body>
</html>

