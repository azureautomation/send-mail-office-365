Send Mail Office 365
====================

            

This Graphical PowerShell runbook connects to Office 365 and sends an email.  You can run this runbook by itself or call it from another runbook as part of a larger workflow.



REQUIRED


1. An Automation credential asset named 'O365Credential' that contains the information for authenticating with Office 365.  To use an asset with a different name you can pass the asset name as a input parameter to this runbook or change the default
 value for the O365CredentialAssetName input parameter.


NOTES


- The From address must be one with authorization to send email in Office 365.


- The SmtpPort value defaults to 587.  You can change the default value, or pass in a different value when calling the runbook.


- The SmtpServer value defaults to smtp.office365.com.  You can change the default value, or pass in a different value when calling the runbook.


 


 

 

![Image](https://github.com/azureautomation/send-mail-office-365/raw/master/SendMailO365.png)


        
    
TechNet gallery is retiring! This script was migrated from TechNet script center to GitHub by Microsoft Azure Automation product group. All the Script Center fields like Rating, RatingCount and DownloadCount have been carried over to Github as-is for the migrated scripts only. Note : The Script Center fields will not be applicable for the new repositories created in Github & hence those fields will not show up for new Github repositories.
