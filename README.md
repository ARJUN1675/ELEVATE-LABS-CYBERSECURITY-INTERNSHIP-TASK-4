# ELEVATE-LABS-CYBERSECURITY-INTERNSHIP-TASK-4

---

#  Firewall Configuration and Testing (Windows Firewall)

This project demonstrates how to configure and test **basic firewall rules** using **Windows Firewall with Advanced Security**.

---

##  Objectives

* Configure firewall rules to allow or block traffic.
* Test rules using Telnet.
* Restore firewall to its original state.

---

##  Tools Used

* **Windows Defender Firewall with Advanced Security**
* **Telnet Client** (Windows feature)

---

##  Steps Performed

### 1. Open Firewall Configuration Tool

* Press `Win + R` → type `wf.msc` → press **Enter**.
* Opens **Windows Defender Firewall with Advanced Security**.

### 2. List Current Firewall Rules

* Select **Inbound Rules** → shows existing firewall rules.
* Screenshot this for documentation.

### 3. Add Rule to Block Telnet (Port 23)

* Right-click **Inbound Rules** → **New Rule**.
* Select **Port** → TCP → Specify port **23**.
* Choose **Block the connection** → Apply to Domain/Private/Public.
* Name it `Block Telnet`.

### 4. Test Blocked Port

* Open **Command Prompt** and run:

  ```cmd
  telnet <IP> 23
  ```
* Expected result:

  ```
  Connecting to <IP>...
  Could not open connection to the host, on port 23: Connect failed
  ```

### 5. Remove the Test Rule

* Right-click the `Block Telnet` inbound rule → Delete.

### 6. Verify Restored State

* Run the same test again:

  ```cmd
  telnet <IP> 23
  ```
* If Telnet service is running, it should now connect.
* If not, you’ll see "connection refused," but **not due to firewall**.

---

##  Test Results Log

**Before rule applied**

* Telnet connection not blocked by firewall.

**After adding rule (`Block Telnet`)**

```cmd
C:\> telnet localhost 23
Connecting to 192.168.1.100...
Could not open connection to the host, on port 23: Connect failed
```

**After deleting rule**

```cmd
C:\> telnet localhost 23
Connecting to 192.168.1.100...
(If Telnet service running, connection succeeds. If not, connection refused but firewall no longer blocks it.)
```

---

##  How Windows Firewall Filters Traffic

* Windows Firewall checks **inbound and outbound packets** against defined rules.
* Rules can be created to **allow** or **block** traffic based on:

  * **Port numbers** (e.g., 23 for Telnet, 80 for HTTP)
  * **Protocols** (TCP/UDP)
  * **Application executables**
* Example:

  * Rule `Block Telnet` → stops inbound Telnet traffic.
  * Rule `Allow Port 80` → permits web traffic.

---

##  Deliverables

* Screenshot of the inbound rule list with `Block Telnet`.
* Screenshot of failed Telnet connection.
* Screenshot after removing the rule (restored state).

---

## ✅ Conclusion

This exercise demonstrated how to:

* Create and apply a firewall rule in Windows,
* Verify the rule by testing blocked traffic,
* Safely remove the rule to restore normal operation.

---
