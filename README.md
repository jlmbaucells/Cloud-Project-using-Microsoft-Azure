# Cloud-Project-using-Microsoft-Azure
Moving to Azure
Report: Moving to Azure
 

 STEP 0:  Problem Background
Contoso is an online cloth merchandise company specializing in selling activewear. They have a rented space in a local data center. They have one system administrator who makes sure all servers are working properly 24x7. Their hardware is getting old and they must decide on whether they need to spend $22,000 for new hardware or move their business to the Azure cloud services.  The following list represents their current on-premises infrastructure:

Server 1: 	Purpose: WordPress web server
CPU: 8 Cores and 60% average utilization
RAM: 16 GB and 87% average utilization
HDD OS: 500 GB capacity with 57 GB used 
Web URL: Contoso.com
IP # Public: 200.200.100.50
IP #: 10.10.1.11 
Firewall: Inbound TCP 2222-2224, 80, 443
Usage: This is Contoso’s only web server. It runs WordPress and eCommerce services. Their on-line store is always open, and they receive orders 24x7
This server uses ports 80 and 443 for HTTP and HTTPS traffic
Server 2 & 3: 	Purpose: Microsoft SQL 2019
CPU: 8 Cores and 30% average utilization x2
RAM: 16 GB and 87% average utilization x2
HDD OS: 500 GB capacity with 240 GB used x2
HDD Data: 2 TB SAN (Storage Area Network drive)
IP #: 10.10.1.12 and 10.10.1.13
SQL Cluster: SQLCluster.Contoso.Com
IP #: 10.10.1.14
Firewall: Inbound TCP 2222-2224, 1433
Usage: These two servers are running Microsoft SQL cluster services. SQL Always-On service is fully configured as Active-Passive nodes. The 2 servers use an external attached SAN drive for all data storage such as product descriptions, transaction logs, and clients lists. Annual data growth is negligible. 
These servers use the standard SQL inbound TCP port 1433
Server 4:	Purpose: ABC Backup and Restore server
CPU: 8 Cores and 30% average utilization
RAM: 16 GB and 87% average utilization
HDD OS: 500 GB capacity with 164 GB used
HDD Backup: 40 TB
IP #: 10.10.1.15
Firewall: Inbound TCP 2222
Usage: The ABS backup software runs daily at 8pm. It stores the last 18 months of all the SQL data drive contents onto a local D: drive (HDD Backup) with 40 TB capacity. 
Server 5:	Purpose: XYZ Antivirus server
CPU: 8 Cores and 30% average utilization
RAM: 16 GB and 87% average utilization
HDD: 500 GB capacity with 43 GB used 
IP #: 10.10.1.16
Firewall: Inbound TCP 2222-2224
This server uses ports TCP 2222-2224 for the antivirus client
Usage: The XYZ anti-virus services are essential for the security of Contoso’s operations security. The server is always on and constantly running. It monitors all Contoso’s servers and mitigates against viruses and hack attacks. Data grown is negligible.  


 STEP 1:  Assessing the On-Premises Environment

Purpose: To identify the Azure services needed to ensure Contoso’s business continuity in the cloud.

Current Environment

Make a list of all current on-premises servers and services.	
Matching Azure Services

Match the list of on-premises servers and services to the corresponding Azure ones.	Make a list of all servers and services you would create on Azure, and why you chose each. As a hint, one of the servers is likely no longer needed.
Discussion Question #1

A - How can you verify the running programs and services on each of your on-premises servers? List the steps taken to identify the services running for each server.

B - List your migration plans.	
Discussion Question #2

On your on-premises servers:
A - How can you find the listing of all windows firewall port exceptions? 

B - Do these firewall port exceptions have to match the NSG firewall exceptions? Please explain.	
Optional Discussion

Looking at the new Azure server farm, what will you change and why? 	


 STEP 2:  Cost Estimates

Purpose: To provide the CIO with a monthly cost estimate after the migration to Azure.

Use Azure Pricing Calculator to provide the CIO with a monthly cost estimate, including:
●	The number of VMs needed
●	The RAM and CPU needed for each VM
●	The amount of storage needed
●	Any Azure services such as anti-virus, back-up, database, etc.
●	Build a list/table that includes VM type (you may use the template below or create your own)

Build / fill out the table providing your current server farm and its corresponding Azure farm. List the potential Azure replacement for each of the on-premises servers, the VM type and monthly cost. Assume your company has Hybrid benefits and are willing to commit to 3-year agreements. Use the East US Azure zone. Show the cost of all servers with a three year commitment after applying Azure Reservations cost reduction. Compare the VMs prices with and without Azure Reservations. 



Server Name	CPU Cores	RAM/HD	VM Type	Monthly Cost
				
				
				
				
				



Discussion Question #1

Will these 4 Azure servers provide HA/DR for Contoso? Will their site be available 24x7, 365 days?	
Discussion Question #2

Can you change the VM type (upgrade or downgrade the configurations based on needs)? Try to downgrade one of the Azure VMs to B2ms. Also, please provide a screenshot of the VM Overview settings, including VM name and size.	
Optional Discussion

Is Contoso better off with a SQL Managed Instance? Check Azure Pricing.	


 STEP 3 (OPTIONAL):  Creating a VPN

Purpose: Build and set up a point-to-point (site to site) VPN connection between Contoso’s on-premises and Contoso’s Azure environments.

Note: This step is entirely optional, and may take a considerable amount of time to implement. Therefore, it is suggested that you only attempt this step on your own after having satisfactorily completed all other project steps. You may find this site helpful in completing this optional step.

 STEP 4:  An Additional Server

Purpose: Use Azure Resource Manager (ARM) to deploy one additional WordPress web server. This additional web server should provide web services redundancy and improve the web site’s response time.

Create a replica of the WordPress server configuration.

The process is summarized as:
●	The current WP server settings were saved as a template during the creation process. If not, you will need to add it to your Template store. 
●	Deploy a new VM from a template. In the Azure portal search for TEMPLATES and run that service. 
●	The WP server template should be listed there.  Select it. 
●	Make sure you load and edit the parameters file and change the values for the new VM as needed. Values such as Name, Password, etc. should be unique. Use the Azure Template Services.

Make sure you already have a resource group to place the VM in. You may need to create a Servers-RG resource group if one does not exist.

Configuration Process

Provide a screenshot of the template configuration process.	
Discussion Question #1

List the benefits (at least three) of using ARM templates. Think of when, why and how you can benefit from this Azure service.	
Discussion Question #2

What is the difference between an ARM template and a server image? When will you use each and for what purpose? Make sure you consider each of the two.	
Optional Discussion

Visit GitHub (https://github.com/azure/azure-quickstart-templates) and look at all available templates. Can you find a template that deploys 2 web servers, a load balancer, and a Resource Group? Send the link to the template or a screenshot clearly highlighting the one you will select.	


 STEP 5:  Backup and Recovery

Purpose: Use the Azure backup services to setup recurring full daily backup jobs of your products and client’s data. Test the backup process. No back is fully verified until you perform a successful restore.

You want to ensure your VMs are all backed up. You want to ensure a working replica of each of them is saved somewhere safe. The steps are:
1.	Create a backup vault. Call it “ServersBackup”.
2.	Install Azure Backup Extension on the target VM.
3.	Create a backup policy in the vault. Set retention policy and daily backup points. 
4.	Now it is time to link the target VM to the backup policy. Click on the target VM, select Backup from the Operations tab. Then select the newly created backup policy.
5.	Alternatively, you can select Recovery Services Vault from the left navigation bar. Select all the VMs you want to add to the backup.


Backups

Provide screenshots of 1) the backup vault and 2) the backup policy. 	
Discussion Question #1

What is the difference between Azure backup and site recovery? When would you use each service and for what reason? 	
Discussion Question #2

Restore Time Objective (RTO) and
Restore Point Objective (RPO) have
similarities and differences. 
A - How are they different? Make sure you consider each of the two.

B - Which backup strategy consumes more disc space?
	
Optional Discussion

Create more that one backup policy for each type of data. For example, you may want to create a policy that backs up certain files and folders and not the entire VM’s hard drive. Try a policy that has folder exclusion and inclusion. 	


 STEP 6:  Antivirus Communication

Purpose: Enable the antivirus server to communicate with client VMs.

The XYZ antivirus server requires TCP ports 2222-2224 to communicate with the target client VMs. A firewall exception on the target VM is necessary to allow the XYZ server to scan and update the clients. Assuming Contoso will want to continue using their XYZ antivirus server, how will you alter the NSG (network security group) to allow all Contoso’s Azure servers port: TCP 2222-2224 in from the
antivirus server?

Each of the Azure servers you created have a unique internal (not public) IP address. Each one of these VMs has its own Network Security Group (nsg) associated with it as well. Your task is to adjust the nsg of each server to allow for traffic coming from the antivirus server. The steps are:

1.	Make a list of each server and it’s internal IP.
2.	For each server’s nsg, modify the settings to allow for TCP 2222-2224 from the antivirus server’s IP number. 
3.	Test your work by trying to deploy the antivirus agent on one of the target servers.

Inbound Rules

Provide a screenshot of the modified nsg firewall inbound rules.	
Discussion Question #1

Will you need to create an inbound port exception on your Windows OS?	



Note: Once you have completed your report, feel free to shut down your Azure resources to avoid charges!
