# Setup-and-Use-a-Firewall-on-Windows-Linux
# Understand What i'm Doing
A firewall filters network traffic based on rules — it can allow or block traffic on specific ports, protocols, or IPs.
Listing existing rules
Blocking Telnet - port 23
Allowing SSH - port 22 on Linux
Testing the rules
Removing the rules
#  I'm on Windows step-bye-step
1. Open Windows Firewall 
Press Windows Key + S → type Windows Defender Firewall with Advanced Security → open it.
In the left panel, click Inbound Rules.
2. List Rules
Scroll through to see existing rules
3. Block Telnet (Port 23)
In Inbound Rules → click New Rule… (right-hand panel).
Select Port → Next.
Select TCP → enter 23 → Next.
Choose Block the connection → Next.
Apply to all profiles → Next.
Named it: Block Telnet Port 23 → Finish.
4. Test the Rule
Open Command Prompt and run:
telnet localhost 23
5. Remove Rule
Right-click Block Telnet Port 23 → Delete.

# If i'm on Linux (UFW) step-bye-step 
1. Install UFW
sudo apt update
sudo apt install ufw
2. Check Status & List Rules
sudo ufw status verbose
3. Enable UFW
sudo ufw enable
4. Block Telnet (Port 23)
sudo ufw deny 23/tcp
5. Allow SSH (Port 22)
sudo ufw allow 22/tcp
6. Test the Rules
From the same machine:
nc -zv localhost 23   # Should be blocked
nc -zv localhost 22   # Should be allowed
7. Remove Test Rule
sudo ufw delete deny 23/tcp
# A short summary:
The firewall was configured to block inbound Telnet (TCP 23) connections and allow SSH (TCP 22).
Testing confirmed blocked Telnet access and successful SSH connectivity.
This demonstrates basic inbound rule management and the ability to filter traffic based on ports.
