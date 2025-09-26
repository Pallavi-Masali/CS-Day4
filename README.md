# CS-Day4
Steps in Ubuntu (Using UFW):-
1. Check if UFW is installed and enabled:    sudo ufw status
    If you see Status: inactive, UFW is installed but not enabled.
If UFW is not installed:   sudo apt update
                           sudo apt install ufw -y
   
2. Enable UFW:      sudo ufw enable
Incoming: Deny
Outgoing: Allow

3. List current firewall rules:   sudo ufw status numbered

4. Block inbound traffic on a specific port (e.g., Telnet on port 23):     sudo ufw deny 23/tcp
This blocks any incoming Telnet traffic.

5. Test the block rule
Try to connect locally or remotely using:      telnet localhost 23
You should see connection refused.

6. Allow SSH (port 22):    sudo ufw allow 22/tcp
Now SSH remains accessible.

7. Remove the test block rule
First, list rules:    sudo ufw status numbered
Then delete the rule by its number, e.g.:   sudo ufw delete <rule-number>
(Example: sudo ufw delete 2)

8. Summarize how firewall filters traffic
UFW works as a frontend for iptables.
It filters network packets based on defined rules:
ALLOW → lets traffic through (example: SSH port 22).
DENY/REJECT → blocks traffic (example: Telnet port 23).
Rules are applied in order of priority, with default deny incoming to protect the system.
