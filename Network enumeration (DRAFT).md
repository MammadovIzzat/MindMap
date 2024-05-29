
- crackmapexec smb 10.129.203.121 -u '' -p '' --users --export $(pwd)/users.txt 

Check for SMB NULL sessions on a domain controller host and enumerate valid users





Network Enumeration scripts. 
```
# Import required modules
Import-Module ActiveDirectory

# Get current domain
$currentDomain = [System.DirectoryServices.ActiveDirectory.Domain]::GetCurrentDomain()

# Enumerate domain controllers
$domainControllers = Get-ADDomainController -Filter *

# Display domain controller information
foreach ($dc in $domainControllers) {
    Write-Host "Domain Controller: $($dc.HostName)"
    Write-Host "  IP Address: $($dc.IPAddress)"
    Write-Host "  Site: $($dc.Site)"
    Write-Host "  OS Version: $($dc.OperatingSystem)"
    Write-Host "  OS Service Pack: $($dc.OperatingSystemServicePack)"
    Write-Host ""
}

# Enumerate domain users
$domainUsers = Get-ADUser -Filter *
Write-Host "Domain Users:"
foreach ($user in $domainUsers) {
    Write-Host "  $($user.SamAccountName) - $($user.Name)"
}

# Enumerate domain groups
$domainGroups = Get-ADGroup -Filter *
Write-Host "Domain Groups:"
foreach ($group in $domainGroups) {
    Write-Host "  $($group.Name)"
}

# Enumerate domain computers
$domainComputers = Get-ADComputer -Filter *
Write-Host "Domain Computers:"
foreach ($computer in $domainComputers) {
    Write-Host "  $($computer.Name)"
}

# Get domain password policy
$domainPolicy = Get-ADDefaultDomainPasswordPolicy
Write-Host "Domain Password Policy:"
Write-Host "  MaxPasswordAge: $($domainPolicy.MaxPasswordAge)"
Write-Host "  MinPasswordLength: $($domainPolicy.MinPasswordLength)"
Write-Host "  PasswordComplexity: $($domainPolicy.PasswordHistoryCount)"

```


Kerberos , NTLM , SMB Enumeration 

```
Import-Module ActiveDirectory

Write-Host "Kerberos Enumeration:"
$kerberosInfo = Get-ADUser -Filter * -Properties UserPrincipalName, ServicePrincipalName
foreach ($user in $kerberosInfo) {
    if ($user.ServicePrincipalName) {
        Write-Host "  $($user.Name)"
        foreach ($spn in $user.ServicePrincipalName) {
            Write-Host "    $spn"
        }
    }
}

Write-Host "NTLM Enumeration:"
$ntlmInfo = Get-ADUser -Filter * -Properties UserPrincipalName
foreach ($user in $ntlmInfo) {
    Write-Host "  $($user.Name) - $($user.UserPrincipalName)"
}

Write-Host "SMB Enumeration:"
$shares = Get-WmiObject -Class Win32_Share
foreach ($share in $shares) {
    Write-Host "  $($share.Name) - $($share.Path)"
}

Write-Host "Domain Controllers Enumeration:"
$domainControllers = Get-ADDomainController -Filter *
foreach ($dc in $domainControllers) {
    Write-Host "  $($dc.HostName)"
}

Write-Host "Domain Users Enumeration:"
$domainUsers = Get-ADUser -Filter *
foreach ($user in $domainUsers) {
    Write-Host "  $($user.SamAccountName) - $($user.Name)"
}

Write-Host "Domain Groups Enumeration:"
$domainGroups = Get-ADGroup -Filter *
foreach ($group in $domainGroups) {
    Write-Host "  $($group.Name)"
}

Write-Host "Domain Computers Enumeration:"
$domainComputers = Get-ADComputer -Filter *
foreach ($computer in $domainComputers) {
    Write-Host "  $($computer.Name)"
}




```