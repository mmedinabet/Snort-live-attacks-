<h1> Lab: Defending Against Live Attacks with Snort </h1>

In this hands-on experience, the cybersecurity analyst will delve into the world of network security by using Snort, a renowned intrusion detection system, to defend against real-time attacks. Throughout this lab, you'll encounter two scenarios where you'll be tasked with identifying and mitigating malicious activities targeting specific services and ports.

<h2>Scenario 1 - Brute-Force</h2>
Objective: Identify and defend against a brute-force attack targeting SSH.

Start Snort in Sniffer Mode:

Open the terminal in the provided VM.
Run Snort in sniffer mode using the command: sudo snort -v -l ..

![Screenshot 2024-05-13 11 01 18 AM](https://github.com/mmedinabet/Snort-live-attacks-/assets/142737434/7fc8365a-e3e6-429f-8c7c-76e7b196b02c)

Let it run for 10-15 seconds, then stop it with ctrl + c.
Analyze Captured Traffic:

![Screenshot 2024-05-13 11 01 34 AM](https://github.com/mmedinabet/Snort-live-attacks-/assets/142737434/b9d45fb6-d9a9-451e-b1a8-523a95c4d5a1)

Use the command sudo snort -r snort.log.<timestamp> -X to view captured traffic.

![Screenshot 2024-05-13 11 04 39 AM](https://github.com/mmedinabet/Snort-live-attacks-/assets/142737434/2d9398c8-1e41-4b6e-b715-374829d87947)

Look for packets involving port 22 (SSH) using grep.
Narrow down the results by inspecting the packets.
Write an IPS Rule:

Open the local.rules file using sudo gedit /etc/snort/rules/local.rules.
Write a rule to drop traffic targeting port 22:

drop tcp any 22 <> any any (msg:"SSH Connection attempted"; sid:100001; rev:1;)

Run Snort in IPS Mode:

Run Snort in IPS mode using:

sudo snort -c /etc/snort/snort.conf -q -Q --daq afpacket -i eth0:eth1 -A full

Wait for the flag.txt file to appear on the desktop.
Stop Snort with ctrl + c.
Open flag.txt to retrieve the flag.

Answer Questions:
What is the name of the service under attack? (Answer: SSH)
What is the used protocol/port in the attack? (Answer: TCP/22)

<h2> Scenario 2 - Reverse-Shell </h2>
Objective: Identify and defend against a reverse shell attack.

Start Snort in Sniffer Mode:

Repeat steps 1 and 2 from Scenario 1.
Write an IPS Rule:

Open the local.rules file.
Write a rule to drop traffic targeting port 4444:
sql
Copy code
drop tcp any 4444 <> any any (msg:"Reverse Shell Detected"; sid:100001; rev:1;)
Save and close the file.
Run Snort in IPS Mode:

Repeat step 4 from Scenario 1.
Answer Questions:

What is the used protocol/port in the attack? (Answer: TCP/4444)
Which tool is highly associated with this specific port number? (Answer: Metasploit)

<h2>Conclusion</h2>

In conclusion, the "Defending Against Live Attacks with Snort" lab provides invaluable practical experience in network security and intrusion detection. By mastering the usage of Snort and understanding its capabilities in thwarting real-time attacks, I am better equipped to defend networks against evolving cyber threats. Vigilance and proactive defense are key to maintaining the integrity and security of digital assets in today's interconnected world.

Takeaways:
- Familiarity with Snort as an intrusion detection system.
- Understanding of how to detect and mitigate brute-force and reverse-shell attacks.
- Importance of crafting effective IPS rules for network defense.
- Appreciation for continuous monitoring and proactive security measures in defending against live cyber threats.


