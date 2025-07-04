# Task 4 Report: Setup and Use a Firewall on Windows/Linux

**Objective:** Configure and test basic firewall rules to allow or block traffic.  
**Tools Used:** UFW (Uncomplicated Firewall) on Linux.  
**Deliverable:** Screenshots showing firewall rules applied.

---

## Task Overview

The goal of this task was to configure and test firewall rules on Linux systems, focusing on blocking and allowing specific network traffic. The task involved working with UFW on Linux, following a structured set of steps to manage firewall rules, test them, and document the process. The outcome aimed to demonstrate basic firewall management skills and an understanding of network traffic filtering.

---

## Step-by-Step Execution

### 1. Open Firewall Configuration Tool
- **UFW (Linux):** On a Linux system (Ubuntu 22.04), I opened a terminal and checked the status of UFW using the command:
  ```
  sudo ufw status
  ```
  UFW was initially disabled, so I enabled it with:
  ```
  sudo ufw enable
  ```

---

### 2. List Current Firewall Rules
- **UFW (Linux):** I ran the following command to list the current UFW rules:
  ```
  sudo ufw status
  ```
  The output showed no specific rules for ports 23 or 22 initially.

---

### 3. Add a Rule to Block Inbound Traffic on a Specific Port (Port 23 for Telnet)
- **UFW (Linux):** I added a rule to block inbound traffic on port 23 with the command:
  ```
  sudo ufw deny 23/tcp
  ```
  I verified the rule with `sudo ufw status`, which showed:
  ```
  To                         Action      From
  --                         ------      ----
  23/tcp                     DENY        Anywhere
  23/tcp (v6)                DENY        Anywhere (v6)
  ```

---

### 4. Test the Rule by Attempting to Connect to That Port Locally or Remotely
- **UFW (Linux):** On the Linux system, I used another machine to attempt a Telnet connection to port 23:
  ```
  telnet <linux-machine-ip> 23
  ```
  The connection was refused, confirming the UFW rule successfully blocked the traffic.

---

### 5. Add a Rule to Allow SSH (Port 22) if on Linux
- **UFW (Linux):** I added a rule to allow inbound traffic on port 22 for SSH:
  ```
  sudo ufw allow 22/tcp
  ```
  I verified the rule with `sudo ufw status`, which showed:
  ```
  To                         Action      From
  --                         ------      ----
  23/tcp                     DENY        Anywhere
  22/tcp                     ALLOW       Anywhere
  23/tcp (v6)                DENY        Anywhere (v6)
  22/tcp (v6)                ALLOW       Anywhere (v6)
  ```

---

### 6. Remove the Test Block Rule to Restore Original State
- **UFW (Linux):** I removed the rule blocking port 23 with:
  ```
  sudo ufw delete deny 23/tcp
  ```
  I confirmed the removal with `sudo ufw status`, which now only showed the SSH rule.

---

### 7. Document Commands or GUI Steps Used
- **UFW (Commands):**
  ```
  sudo ufw enable
  sudo ufw status
  sudo ufw deny 23/tcp
  sudo ufw allow 22/tcp
  sudo ufw delete deny 23/tcp
  ```

---

### 8. Summarize How Firewall Filters Traffic
Firewalls filter traffic by evaluating packets against predefined rules. In this task:
- **UFW (Linux):** UFW uses iptables under the hood to filter traffic. The `deny 23/tcp` rule dropped all inbound TCP packets on port 23, while `allow 22/tcp` permitted SSH traffic. UFW simplifies rule management by providing a user-friendly interface for iptables.

---

## Outcome
This task successfully demonstrated the ability to configure and test firewall rules on Linux systems. I gained hands-on experience with  UFW, learning how to block and allow specific traffic, test rules, and restore the original state. The process enhanced my understanding of network traffic filtering and the role of firewalls in securing systems.
