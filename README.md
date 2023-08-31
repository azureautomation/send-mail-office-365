Send Mail Office 365 via a System Managed Identity
=
This Graphical PowerShell runbook connects to Office 365 and sends an email.  You can run this runbook by itself or call it from another runbook as part of a larger workflow.
![image](https://github.com/c5245010/send-mail-office-365/assets/98794426/e6fa7906-1cc6-4d46-9e0e-21e41bb0f4c4)
<br/><br/>

**REQUIRED**
1. A system managed identity is enabled in the Automation Account.
2. Use PowerShell to Admin Consent for managed identity, the following code MUST run in the local machine (**None Runbook or None automation account**) where microsoft.graph module installed:

```powershell
Connect-MgGraph -Scopes Application.Read.All, AppRoleAssignment.ReadWrite.All, RoleManagement.ReadWrite.Directory
$managedIdentityId = "managed identity object id in the AAD"
$roleName = "Mail.Send"
$msgraph = Get-MgServicePrincipal -Filter "AppId eq '00000003-0000-0000-c000-000000000000'"
$role = $Msgraph.AppRoles| Where-Object {$_.Value -eq $roleName} 
New-MgServicePrincipalAppRoleAssignment -ServicePrincipalId $managedIdentityId -PrincipalId $managedIdentityId -ResourceId $msgraph.Id -AppRoleId $role.Id 
```

**Note: This comamnd requires Azure AD Global administrator to approve Admin Consent.**
<img width="651" alt="image" src="https://github.com/c5245010/send-mail-office-365/assets/98794426/1d32315b-7ac8-4390-9aa1-3516b0fc0744">
<br/><br/>

Refer to below screenshot to find Azure automation managed identity ID.
<img width="517" alt="image" src="https://github.com/c5245010/send-mail-office-365/assets/98794426/d04d6382-24c4-48ec-ad2d-24bfc6b5c6ce">
<br/><br/>

3. Import dependencies modules: Microsoft.Graph.Authentication, Microsoft.Graph.Users.Actions in the Azure automation account.
<br/><br/>

AUTHOR
Azure Automation Team 

LASTEDIT
2023-8-31
<br/><br/>

TechNet gallery is retiring! This script was migrated from TechNet script center to GitHub by Microsoft Azure Automation product group. All the Script Center fields like Rating, RatingCount and DownloadCount have been carried over to Github as-is for the migrated scripts only. Note : The Script Center fields will not be applicable for the new repositories created in Github & hence those fields will not show up for new Github repositories.
