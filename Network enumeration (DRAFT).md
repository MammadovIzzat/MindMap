Commands:

1. **net view**: Displays a list of resources available on the network.
2. **net user**: Displays user accounts on a domain.
3. **net group**: Displays group information on a domain.
4. **net group "Domain Admins" /domain**: Lists members of the Domain Admins group.
5. **net group "Enterprise Admins" /domain**: Lists members of the Enterprise Admins group.
6. **net group "Domain Controllers" /domain**: Lists domain controller servers.
7. **net group "Schema Admins" /domain**: Lists members of the Schema Admins group.
8. **net group "Exchange Organization Administrators" /domain**: Lists members of Exchange Organization Administrators group.
9. **net group "Administrators" /domain**: Lists members of the Administrators group.


1. **nltest /domain_trusts**: Displays domain trust relationships.
2. **nltest /dclist:<domain>**: Lists domain controllers for a specified domain.


1. **dsquery server -domain <domain>**: Lists servers in a domain.
2. **dsquery user -name * -limit 0**: Lists all user accounts.
3. **dsquery computer -limit 0**: Lists all computers in the domain.
4. **dsquery group -name * -limit 0**: Lists all groups.
5. **dsquery ou -limit 0**: Lists all organizational units (OUs).
6. **dsquery subnet -limit 0**: Lists all subnets in the domain.
7. **dsquery site -limit 0**: Lists all sites in the domain.
8. **dsquery contact -limit 0**: Lists all contacts in the domain.
9. **dsquery * -filter (objectClass=*) -attr distinguishedName**: Lists all objects in the domain with their distinguished names.










1. **Get-ADDomain**: Retrieves the properties of the Active Directory domain.
2. **Get-ADForest**: Retrieves the properties of the Active Directory forest.
3. **Get-ADDomainController**: Retrieves the properties of domain controllers.
4. **Get-ADUser -Filter * -Properties * | Select-Object Name, SamAccountName, Description**: Retrieves all user accounts along with their names, SAM account names, and descriptions.
5. **Get-ADGroup -Filter * -Properties * | Select-Object Name, GroupCategory, Description**: Retrieves all groups along with their names, categories, and descriptions.
6. **Get-ADComputer -Filter * -Properties * | Select-Object Name, OperatingSystem, OperatingSystemServicePack**: Retrieves all computers along with their names, operating systems, and service packs.
7. **Get-ADOrganizationalUnit -Filter * -Properties * | Select-Object Name, Description**: Retrieves all organizational units along with their names and descriptions.
8. **Get-ADDomainController -Filter * | Select-Object Name, Site, IPv4Address**: Retrieves domain controllers along with their names, sites, and IPv4 addresses.
9. **Get-ADGroupMember "Domain Admins" | Select-Object Name, SamAccountName**: Retrieves members of the Domain Admins group along with their names and SAM account names.
10. **Get-ADGroupMember "Enterprise Admins" | Select-Object Name, SamAccountName**: Retrieves members of the Enterprise Admins group along with their names and SAM account names.
11. **Get-ADGroupMember "Schema Admins" | Select-Object Name, SamAccountName**: Retrieves members of the Schema Admins group along with their names and SAM account names.



13. **Get-ADTrust -Filter * | Select-Object Name, TrustType, TrustDirection, SourceDomain, TargetDomain**: Retrieves trust relationships along with their names, types, directions, source domains, and target domains.


1. **Get-ADObject -LDAPFilter "(objectClass=computer)"**: Retrieves all computer objects.
2. **Get-ADObject -LDAPFilter "(objectClass=group)"**: Retrieves all group objects.
3. **Get-ADObject -LDAPFilter "(objectClass=user)"**: Retrieves all user objects.
4. **Get-ADObject -LDAPFilter "(objectClass=organizationalUnit)"**: Retrieves all organizational unit objects.
5. **Get-ADReplicationPartnerMetadata -Target "<DomainController>"**: Retrieves replication partner metadata for a specific domain controller.
6. **Get-ADReplicationFailure -Scope "<Domain>"**: Retrieves replication failures for a specific domain.
7. **Get-ADReplicationUpToDatenessVectorTable -Server "<DomainController>"**: Retrieves replication up-to-dateness vector table for a specific domain controller.
8. **Get-ADFineGrainedPasswordPolicy**: Retrieves fine-grained password policies in the domain.

Tools:

1. **ADRecon**: A tool for Active Directory reconnaissance and enumeration.
2. **PingCastle**: A tool for Active Directory security assessment and auditing.
3. **SharpHound**: A BloodHound ingestor implemented in C# for



Network enumeration : 

ipconfig /all 

arp -a 

netstat 

route print 

net use 

GET-DnsClientCache


1. Start Powershell - **powershell -ep bypass -ep** bypasses the execution policy of powershell allowing you to easily run scripts 

2. Start PowerView - . **.\Downloads\PowerView.ps1**

3. Enumerate the domain users - **Get-NetUser | select cn**

4. Enumerate the domain groups - **Get-NetGroup -GroupName *admin*** 

5 SharedFolder **net share Invoke-ShareFinder****
**
6 Enumerate **netdevices Get-NetComputer -fulldata | select operatingsystem**