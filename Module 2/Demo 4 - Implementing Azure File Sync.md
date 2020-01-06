<h1>Implementing Azure File Sync</h1>
<h2>Introduction</h2>
<p>In this walkthrough task we will locate an Azure Policy to restrict deployment of Azure resources to a particular Datacenter, and then assign that allowed location policy to a subscription. We will then verify that creating an Azure resource, such as a virtual machine, outside of the allowed location is blocked. We will finally remove the allowed location policy assignment, to allow us deploy resources again to any Datacenter location using that same subscription.</p>

<h2>Technical requirements</h2>
<p>You must need a valid Azure Subscription and need some knowledge on Azure File Sync and Template deployment to work in this session. Follow the below steps for implementing Azure File Sync. Befor starting this lab download the template files from - http://bit.ly/39HLshF</p>

<h2>Steps:</h2>

<h2>Deploying an Azure Virtual Machine using Azure Resource Manager Template</h2>
<p>•Login with your Azure account using http://portal.azure.com</p>
<p>•Click on create new resource panel and search for Template Deployment.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/01.jpg"/>
<p>•Select Build your own template in the editor.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/02.jpg"/>
<p>•In the edit template panel load the template file az-100-02b_azuredeploy.json and save the template.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/03.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/04.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/05.JPG"/>
<p>•Then navigate to the Custom deployment panel and click on Edit Parameter.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/06.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/07.JPG"/>
<p>•Load the file az-100-02b_azuredeploy.parameters.json by clicking load file and save the parameter.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/08.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/09.JPG"/>
<p>•In Custom deployment panel, start a template deployment with the following settings and click on purchase.</p> 
	<p>•Subscription: select a valid subscription</p>
	<p>•Resource group: the name of a new resource group DemoRG1</p> 
	<p>•Location: Select the valid one</p> 
	<p>•Vm Size: Standard_DS1_v2</p>
	<p>•Vm Name: DemoVM1</p>
	<p>•Admin Username: DemoUser</p>
	<p>•Admin Password: For your choice </p>
	<p>•Virtual Network Name: demoVnet1 </p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/10.jpg"/>

<h2>Preparing Azure File Sync Infrastructure</h2>
<h2>1.Creating an Azure Storage account and a file share:</h2>
<p>•In Azure Portal click on Create a new resource and search for Storage account.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/11.jpg"/>
<p>•In the Create storage account panel, create a new storage account with following settings</p>
	<p>•Subscription: select a valid one</p>
	<p>•Resource group: Create a new resource group StorageRG1</p> 
	<p>•Storage account name: DemoStorage1</p>  
	<p>•Location: Select a valid one</p>   
	<p>•Performance: Standard</p>  
	<p>•Account kind: Storage (general purpose v1)</p> 
	<p>•Replication: Locally-redundant storage (LRS)</p> 
	<p>•Secure transfer required: Disabled</p>
	<p>•Allow access from: All networks</p> 
	<p>•Hierarchical namespace: Disabled</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/12.jpg"/>
<p>•Navigate to the created storage account DemoStorage1 and click on File.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/13.jpg"/>
<p>•From the Files panel, create a new file share.</p>
	<p>•Name: FileShare1</p>
	<p>•Quota: none</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/14.jpg"/>

<h2>2.Preparing Windows Server 2016 for use with Azure File Sync:</h2>
<p>•Connect to the Virtual Machine DemoVM1 that you have created using valid credentials.</p> 
	<p>•Admin Username: DemoUser</p>
	<p>•Admin Password: which you have provided while creating the VM</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/15.jpg"/>
<p>•After connecting to the Virtual Machine navigate to Server Manager, click on File and Storage Services, find the data disk attached to the Azure VM and initialize it as a GPT.</p>  
<p>•Click on New Volume Wizard to create a single volume occupying entire disk with the following settings o Drive letter: S o File system: NTFS o Allocation unit size: Default o Volume label: Data</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/16.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/17.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/18.jpg"/>
<p>•Start Windows PowerShell session as Administrator and run the following commands in order.</p>
	<p>$directory = New-Item -Type Directory -Path 'S:\FileShare1'	</p>  
	<p>New-SmbShare -Name $directory.Name -Path $directory.FullName -FullAccess	</p> 
	<p>'Administrators' -ReadAccess Everyone	•	Install AzureRM using the command    
	<p>Copy-Item -Path 'C:\WindowsAzure\*' -Destination $directory.FullName –Recurse	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/19.jpg"/>
<p>•Install AzureRM using the command:</p>
	<p>Install-Module -Name AzureRM		</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/20.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/21.jpg"/>

<h2>3.Running Azure File Sync evaluation tool:</h2>
<p>•In PowerShell install the Package Management and PowerShellGet by running the command:</p>
	<p>Install-Module -Name PackageManagement -Repository PSGallery -Force	</p>	 
	<p>Install-Module -Name PowerShellGet -Repository PSGallery -Force	</p>		
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/22.jpg"/>
<p>•Restart the PowerShell session and run the following command to install Azure File Sync.</p>
	<p>Install-Module -Name Az.StorageSync -AllowPrerelease -AllowClobber -Force	</p>
<p>•Install the Azure File Sync PowerShell module by running the command.</p>
	<p>Invoke-AzStorageSyncCompatibilityCheck -Path 'S:\FileShare1'	•	erify that no compatibility issues have been found. 
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/23.jpg"/>
<p>•erify that no compatibility issues have been found.</p>

<h2>Prepare Azure File Sync infrastructure</h2> 
<h2>1.Deploying the Storage Sync Service:</h2>
<p>•In Server Manager, navigate to the Local Server and turn off the IE Enhanced Security Configuration.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/24.jpg"/>
<p>•Open the browser and login with your Azure account using http://portal.azure.com.</p>  	
<p>•Click on create a new resource and search for Azure File Sync.</p>  
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/25.jpg"/>
<p>•Create a Storage Sync Service with following settings and click on create.</p>  
	<p>•Name: DemoStorageSync</p> 
	<p>•Subscription: Select a valid subscription</p> 
	<p>•Resource group: Create a new resource group StorageSyncRG</p> 
	<p>•Location: Select a valid location</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/26.jpg"/>

<h2>3.Installing Azure File Sync Agent</h2>
<p>•Download the Azure File Sync Agent Windows Installer file using the link https://go.microsoft.com/fwlink/?linkid=858257 select the file StorageSyncAgent_V5_WS2016.msi and run it.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/27.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/28.jpg"/>

<h2>4.Registering Windows server with the storage sync service</h2>
<p>•In the Azure File Sync - Server Registration page, sign in by using the same Microsoft account that you used in this lab.</p> 
<p>•On the Azure File Sync - Server Registration register with your storage account o Azure Subscription: the one which you are using in this lab o Resource group: StorageSyncRG o Storage Sync Service: DemoStorageSync</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/29.jpg"/>

<h2>5.Creating a Sync group and a cloud endpoint</h2>
<p>•Navigate to the DemoStorageSync Storage Sync panel and view the Sync group panel to create a new sync group with the following settings</p>
	<p>•Sync group name: demosyncgroup1</p> 
	<p>•Azure Subscription: select a valid one</p> 
	<p>•Storage account: DemoStorage1</p> 
	<p>•Azure File Share: FileShare1 Creating Server End-Point</p> 
<p>•In the Azure portal, from the DemoStorageSync Storage Sync panel, navigate to the demosyncgroup1 and click on Add server endpoint panel and create a new server endpoint with the following settings o Registered server: DemoVM1 o Path: S:\DemoShare1 o Cloud Tiering: Enabled o Volume: 15 o Specified number of days: 30 o Offline Data Transfer: Disabled.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/30.jpg"/>

<h2>6.Validate Azure File Sync Operation</h2>
<p>•In the Azure portal, monitor the health status of the server endpoint DemoVM1 on the demosyncgroup1 panel, as it changes from red mark to green mark.</p> 
<p>•Start File Explorer and go to the Z: drive, verify that the drive contains the same content as S:\DemoShare1.</p> 
<p>•Check that the file is synced with the file you created in the storage account.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-003/31.jpg"/>

