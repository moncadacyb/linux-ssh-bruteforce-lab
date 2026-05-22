# 🛡️ Linux SSH Brute Force Detection & Response Lab

## 📌 Overview

This project simulates a Blue Team security scenario where an Ubuntu Server is targeted by SSH brute force attempts from a Kali Linux attacker machine.

The objective of the lab is to detect malicious authentication attempts, analyze Linux logs, identify attacker activity, and apply defensive measures using native Linux security tools.

---

# 🏗️ Lab Architecture

## 🖥️ Ubuntu Server (RED)
- Target system
- SSH server enabled
- Authentication logs analyzed
- UFW firewall configured

## 💻 Kali Linux
- Attacker machine
- SSH brute force simulation
- Failed login attempts generation

---

# 🎯 Objectives

- Simulate SSH brute force attacks
- Analyze Linux authentication logs
- Detect attacker IP addresses
- Monitor logs in real time
- Apply firewall mitigation using UFW

---

# ⚔️ Attack Simulation

SSH connection from Kali Linux to Ubuntu Server:

```bash
ssh RED@192.168.1.146
```

Simulated brute force attempts:

```bash
ssh root@192.168.1.146

ssh admin@192.168.1.146

ssh test@192.168.1.146
```

---

# 🔍 Detection & Analysis

## Failed password detection

```bash
grep "Failed password" /var/log/auth.log
```

---

## Extract attacker IP addresses

```bash
grep "Failed password" /var/log/auth.log | awk '{print $(NF-3)}' | sort | uniq -c
```

---

## Real-time log monitoring

```bash
tail -f /var/log/auth.log
```

---

## Search SSH events

```bash
grep "ssh" /var/log/auth.log
```

---

# 🛡️ Incident Response

## Firewall status verification

```bash
sudo ufw status verbose

sudo ufw status numbered
```

---

## Block attacker IP

```bash
sudo ufw deny from 192.168.1.102
```

---

# 📸 Evidence

The project includes screenshots of:

- Successful SSH connectivity
- Failed login attempts
- Real-time log monitoring
- SSH log analysis
- UFW firewall configuration
- Attacker IP blocking
- Blocked SSH access from Kali Linux

---

# 📊 Key Findings

- SSH services are common attack targets
- Linux authentication logs provide valuable forensic data
- Real-time monitoring improves incident visibility
- UFW can be used for fast attack mitigation
- Native Linux tools are effective for basic SOC operations

---

# 🔄 Incident Workflow

1. Kali Linux established SSH connectivity with Ubuntu Server
2. Multiple failed login attempts were generated
3. Authentication logs recorded attacker activity
4. Logs were analyzed using grep and awk
5. Attacker IP address identified
6. UFW firewall rule applied
7. SSH access blocked successfully

---

# 🚀 Conclusion

This project demonstrates a basic Blue Team / SOC workflow using native Linux tools.

The lab simulates:

Attack → Detection → Analysis → Response → Containment

It provides hands-on experience in Linux security monitoring, SSH attack detection, and incident response.
