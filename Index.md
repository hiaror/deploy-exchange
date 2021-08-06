# deploy-exchange
Deploy co-existing exchange on premises servers
I will try to share all the challenges faced during the setup of this lab. Some of you might already know how to setup the lab and some might not. I was able to finally set up the co-existence by executing the following steps:
 
Install Exchange 2010 SP3 on Windows Server 2012R2
 
1st Step: On Domain Controller, execute the following steps:
 
1. Import-Module ServerManager
2. Copy the installation files on DC and run the following in command prompt from setup location:
	a. Setup.exe /prepareschema
	b. Setup.exe /preparead
	c. In the powershell run: 
Install-WindowsFeature Telnet-Client,RSAT-ADDS, RSAT-Clustering,Web-Server,Web-Basic-Auth,Web-Windows-Auth,Web-Metabase,Web-Net-Ext,Web-Request-Monitor,Web-Static-Content,Web-Mgmt-Console,Web-Lgcy-Mgmt-Console,Web-WMI,WAS-Process-Model,Web-Asp-Net,Web-Client-Auth,Web-ISAPI-Ext,Web-ISAPI-Filter,Web-Http-Errors,Web-Http-Logging,Web-Http-Redirect,Web-Http-Tracing,Web-Digest-Auth,Web-Dir-Browsing,Web-Dyn-Compression,NET-HTTP-Activation,RPC-Over-HTTP-Proxy –Restart
Repadmin /syncall
3. Repadmin /syncall
 
2nd Step: On the member server where you want to install Exchange 2010, execute following steps:
 
1. Install the Office 2010 Filter Packs found here: http://www.microsoft.com/en-us/download/details.aspx?id=17062
2. Install Office 2010 Filter Pack Service Pack 1 found here: http://www.microsoft.com/en-us/download/details.aspx?id=26604
3. Run the following commands:
i. Import-module servermanager
ii. Install-WindowsFeature Telnet-Client,RSAT-ADDS, RSAT-Clustering,Web-Server,Web-Basic-Auth,Web-Windows-Auth,Web-Metabase,Web-Net-Ext,Web-Request-Monitor,Web-Static-Content,Web-Mgmt-Console,Web-Lgcy-Mgmt-Console,Web-WMI,WAS-Process-Model,Web-Asp-Net,Web-Client-Auth,Web-ISAPI-Ext,Web-ISAPI-Filter,Web-Http-Errors,Web-Http-Logging,Web-Http-Redirect,Web-Http-Tracing,Web-Digest-Auth,Web-Dir-Browsing,Web-Dyn-Compression,NET-HTTP-Activation,RPC-Over-HTTP-Proxy –Restart
iii. Install the following: Microsoft Unified Communications Managed API, Core Runtime 64-bit.  Please install the softwadownload re from http://go.microsoft.com/fwlink/?LinkID=180957.
iv. Microsoft Server Speech Platform Runtime (x64). Please install the software from http://go.microsoft.com/fwlink/?LinkID=180958.
		 
 
Finally you can install exchange 2010 SP3. Interested in knowing more about the Exchange 2010 installation and prerequisites, refer to : https://www.microsoft.com/en-in/download/confirmation.aspx?id=36768
 
 

 
Exchange 2013 co-existence with Exchange 2010
 
1st Step: On Domain Controller, execute the following steps:
 
1. Import-Module ServerManager
2. Install-WindowsFeature AS-HTTP-Activation, Desktop-Experience, NET-Framework-45-Features, RPC-over-HTTP-proxy, RSAT-Clustering, RSAT-Clustering-CmdInterface, RSAT-Clustering-Mgmt, RSAT-Clustering-PowerShell, Web-Mgmt-Console, WAS-Process-Model, Web-Asp-Net45, Web-Basic-Auth, Web-Client-Auth, Web-Digest-Auth, Web-Dir-Browsing, Web-Dyn-Compression, Web-Http-Errors, Web-Http-Logging, Web-Http-Redirect, Web-Http-Tracing, Web-ISAPI-Ext, Web-ISAPI-Filter, Web-Lgcy-Mgmt-Console, Web-Metabase, Web-Mgmt-Console, Web-Mgmt-Service, Web-Net-Ext45, Web-Request-Monitor, Web-Server, Web-Stat-Compression, Web-Static-Content, Web-Windows-Auth, Web-WMI, Windows-Identity-Foundation, RSAT-ADDS
3. Install-WindowsFeature RSAT-ADDS
4. Install-WindowsFeature ADLDS
5. Download the latest PowerShell: https://www.microsoft.com/en-us/download/confirmation.aspx?id=53344
6. Run the following commands:-
i. Setup.exe /PrepareSchema /IAcceptExchangeServerLicenseTerms
ii. Setup.exe /PrepareAD /OrganizationName:"himanshu-arora" /IAcceptExchangeServerLicenseTerms
iii. Setup.exe /PrepareAllDomains /IAcceptExchangeServerLicenseTerms
iv. Setup.exe /PrepareDomain:ex2013.himanshu-arora.com /IAcceptExchangeServerLicenseTerms
7. Download the following pre-requisites:-
i. https://www.microsoft.com/en-us/download/confirmation.aspx?id=34992
ii. https://blogs.technet.microsoft.com/exchange/2013/04/02/released-exchange-server-2013-rtm-cumulative-update-1/
 
2nd Step: On the member server, where you wish to install exchange 2013, execute following:
 
8. Import-Module ServerManager
9. Install-WindowsFeature AS-HTTP-Activation, Desktop-Experience, NET-Framework-45-Features, RPC-over-HTTP-proxy, RSAT-Clustering, RSAT-Clustering-CmdInterface, RSAT-Clustering-Mgmt, RSAT-Clustering-PowerShell, Web-Mgmt-Console, WAS-Process-Model, Web-Asp-Net45, Web-Basic-Auth, Web-Client-Auth, Web-Digest-Auth, Web-Dir-Browsing, Web-Dyn-Compression, Web-Http-Errors, Web-Http-Logging, Web-Http-Redirect, Web-Http-Tracing, Web-ISAPI-Ext, Web-ISAPI-Filter, Web-Lgcy-Mgmt-Console, Web-Metabase, Web-Mgmt-Console, Web-Mgmt-Service, Web-Net-Ext45, Web-Request-Monitor, Web-Server, Web-Stat-Compression, Web-Static-Content, Web-Windows-Auth, Web-WMI, Windows-Identity-Foundation, RSAT-ADDS
10. Install-WindowsFeature RSAT-ADDS
11. Install-WindowsFeature ADLDS
12. Download the latest PowerShell: https://www.microsoft.com/en-us/download/confirmation.aspx?id=53344
13. Run the following commands:-
v. Setup.exe /PrepareSchema /IAcceptExchangeServerLicenseTerms
vi. Setup.exe /PrepareAD /OrganizationName:"himanshu-arora" /IAcceptExchangeServerLicenseTerms
vii. Setup.exe /PrepareAllDomains /IAcceptExchangeServerLicenseTerms
viii. Setup.exe /PrepareDomain:ex2013.himanshu-arora.com /IAcceptExchangeServerLicenseTerms
14. Download the following pre-requisites:-
iii. https://www.microsoft.com/en-us/download/confirmation.aspx?id=34992
iv. https://blogs.technet.microsoft.com/exchange/2013/04/02/released-exchange-server-2013-rtm-cumulative-update-1/
 
 

 
 
You might run into the issue where the admin does NOT have rights to open ECP on exchange 2013, to resolve this, assign the organization roles permissions to the administrator account form ON-Prem AD and run the following:
 
 
Launch the Windows PowerShell
 
1. Run Add-PSSnapin Microsoft.*
 
2. Run the command “Install-CannedRBACRoles” cmdlet to install the out-of-the-box RBAC roles.
 
3. Run the command “Install-CannedRBACRoleAssignments”
 
 
You might also face the issue where the EMS on Exchange 2013 will not be able to connect to FQDN on Exchange 2013 server and will connect to Exchange 2010 FQDN automatically, to resolve this make sure that IPv6 is unchecked and also make sure that you are able to ping the FQDN of Exchange 2013 Server and then use the following link to access the ECP: https://ex2013/ecp?ExchClientVer=15
 
To know more, refer to following links:
 
http://www.enowsoftware.com/solutions-engine/bid/156110/Exchange-2013-OWA-Coexistence-with-Exchange-2010
http://msexchangeguru.com/2013/05/10/exchange2013-migration/
https://blogs.technet.microsoft.com/exchange/2013/04/02/released-exchange-server-2013-rtm-cumulative-update-1/
![image](https://user-images.githubusercontent.com/88178522/127604903-9f618684-8d81-4065-9ec6-5b31fae42b81.png)
