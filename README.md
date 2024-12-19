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
<b>STEP 1</b><br>
While working through this alert, it is important to track what the alert has provided. <b>What should I do first?</b> Well good question. If you head to <b>"CASE PLAYBOOK"</b>, you are provided with details on what you should check for. Examine the rule name. Rule names are usually created specifically for the attack to be detected. By examining the rule name, you can understand which attack you are facing. Detect between which two devices the traffic is occurring. It's a good starting point to understand the situation by learning about the direction of traffic, what protocol is used between devices, etc. Here is the collection data for this alert: <br><br>
Ownership of the IP addresses and devices.<br>
If the traffic is coming from outside (Internet)<br>
Ownership of IP address (Static or Pool Address? Who owns it? Is it web hosting?)<br>
Reputation of IP Address (Search in VirusTotal, AbuseIPDB, Cisco Talos)<br>
If the traffic is coming from the company network;<br>
The hostname of the device<br>
Who owns the device (username)<br>
Last user logon time<br>
<br>
<b>STEP 2</b><br>
Now that I have identified what alert I'm facing, it is important to examine the traffic for any suspicious conditions regarding the web attack payloads. Since attackers do not only attack through URLs, it is mandatory to do my due diligence and examine all of the data to determine if there is a cyber attack. I will now decide whether or not this alert is malicious based on my investigation.<br>

<b>Provided URL:</b> https://172.16.17.18/search/?q=%22%20OR%201%20%3D%201%20--%20-
<br>
If I was to insert this URL within "VirusTotal", I would get results of this link not being malicious. But if you take a closer look at the link, some patterns indicate a possible SQL injection. I went ahead and utilized a URL decoder/encoder called <a href="https://www.urldecoder.org/">URL Decode and Encode</a>. After importing the URL link into the decoder, the results came back as a suspicious injection. <br><b>Results:</b> (https://172.16.17.18/search/?q=" OR 1 = 1 -- -).<br> <b>Attack Type:</b> SQL Injection <br> 

<b>STEP 3</b><br>
After identifying the attack type, it is also important to check if this is a planned test. Why check if this is a planned test? Well, to answer your question, penetration tests or attack simulations can trigger False Positive alarms if the rules are not set correctly.
<br>
<b>Objective:</b>
<br>
<ul>
  <li>Check if there is an email showing that there will be planned work by searching for information such as hostname, username, and IP address on the mailbox.</li>
  <li>Check if the device generating malicious traffic belongs to attack simulation products. If the Hostname contains the name of Attack Simulation products (such as Verodin, AttackIQ, Picus…), these devices belong to Attack Simulation products within the framework of LetsDefend simulation and it is a planned work.</li>
</ul>
<br>
After checking the SIEM, it is safe to say that this was NOT a planned work attack. "Please view attachments for screenshots of findings". The next step is to find out what the direction is traffic this alert is going through. After continuing my investigation, this alert was directed through the <b>Company > Internet</b>. <br>
<b>Source IP:</b> 167.99.169.17 <br>
<b>Destination IP:</b> 172.16.17.18 <br>
<b>Destination Port:</b> 443 <br>
<br>

<b>STEP 4</b><br>
Since it is now detected that the device is compromised, it is important to contain this internal device to avoid any future attacks. By heading to <b>Endpoint Security</b> and requesting to contain the device.<br>
<br>
<b>Summary:</b><br>
I've analyzed the requested URL by decoding it and identified a payload consistent with an SQL Injection attack. Upon URL decoding, it was confirmed that the payload was crafted to exploit an SQL Injection vulnerability. By filtering the source address through the Log Management page, we observed multiple related requests originating from the same source. Further examination of these requests revealed that all were targeting the same SQL Injection vulnerability. Analysis of the response size for each request showed uniformity, with all responses returning a status code of 500. This indicates that the SQL Injection attack was unsuccessful. A successful attack would typically result in varying response sizes and a status code of 200.


