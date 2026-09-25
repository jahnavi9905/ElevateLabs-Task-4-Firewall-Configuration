# 🔥 Firewall Configuration and Traffic Filtering

## 🎯 Objective

To configure and test basic firewall rules to allow or block network traffic and understand how firewall rules control network access.

## 🛠️ Tools Used

- **UFW (Uncomplicated Firewall)** – Firewall management tool on Linux
- **Ubuntu 22.04** – Operating system
- **Terminal** – Used to execute firewall commands

## 📋 Task Overview

The goal of this task was to configure and test firewall rules on a Linux system using UFW.

The practical focused on:

- Checking the firewall status
- Enabling UFW
- Listing existing firewall rules
- Blocking inbound traffic on a specific port
- Testing the firewall rule
- Allowing SSH traffic
- Removing the test block rule
- Documenting the firewall commands and results

## 🔧 Step-by-Step Execution

### 1. Check Firewall Status

The UFW firewall status was checked using:

```bash
sudo ufw status
```

UFW was initially disabled, so it was enabled using:

```bash
sudo ufw enable
```

### 2. List Current Firewall Rules

The current firewall configuration was checked using:

```bash
sudo ufw status
```

The output initially showed no specific rules for ports 23 or 22.

### 3. Block Inbound Traffic on Port 23

Port 23, commonly associated with Telnet, was blocked using:

```bash
sudo ufw deny 23/tcp
```

The rule was verified using:

```bash
sudo ufw status
```

Example output:

```text
To                         Action      From
--                         ------      ----
23/tcp                     DENY        Anywhere
23/tcp (v6)                DENY        Anywhere (v6)
```

### 4. Test the Firewall Rule

A Telnet connection to port 23 was attempted from another machine:

```bash
telnet <linux-machine-ip> 23
```

The connection was refused, confirming that the configured firewall rule blocked the traffic.

### 5. Allow SSH Traffic on Port 22

SSH traffic was allowed using:

```bash
sudo ufw allow 22/tcp
```

The firewall configuration was then verified using:

```bash
sudo ufw status
```

Example output:

```text
To                         Action      From
--                         ------      ----
23/tcp                     DENY        Anywhere
22/tcp                     ALLOW       Anywhere
23/tcp (v6)                DENY        Anywhere (v6)
22/tcp (v6)                ALLOW       Anywhere (v6)
```

### 6. Remove the Test Block Rule

After completing the test, the temporary Telnet block rule was removed using:

```bash
sudo ufw delete deny 23/tcp
```

The firewall status was checked again:

```bash
sudo ufw status
```

The final configuration retained the SSH rule.

## 💻 Commands Used

```bash
sudo ufw enable
sudo ufw status
sudo ufw deny 23/tcp
sudo ufw allow 22/tcp
sudo ufw delete deny 23/tcp
```

## 🧠 How a Firewall Filters Traffic

A firewall filters network traffic by evaluating incoming and outgoing connections against predefined rules.

In this practical:

- The `deny 23/tcp` rule blocked inbound TCP traffic on port 23.
- The `allow 22/tcp` rule permitted inbound TCP traffic on port 22.
- UFW provided a simplified interface for managing Linux firewall rules.

## 📚 Key Concepts Demonstrated

- Firewall configuration
- Network traffic filtering
- Inbound traffic control
- Port-based firewall rules
- UFW
- Linux security
- Telnet and SSH ports
- Firewall rule testing
- Security configuration

## 📌 Outcome

This practical demonstrated how to configure and test firewall rules on a Linux system using UFW.

The exercise provided hands-on experience with blocking and allowing specific network traffic, testing firewall behavior, and restoring the firewall configuration after testing.

## ⚠️ Ethical Use

This practical is intended for educational and cybersecurity learning purposes.

Firewall configuration and security testing should only be performed on systems and networks where you have appropriate authorization.

## 👩‍💻 Author

**Jahnavi Pokala**

- GitHub: [jahnavi9905](https://github.com/jahnavi9905)
- LinkedIn: [Jahnavi Pokala](https://www.linkedin.com/in/jahnavi-pokala59/)
