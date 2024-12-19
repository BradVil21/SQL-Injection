# SQL Injection Payload Detected 

<div>
  <b>SEVERITY:</b> HIGH | <b>DATE:</b> Feb, 25, 2022, (11:34 AM) | <b>RULE NAME:</b> SOC165 - Possible SQL Injection Payload Detected | <b>TYPE:</b> Web Attack
    <br>
  <br>
  <b>EventID:</b> 115
  <br>
  <b>Event Time:</b> Feb, 25, 2022, 11:34 AM
  <br>
  <b>Rule:</b> SOC165 - Possible SQL Injection Payload Detected
  <br>
  <b>Level:</b> Security Analyst
  <br>
  <b>Source Address:</b> 167.99.169.17
  <br>
  <b>Source Hostname:</b> WebServer1001
  <br>
  <b>Destination Address:</b> 172.16.17.18
  <br>
  <b>HTTP Request Method:</b> GET
  <br>
  <b>Alert Trigger Reason:</b> Requested URL Contains OR 1 = 1
  <br>
  <b>Request URL:</b> [http://mogagrocol.ru/wp-content/plugins/akismet/fv/index.php?email=ellie@letsdefend.io](https://172.16.17.18/search/?q=%22%20OR%201%20%3D%201%20--%20-)
  <br>
  <b>User Agent:</b> Mozilla/5.0 (Windows NT 6.1; WOW64; rv:40.0) Gecko/20100101 Firefox/40.1
  <br>
  <b>Device Action:</b> Allowed
</div>
<br>
[Introduction: This repository aims to analyze, detect, and prevent SQL injection attacks within web applications. By integrating detection mechanisms into an existing web environment, we can monitor for suspicious SQL injection activity, log attacks in real time, and implement preventive measures to safeguard sensitive data. The primary goal is to recognize potential SQL injection attacks as early as possible, allowing for swift remediation.]
<br>
<br>
Please also use this as a guide on how to work phishing alerts using Let's Defend. For any questions or concerns you can <b>CONTACT</b> me directly on <a href= "https://www.linkedin.com/in/bradley-vilsaint-414329267/">LinkedIn</a> or email <a href="info@letsdefend.io">info@letsdefend.io</a> for support.
<br>
<br>
<b>STEP 1</b><be>
While working through this alert, it is important to keep track of what the alert has provided. <b>What should I do first?</b> Well good question. If you head to <b>"CASE PLAYBOOK"</b>, you are provided with details on what you should check for. Examine the rule name. Rule names are usually created specifically for the attack to be detected. By examining the rule name, you can understand which attack you are facing. Detect between which two devices the traffic is occurring. It's a good starting point to understand the situation by learning about the direction of traffic, what protocol is used between devices, etc. Here is the collection data for this alert: <br><br>
Ownership of the IP addresses and devices.<br>
If the traffic is coming from outside (Internet)<br>
Ownership of IP address (Static or Pool Address? Who owns it? Is it web hosting?)<br>
Reputation of IP Address (Search in VirusTotal, AbuseIPDB, Cisco Talos)<br>
If the traffic is coming from the company network;<br>
The hostname of the device<br>
Who owns the device (username)<br>
Last user logon time<br>
