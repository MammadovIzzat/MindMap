Got it! Here's a revised list that specifies whether each command should be run in Command Prompt (cmd) or PowerShell, and whether it requires administrative privileges or can be run as a normal user.

### Windows Commands

1. **Whoami**
   - **Command**: `whoami`
   - **Environment**: CMD / PowerShell
   - **Privileges**: Normal User

2. **Echo %username%**
   - **Command**: `echo %username%`
   - **Environment**: CMD
   - **Privileges**: Normal User

3. **Userinfo**
   - **Command**: `net user %username%`
   - **Environment**: CMD / PowerShell
   - **Privileges**: Normal User

4. **Privileges**
   - **Command**: `whoami /priv`
   - **Environment**: CMD / PowerShell
   - **Privileges**: Normal User

5. **Groups**
   - **Command**: `whoami /groups`
   - **Environment**: CMD / PowerShell
   - **Privileges**: Normal User

6. **Local Group Membership**
   - **Command**: `net localgroup`
   - **Environment**: CMD / PowerShell
   - **Privileges**: Normal User

7. **Logged on Users**
   - **Command**: `query user`
   - **Environment**: CMD / PowerShell
   - **Privileges**: Normal User

8. **Environment Variables**
   - **Command**: `set`
   - **Environment**: CMD
   - **Privileges**: Normal User

   - **Command**: `Get-ChildItem Env:`
   - **Environment**: PowerShell
   - **Privileges**: Normal User

9. **User SID**
   - **Command**: `whoami /user`
   - **Environment**: CMD / PowerShell
   - **Privileges**: Normal User

10. **Logon Events**
    - **Command**: `wevtutil qe Security /q:"*[System/EventID=4624]" /f:text /rd:true /c:1`
    - **Environment**: CMD / PowerShell
    - **Privileges**: Admin

11. **List All Users**
    - **Command**: `net user`
    - **Environment**: CMD / PowerShell
    - **Privileges**: Normal User

12. **Check Current User Token Privileges**
    - **Command**: `whoami /all`
    - **Environment**: CMD / PowerShell
    - **Privileges**: Normal User

### Additional Commands for Admin Users

13. **List Local Administrators Group Members**
    - **Command**: `net localgroup administrators`
    - **Environment**: CMD / PowerShell
    - **Privileges**: Admin

14. **Detailed User Account Information**
    - **Command**: `wmic useraccount where name='%username%' get /all`
    - **Environment**: CMD / PowerShell
    - **Privileges**: Admin

15. **Audit Policies**
    - **Command**: `auditpol /get /category:*`
    - **Environment**: CMD / PowerShell
    - **Privileges**: Admin

### PowerShell Specific Commands

16. **Get Current User Information**
    - **Command**: `Get-WmiObject -Class Win32_ComputerSystem`
    - **Environment**: PowerShell
    - **Privileges**: Normal User

17. **Get Process Owner**
    - **Command**: `Get-Process | Select-Object -Property Id,ProcessName,@{Name="Owner";Expression={(Get-WmiObject Win32_Process -Filter "ProcessId=$($_.Id)").GetOwner().User}}`
    - **Environment**: PowerShell
    - **Privileges**: Admin

### Summary Table

| Command                                   | CMD | PowerShell | Normal User | Admin |
| ----------------------------------------- | --- | ---------- | ----------- | ----- |
| whoami                                    | ✓   | ✓          | ✓           |       |
| echo %username%                           | ✓   |            | ✓           |       |
| net user %username%                       | ✓   | ✓          | ✓           |       |
| whoami /priv                              | ✓   | ✓          | ✓           |       |
| whoami /groups                            | ✓   | ✓          | ✓           |       |
| net localgroup                            | ✓   | ✓          | ✓           |       |
| query user                                | ✓   | ✓          | ✓           |       |
| set                                       | ✓   |            | ✓           |       |
| Get-ChildItem Env:                        |     | ✓          | ✓           |       |
| whoami /user                              | ✓   | ✓          | ✓           |       |
| wevtutil qe Security                      | ✓   | ✓          |             | ✓     |
| net user                                  | ✓   | ✓          | ✓           |       |
| whoami /all                               | ✓   | ✓          | ✓           |       |
| net localgroup administrators             | ✓   | ✓          |             | ✓     |
| wmic useraccount                          | ✓   | ✓          |             | ✓     |
| auditpol /get /category:*                 | ✓   | ✓          |             | ✓     |
| Get-WmiObject -Class Win32_ComputerSystem |     | ✓          | ✓           |       |
| Get-Process (with owner info)             |     | ✓          |             | ✓     |

This comprehensive list should cover your needs for enumerating current user information on Windows machines, distinguishing between CMD and PowerShell, and noting the required privileges. If you need any further modifications or additional commands, let me know!