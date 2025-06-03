# Firewall Setup & Testing Guide (Windows)

## 📌 Overview
This guide provides step-by-step instructions for setting up, testing, and verifying firewall rules on **Windows Defender Firewall** to allow or block network traffic.

---

## 🔹 Windows Firewall Setup

### **1. Check Existing Firewall Rules**
Run this in **PowerShell** to list firewall rules related to Telnet:

Using Powershell:
```
Get-NetFirewallRule | Where-Object { $_.DisplayName -like "*Telnet*" }
```

### **2. Block Telnet (Port 23) **

Using PowerShell:
```  
New-NetFirewallRule -DisplayName "Block Telnet" -Direction Inbound -Action Block -Protocol TCP -LocalPort 23
```

Using Command Prompt (Netsh):
```
netsh advfirewall firewall add rule name="Block Telnet" dir=in action=block protocol=TCP localport=23
```

### **3. Block Outbound Telnet Traffic **
```
netsh advfirewall firewall add rule name="Block Telnet" dir=out action=block protocol=TCP remoteport=23
```

### **4. Verify Firewall Rules **
```
netsh advfirewall firewall show rule name="Block Telnet"
```


### **5. Test Telnet Connection **

Attempt to connect:
```
telnet telehack.com 23
```


![Screenshot (661)](https://github.com/user-attachments/assets/87d02aa8-682f-4d72-ab45-106546d2f2d7)



***If blocked, the firewall is working!***

### **6. Remove Firewall Rule**

If needed, delete the rule:
```
netsh advfirewall firewall delete rule name="Block Telnet"
```

![Screenshot (659)](https://github.com/user-attachments/assets/0cc3ef4b-b0e7-4f7e-ac92-a55310c6724f)


***if anyone is looking for linux commands can check in the report section***
