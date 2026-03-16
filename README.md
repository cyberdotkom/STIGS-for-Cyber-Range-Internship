# STIGS-for-Cyber-Range-Internship
STIG report for Cyber Range Internship 

<#
.SYNOPSIS
    This is a report on STIGS that have been accomplished for the Cyber Range Internship 

.NOTES
    Author          : Kemar Morrison 
    LinkedIn        : http://www.linkedin.com/in/morrison-35717292
    GitHub          : https://github.com/cyberdotkom 
    Date Created    : 2026-03-16
    Last Modified   : 2026-03-16
    

.Setup: The VM was created in Azure. Vulnerabilities where either created by scripts or manually.

.Tools:  
 Powershell 
 Tenable  
 Microsoft Azure 


.Procedures: A Tenable DISA STIG  pre and post scan for Windows 11 was conducted. The following below are some of the STIGS that failed 
             the audit. During the pre scan the STIGS failed, but the post scan showed that these STIGS passed. 

STIGS Tested:  1. WN11-00-000165 - The Server Message Block (SMB) v1 protocol must be disabled on the SMB server. 

               2. WN11-SO-000010 - The built-in guest account must be disabled. 

               3. WN11-00-000115 - The Telnet Client must not be installed on the system. 

               4. WN11-CC-000110 - Printing over HTTP must be prevented. 

               5. WN11-SO-000025 - The built-in guest account must be renamed. 

               6. WN11-CC-000391 - Internet Explorer must be disabled for Windows 11 



1. For this STIG I used the following script in Powershell ISE (in Admin) to toggle SMB v1 protocol on (or off) :
   
  **Disable SMBv1**
  Set-SmbServerConfiguration -EnableSMB1Protocol $false -Force
  Disable-WindowsOptionalFeature -Online -FeatureName SMB1Protocol -NoRestart


3. For this STIG I manually went to **Start** >> typed **Computer Management** and then went to **Local Users and Groups** >> Users and double clicked **Guest** went into properties and disabled it again.  


4. For this STIG I used the following script in Powershell ISE (in Admin) to disable the Telnet Client : 

    **Toggle Telnet**
    Disable-WindowsOptionalFeature -Online -FeatureName TelnetClient   


5. For this STIG I manually configured the local policy for the VM. I did the following: Configure the policy value for Computer Configuration >> Administrative Templates >> System >> Internet Communication Management >> Internet Communication settings >> 'Turn off printing over HTTP' to 'Enabled' and selected " Apply" 


6. For this STIG I just renamed the "Guest" account to Nonna by going to to **Start** >> typed **Computer Management** and then went to **Local Users and Groups** >> Users and double clicked **Guest** went into properties and renaming it Nonna 


7. For this STIG I manually configured the local policy for the VM. I did the following: Set the policy value for 'Computer Configuration >> Administrative Templates >> Windows Components >> Internet Explorer >>  Disable Internet Explorer 11 as a standalone browser' to 'Enabled' with the option value set to 'Never' and selected " Apply" 

 

#>
