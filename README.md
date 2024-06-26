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

![Screenshot 2024-05-13 11 08 25 AM](https://github.com/mmedinabet/Snort-live-attacks-/assets/142737434/8e452e2b-2fa1-4866-acd0-4a2b72da17ff)

![Screenshot 2024-05-13 11 07 20 AM](https://github.com/mmedinabet/Snort-live-attacks-/assets/142737434/b09db4c9-eaf3-415c-9027-3ee49d328abe)

Narrow down the results by inspecting the packets.

![Screenshot 2024-05-13 11 10 16 AM](https://github.com/mmedinabet/Snort-live-attacks-/assets/142737434/af0c6959-b83f-4eaa-873e-af51870b9465)

![Screenshot 2024-05-13 11 10 45 AM](https://github.com/mmedinabet/Snort-live-attacks-/assets/142737434/f3d12797-a172-45bc-aa06-a91afaa3b985)

![Screenshot 2024-05-13 11 12 27 AM](https://github.com/mmedinabet/Snort-live-attacks-/assets/142737434/69276501-5463-4af0-a2ae-fdc9a4ad857a)

![Screenshot 2024-05-13 11 14 13 AM](https://github.com/mmedinabet/Snort-live-attacks-/assets/142737434/f77d6388-c579-4a50-aeef-167df140d62b)

Write an IPS Rule:

Open the local.rules file using sudo gedit /etc/snort/rules/local.rules.
Write a rule to drop traffic targeting port 22:

drop tcp any 22 <> any any (msg:"SSH Connection attempted"; sid:100001; rev:1;)

Run Snort in IPS Mode:

Run Snort in IPS mode using:

![Screenshot 2024-05-13 11 18 32 AM](https://github.com/mmedinabet/Snort-live-attacks-/assets/142737434/93c90a69-2881-42ec-bffe-0d1bdfd3b043)

sudo snort -c /etc/snort/snort.conf -q -Q --daq afpacket -i eth0:eth1 -A full

![Screenshot 2024-05-13 11 20 40 AM](https://github.com/mmedinabet/Snort-live-attacks-/assets/142737434/99a4334a-234a-43fd-b7ad-8fb7003717c3)

Wait for the flag.txt file to appear on the desktop.
Stop Snort with ctrl + c.
Open flag.txt to retrieve the flag.

Answer Questions:
- What is the name of the service under attack? (Answer: SSH)
- What is the used protocol/port in the attack? (Answer: TCP/22)

<h2> Scenario 2 - Reverse-Shell </h2>
Objective: Identify and defend against a reverse shell attack.

Start Snort in Sniffer Mode:

![Screenshot 2024-05-13 11 46 17 AM](https://github.com/mmedinabet/Snort-live-attacks-/assets/142737434/19681547-315a-40fb-87ef-ea109a9d0c31)

Repeat steps 1 and 2 from Scenario 1.

![Screenshot 2024-05-13 11 48 25 AM](https://github.com/mmedinabet/Snort-live-attacks-/assets/142737434/1e5fc1c8-af3b-41c1-8b4d-5c5dd5a7ca88)

![Screenshot 2024-05-13 11 50 01 AM](https://github.com/mmedinabet/Snort-live-attacks-/assets/142737434/c768692d-1f41-43ec-ba55-0060d45abd19)

![Screenshot 2024-05-13 11 50 14 AM](https://github.com/mmedinabet/Snort-live-attacks-/assets/142737434/5c43b820-5e57-4cb8-92bd-7a248581bef2)

![Screenshot 2024-05-13 11 53 01 AM](https://github.com/mmedinabet/Snort-live-attacks-/assets/142737434/33b340ff-cfa8-4b74-9432-d05bb5b69280)

![Screenshot 2024-05-13 11 54 31 AM](https://github.com/mmedinabet/Snort-live-attacks-/assets/142737434/e4ffc26c-c5a9-4a81-80e7-5c842551eece)


Write an IPS Rule to drop traffic targeting port 4444:

![Screenshot 2024-05-13 11 57 13 AM](https://github.com/mmedinabet/Snort-live-attacks-/assets/142737434/a98abf35-5c05-47c9-ade5-ae64383da148)

Run Snort in IPS Mode:
![Screenshot 2024-05-13 12 02 13 PM](https://github.com/mmedinabet/Snort-live-attacks-/assets/142737434/ef520d84-3056-41ec-9d4c-6d40fa7e29f9)


Repeat step 4 from Scenario 1.
Answer Questions:

- What is the used protocol/port in the attack? (Answer: TCP/4444)
- Which tool is highly associated with this specific port number? (Answer: Metasploit)

<h2>Conclusion</h2>

In conclusion, the "Defending Against Live Attacks with Snort" lab provides invaluable practical experience in network security and intrusion detection. By mastering the usage of Snort and understanding its capabilities in thwarting real-time attacks, I am better equipped to defend networks against evolving cyber threats. Vigilance and proactive defense are key to maintaining the integrity and security of digital assets in today's interconnected world.

Takeaways:
- Familiarity with Snort as an intrusion detection system.
- Understanding of how to detect and mitigate brute-force and reverse-shell attacks.
- Importance of crafting effective IPS rules for network defense.
- Appreciation for continuous monitoring and proactive security measures in defending against live cyber threats.


