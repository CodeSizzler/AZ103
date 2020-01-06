<h1>Migrating on premises Hyper-V VMs to Azure</h1>

<h2>Introduction</h2>
<p>This article will help you to migrate your workloads from on-premises Hyper-V virtual machines to Azure Virtual Machines.</p>

<h2>Pre-requisites</h2>
<p>To perform this demo user must have a valid Azure subscription and some knowledge on Hyper-V Virtual Machine, PowerShell, Migration.</p>

<h2>Template files</h2>
<p>Download the template files from - http://bit.ly/templatefilescs</p>

<h2>Demo</h2>

<p>Log-in to Azure portal with your account using www.portal.azure.com. In Azure portal start a PowerShell session in Cloud Shell.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/01.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/02.jpg"/>
<p>Upload az-101-01b_azuredeploy.ps1, az-101-01b_azuredeploy.json, az-101- 01b_azuredeploy.parameters.json, InstallHyperV.ps1, and InstallHyperV.zip files in the PowerShell panel.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/03.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/04.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/05.jpg"/>
<p>After uploading the files run the following command in PowerShell to copy the InstallHyperV.ps1 and InstallHyperV.zip files in a sub folder.</p>
	<p>Set-Location -Path $HOME</p>
	<p>New-Item -Type Directory -Path '.\DSC'</p>
	<p>Move-Item -Path '.\InstallHyperV.*' -Destination '.\DSC'</p>

<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/06.jpg"/>

<p>After the command run completes run the following command to deploy a VM and a resource group.</p>
	<p>./az-101-01b_azuredeploy.ps1 -resourceGroupName DemoRG' -resourceGroupLocation <location></p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/07.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/08.jpg"/>
<p>If the deployment fails due to the Standard_DS2_v3 size not being available due to your subscription run the following command by replacing the VM size string with a valid VM size.</p>
	<p>.\az-101-01b_azuredeploy.ps1 -resourceGroupName 'az1010101b-RG' - resourceGroupLocation <location> -vmSize <vm_Size></p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/09.jpg"/>

<p>Then close the PowerShell session and click on create a new resource. When it prompts search for Backup and Site Recovery.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/10.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/11.jpg"/>
<p>Configure the following settings and click on create.</p>

<p>•	Name: CodesizzlerRecovery</p>
<p>•	Subscription: Select a valid subscription</p>
<p>•	Resource group: Create a new resource group RecoveryRG</p>
<p>•	Location: Select a valid location</p>

<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/12.jpg"/>
<p>After creating the recovery service vault navigate to the created Virtual Machine blade and click on connect.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/13.jpg"/>
<p>Download the RDP file and provide the respective credentials that you have provided while creating the Virtual Machine to connect with it.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/14.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/15.jpg"/>
<p>In the Virtual Machine launch the Hyper-V Manager and create an Internal switch.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/16.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/17.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/18.jpg"/>
<p>Create a new Hyper-V VM with the followings</p>

<p>•	Name: RecoveryVM</p>
<p>•	Generation: 1</p>
<p>•	Start-up memory: 2048</p>
<p>•	Connection: Internal</p>
<p>•	Create a virtual disk:</p>
	<p>o	Name: RecoveryVM.vhdx</p>
	<p>o	Location: Default </p>
	<p>o	Size: 32GB</p>
<p>•	Installation Options: Install operating system later</p>
<p>After creating the Hyper-V VM navigate to Server Manager and turn off the IE Enhanced Security Configuration.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/19.jpg"/>

<p>In the lab Virtual Machine log-in with your Azure account using www.portal.azure.com. In Azure portal navigate to RecoveryRG blade and display the Site Recovery Infrastructure panel.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/20.jpg"/>
<p>In site recovery infrastructure display the Site Recovery infrastructure - Hyper-V Site panel.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/21.jpg"/>
<p>Create a Hyper-V site in the name of CodesizzlerHyperVsite.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/22.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/23.jpg"/>
<p>After creating the Hyper-V site navigate to Hyper-V host and add a registered server.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/24.jpg"/>
<p>When it prompts click-on Download the installer and run the file. Also download the registration key to register with it.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/25.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/26.jpg"/>
<p>For the registration key click-on browse and upload the registration key that you downloaded in the previous step.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/27.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/28.jpg"/>
<p>After registering with Azure Site recovery note that your server has been added.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/29.jpg"/>
<p>After adding server to the Hyper-V host prepare an infrastructure. Navigate to recovery vault and prepare the infrastructure.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/30.jpg"/>
<p>For protection goal</p>
	<p>•	Where are your machines located: On-premises</p>
	<p>•	Where do you want to replicate your machines to: To Azure</p>
	<p>•	Are your machines virtualized: Yes, with Hyper-V</p>
	<p>•	Are you using System Centre VMM to manage your Hyper-V hosts: No</p> 
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/31.JPG"/>

<p>For deployment planning select Yes I have done it from the drop down and click OK.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/32.jpg"/>
<p>For prepare source</p>
	<p>•	Select Hyper-V Site: CodesizzlerHyperVsite</p>
	<p>•	Ensure Hyper-V servers are added: az1010102b-vm1</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/33.JPG"/>
<p>For target add a network.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/34.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/35.JPG"/>
<p>After adding the network add the Storage account.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/36.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/37.JPG"/>
<p>After adding the storage account and network click on OK.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/38.jpg"/>
<p>Create and associate a replicate setting with following configuration</p>
	<p>Name: codesizzlerassociatepolicy</p>
	<p>Source type: Hyper-V</p>
	<p>Target type: Azure</p>
	<p>Copy frequency: 5</p>
	<p>Recovery point retention in hours: 2</p>
	<p>App-consistent snapshot frequency in hours: 1</p>
	<p>Initial replication start time: Immediately</p>
	<p>Associated Hyper-V site: CodesizerHyperVsite</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/39.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/40.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/41.jpg"/>
<p>After finishing all the setting click on ok to prepare infrastructure.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/42.JPG"/>
<p>Navigate to Codesizzlerrecovery and display the replicate items blade. In the replicate items blade click on Replicate.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/43.jpg"/>
<p>Add a replication policy with the following settings</p>
<p>Source</p>
	<p>•	Source: On-premises</p>
	<p>•	Source location: Adatum Hyper-V Site</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/44.jpg"/>
<p>Target</p>
	<p>•	Target: Azure</p>
	<p>•	Subscription: the same subscription you selected earlier in this lab</p>
	<p>•	Post-failover resource group: RecoveryRG</p>
	<p>•	Post-failover deployment model: Resource Manager</p>
	<p>•	Storage account: the storage account you created in the previous task</p>
	<p>•	Azure network: Configure now for selected virtual machines</p>
	<p>•	Post-failover virtual network: RecoveryRG</p>
	<p>•	Subnet: Default</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/45.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/46.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/47.jpg"/>
<p>Select virtual machines: VMrecovery (the one which have created in Hyper-V)</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/48.JPG"/>
<p>Configure the following properties</p>
	<p>OS TYPE: Windows</p>
	<p>OS DISK: Need to select per VM</p>
	<p>DISK TO REPLICATE: Need to select per VM</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/49.jpg"/>
<p>Configure replication settings with a new replication policy</p> 
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/50.JPG"/>
<p>After configuring all the above settings click on OK to enable replication.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-04/51.jpg"/>
<p>After enabling replication, navigate to the Recovery vault blade and display the replicate items blade. Monitor that the replication health indicates Healthy and also monitor the status column. Wit until it changes to Protected.</p>
<p>Then navigate to the Hyper-V manager and monitor the Health and status, Failover readiness, Latest recovery points, and Infrastructure view.</p>

