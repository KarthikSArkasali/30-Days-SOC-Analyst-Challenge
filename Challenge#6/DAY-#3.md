# Day-#3: EDR Basics: Detecting SSH Brute Force attack
## Objective:
The objective of this task was to detect SSH brute-force attacks on an Ubuntu machine using Wazuh’s security monitoring capabilities. I simulated an SSH brute-force attack, analyzed logs, and detected suspicious authentication attempts through Wazuh alerts.

## Preparation: Configure Wazuh Agent on Ubuntu Target Machine
### Requirements
- Wazuh Server: Installed and running (Refer to Task #26).
- Ubuntu 22.04/20.04 (Target Machine).
- Wazuh Agent installed on the Ubuntu machine.
- SSH enabled on the target machine.
- Admin or sudo access on the target machine.

**Step 1: Install Wazuh Agent on Ubuntu**

1. Download and install the Wazuh Agent on the target machine:

        curl -sO https://packages.wazuh.com/4.7/wazuh-agent-linux.sh && sudo bash wazuh-agent-linux.sh

2. Configure the agent to connect to the Wazuh Server:

       sudo nano /var/ossec/etc/ossec.conf

- Locate and set it to the Wazuh Server IP:

      <address>WAZUH-SERVER-IP</address>

3. Restart the Wazuh Agent service:

       sudo systemctl restart wazuh-agent

## Attack Simulation & Detection

**Step 1: Simulate an SSH Brute-Force Attack Using Hydra**

1. From the attacker machine, install Hydra:

       sudo apt update && sudo apt install hydra -y

2. Run the following command to simulate an SSH brute-force attack:

       hydra -l ubuntu -P /usr/share/wordlists/rockyou.txt <target-IP> ssh

- Replace `<target-IP>` with the Ubuntu target machine’s IP address.
- `-l ubuntu` specifies the username to attack.
- `-P /usr/share/wordlists/rockyou.txt` uses a password list for brute-forcing SSH.

3. If a valid password is found, Hydra will display:

       [22][ssh] host: <target-IP> login: ubuntu password: <password>

**Step 2: Detect SSH Brute Force Attempts in Wazuh**
1. Open the Wazuh Dashboard (http://:5601).
2. Navigate to Security Events and run below query

       rule.id:(5551 OR 5712)

3. Look for logs indicating:
   - Multiple failed SSH login attempts from the same IP.
   - High volume of authentication failures in a short period.
   - Successful logins after repeated failed attempts (possible compromise).

## Conclusion
- Successfully configured Wazuh Agent on an Ubuntu machine for SSH monitoring.
- Simulated SSH brute-force attacks using Hydra.
- Detected brute-force attempts in Wazuh logs and alerts.
- Learned how SOC analysts investigate authentication attacks using SIEM tools.

## Submission
- Share a screenshot of the Wazuh dashboard showing SSH brute-force detection alerts.

  ![1](https://github.com/user-attachments/assets/a1bab583-38d1-4b59-8c04-830ee5c8dabe)

- Share a screenshot of logs confirming multiple failed SSH attempts.

  ![2](https://github.com/user-attachments/assets/0008d74b-60f3-47ab-9711-71a5890e19c6)

- Write a short observation on how SSH brute-force detection helps in security monitoring and threat prevention.

  **SSH brute-force** detection helps in security monitoring by identifying repeated failed login attempts to a server. These attempts are often made by 
  attackers trying to guess a user's password. Detecting such activity early allows security teams to block the attacker's IP address, apply rate-limiting, or 
  enforce stronger authentication. This helps prevent unauthorized access and protects the system from potential compromise.
