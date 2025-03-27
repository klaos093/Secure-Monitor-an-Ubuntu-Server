Report: Secure & Monitor an Ubuntu Server  

1️⃣ Introduction  

This project simulates the setup, hardening, and monitoring of an Ubuntu server to replicate real-world cybersecurity tasks. By implementing key security measures, such as a firewall, SSH hardening, and intrusion detection, the project demonstrates practical skills required for system administrators and SOC analysts.  

 Key goals include:

-Securing the server through hardening techniques.  
-Monitoring the server with security tools and analyzing logs for potential threats.  
-Documenting findings in a professional manner.

2️⃣ Setup Process Environment Local Virtual Machine:

VirtualBox was used to set up Ubuntu Server 24.04.

Resources: 2GB RAM and 20GB storage.

Server Configuration:

UFW firewall and Fail2Ban installed.

SSH configuration updated to disable root login and change the default port.

3️⃣ Security Hardening

The following steps were applied to harden the server:

Firewall (UFW) Configuration Allowed only necessary ports:

``sudo ufw allow OpenSSH``  
``sudo ufw enable``

SSH Security Disabled root login by updating the SSH configuration file:

``PermitRootLogin no``

Changed the default SSH port from 22 to 2222:

``Port 2222``

Fail2Ban Setup Installed and configured Fail2Ban to prevent brute-force attacks:

``sudo apt install fail2ban -y``  
``sudo systemctl enable fail2ban``  
4️⃣ Monitoring & Analysis  

Log Auditing with Fail2Ban Results:  

 Fail2Ban identified and blocked repeated SSH login attempts from the IP 192.168.1.168. The following entries were observed:

``2025-03-25 20:47:45,814 fail2ban.actions [1267]: NOTICE  [sshd] Ban 192.168.1.168 Authentication Log Analysis``

Findings: The auth.log revealed failed login attempts from 192.168.1.168, indicating repeated unauthorized access attempts. Example entries:  

``2025-03-25T20:47:44.704297+00:00 Server01 sshd[4016]: Failed password for server from 192.168.1.168 port 58496 ssh2``  
``2025-03-25T20:47:47.432418+00:00 Server01 sshd[4021]: Failed password for server from 192.168.1.168 port 58520 ssh2``  

5️⃣ Simulated Attacks  

A brute-force attack was simulated using Hydra to test the server's defense mechanisms:

Fail2Ban successfully detected and blocked the attacker after multiple failed login attempts.

Analysis confirmed that Fail2Ban prevented unauthorized access effectively.

6️⃣ Conclusion  

This project successfully showcased the following:

-Setting up a secure and hardened server environment.  
-Implementing security monitoring tools like Fail2Ban and log auditing.  
-Testing server defenses through simulated attacks and analyzing logs for security events.  

By completing this project, valuable skills in system hardening, monitoring, and incident response were demonstrated. This report can serve as a portfolio entry to highlight real-world cybersecurity practices.
