# 🔐 Windows Firewall Lab: Blocking Telnet (Port 23)

## Objective
Configure and test a basic firewall rule on Windows to block inbound traffic on port 23 (Telnet), verify its effect, and document the process.

---

## Steps Performed

### 1. Open Windows Firewall
- Open Run (`Win + R`) → type `wf.msc` → press Enter.
- This opens **Windows Defender Firewall with Advanced Security**.

### 2. List Current Rules
- Navigate to **Inbound Rules**.
- Reviewed existing rules before making changes.

### 3. Create Block Rule for Port 23
- Right-click **Inbound Rules → New Rule**.
- Select:
  - **Rule Type**: Port
  - **Protocol**: TCP
  - **Port**: 23
  - **Action**: Block the connection
  - **Profile**: All
  - **Name**: Block Telnet

### 4. Test the Rule
Used PowerShell to verify the rule:
```powershell
Test-NetConnection -ComputerName localhost -Port 23 
```
Expected Result:
TcpTestSucceeded : False
Confirms that port 23 is blocked or no service is listening.
