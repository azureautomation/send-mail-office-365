Send Mail Office 365
====================

This runbook sends an email through Office 365 Exchange.
You can run this runbook by itself or call it from another runbook as part of a larger workflow. 

REQUIRED
1. An Automation managed identity is enabled.
2. Use PowerShell to Admin Consent for managed identity, the following code MUST run in the local machine (None-Runbook) where microsoft.graph module installed:

Connect-MgGraph -Scopes Application.Read.All, AppRoleAssignment.ReadWrite.All, RoleManagement.ReadWrite.Directory
$managedIdentityId = "managed identity object id in the AAD"
$roleName = "Mail.Send"
$msgraph = Get-MgServicePrincipal -Filter "AppId eq '00000003-0000-0000-c000-000000000000'"
$role = $Msgraph.AppRoles| Where-Object {$_.Value -eq $roleName} 
new-MgServicePrincipalAppRoleAssignment -ServicePrincipalId $managedIdentityId -PrincipalId $managedIdentityId -ResourceId $msgraph.Id -AppRoleId $role.Id 

3. Import dependencies modules: Microsoft.Graph.Authentication, Microsoft.Graph.Users.Actions


AUTHOR
Azure Automation Team 

LASTEDIT
2023-5-29

     
TechNet gallery is retiring! This script was migrated from TechNet script center to GitHub by Microsoft Azure Automation product group. All the Script Center fields like Rating, RatingCount and DownloadCount have been carried over to Github as-is for the migrated scripts only. Note : The Script Center fields will not be applicable for the new repositories created in Github & hence those fields will not show up for new Github repositories.
