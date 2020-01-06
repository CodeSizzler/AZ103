<h1>Implementing and Managing Storage</h1>
<h2>Introduction</h2>
<p>In this article we are going to learn how to Implement and manage a storage account in Azure Portal. Manage and secure storage account using Shared Access Signature (SAS). You can monitor the storage account in Azure by configuring alerts and metrics, Activity log. Store a cached content on a distribute network with the help of Content Delivery Network. In addition you can also learn about Azure Blob Storage.</p>

<h2>Technical requirements</h2>
<p>You must need a valid Azure Subscription and need some knowledge on Azure Storage and Template deployment to work in this session. Follow the below steps for securing and managing your Azure Storage account.</p>

<h2>Steps:</h2>

<h2>Deploying an VM using Azure Resource Manager Template:</h2>
<p>•Login with your Azure account using http://portal.azure.com</p>
<p>•From the create new resource panel search for Template Deployment.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/01.jpg"/>
<p>Select Build your own template in the editor.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/02.jpg"/>
<p>•In the edit template panel load the template file azuredeploy.json and save the template.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/03.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/04.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/05.JPG"/>
<p>•Then navigate to the Edit parameters panel and click on Load Template.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/06.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/07.JPG"/>
<p>•Load the parameters file az-100-02_azuredeploy.parameters.json.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/08.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/09.JPG"/>
<p>•Save the parameter and return to Custom deployment panel.</p>
<p>•From the Custom deployment panel, initiate a template deployment with the following settings and click on purchase.</p>
	<p>•Subscription: Select a valid one</p> 
	<p>•Resource group: the name of a new resource group demoRG</p> 
	<p>•Location: the name of the Azure region which is closest to the lab location and where you can provision</p> 
	<p>•Azure VMs o Vm Size: Standard_DS1_v2v
	<p>•Vm Name: demoVM1</p> 
	<p>•Username: Demouser</p>   
	<p>•Admin Password: for your choice</p>
	<p>•Virtual Network Name: demoVnet1</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/10.jpg"/>

<h2>Implement and use Blob Storage</h2>
<h2>Sreps:</h2>
<h2>1.Creating Azure Storage accounts:</h2>
<p>•In Azure Portal click on create new resource and search for Storage account.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/11.jpg"/>
<p>From the Create storage account panel, create a new storage account with the following settings and click on review and create.</p>
	<p>•o	Subscription: Select the valid one</p>
	<p>•Resource group: StorageRg1</p>
	<p>•Storage account name: DemoStorage1</p> 
	<p>•Location: Select the valid one</p> 
	<p>•Performance: Standard</p> 
	<p>•Account kind: Storage (general purpose v1)</p> 
	<p>•Replication: Locally-redundant storage (LRS)</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/12.jpg"/>
<p>Once the validation gets paused click on create.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/13.jpg"/>
<p>In Azure Portal click on create new resource and search for Storage account.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/14.jpg"/>
<p>From the Create storage account panel, create a new storage account with the following settings and click on review and create.</p> 
	<p>•Subscription: Select the valid one</p> 
	<p>•Resource group: StorageRG2</p>
	<p>•Storage account name: DemoStorage2</p> 
	<p>•Location: Select the valid location</p>
	<p>•Performance: Standard</p> 
	<p>•Account kind: Storage (general purpose v2)</p> 
	<p>•Replication: Geo-redundant storage (GRS)</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/15.jpg"/>
<p>Once your validation gets paused click on Create.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/16.jpg"/>

<h2>2.Review configuration settings of Azure Storage account:</h2> 
<p>•In Azure Portal navigate to the storage account DemoStorage1 and review the storage account configuration.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/17.jpg"/>
<p>•Display the Access keys panel. Here you can copy the values of key1 and key2. You can also regenerate each of the keys.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/18.jpg"/>
<p>•Display the Configuration panel and review the settings.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/19.jpg"/>
<p>•Display the Encryption panel of the storage account and note the encryption type.</p>
<p>•Move to the storage account that you have created second and display the configuration panel.</p>
<p>•Note that you have the option of editing the parameters.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/20.jpg"/>
<p>•Display the Encryption panel and note the encryption type.</p>

<h2>3.Manage Azure Storage Blob Service:</h2>
<p>•Navigate to the blob panel of DemoStorage1 and create a new container in the name of DemoContainer1 and select the public access level to private.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/21.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/22.jpg"/>
<p>•In the created container panel, click on upload and load the file azuredeploy.json and azuredeploy.parameters.json into the container and save it.</p>  
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/23.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/24.jpg"/>

<h2>4.Copy a container and blobs between Azure Storage account:</h2>
<p>•In Azure Portal, start a PowerShell session.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/25.jpg"/>
<p>•Run the following command in the PowerShell with valid string.</p>
	<p>$storageAccount1Name = (Get-AzStorageAccount -ResourceGroupName 	</p>
	<p>'DemoRG1')[0].StorageAccountName	</p> 
	<p>$storageAccount2Name = (Get-AzStorageAccount -ResourceGroupName	</p> 
	<p>'StorageRG1')[0].StorageAccountName	</p> 
	
	<p>$storageAccount1Key1 = (Get-AzStorageAccountKey -ResourceGroupName 'StorageRG1'	</p> 
	<p>StorageAccountName $storageAccount1Name)[0].Value	</p> 
	<p>$storageAccount2Key1 = (Get-AzStorageAccountKey -ResourceGroupName 'StorageRG2' -	</p>
	<p>StorageAccountName $storageAccount2Name)[0].Value	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/26.jpg"/>
<p>•After getting the output for the previous command run the command</p>
	<p>azcopy --source	</p> 
	<p>https://$storageAccount1Name.blob.core.windows.net/DemoContainer1/ -destination	</p> 
	<p>https://$storageAccount2Name.blob.core.windows.net/DemoContainer1/ --sourcekey 	</p>
	<p>$storageAccount1Key1 --dest-key $storageAccount2Key1 --include "az" -sync-copy	</p>
	<p>--recursive	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/27.jpg"/>
<p>•Verify that the command output confirm two files were transferred.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/28.jpg"/>
<p>•Navigate to the Blobs panel of DemoStorage2 and verify that it includes entry of the newly created container and that the container includes two copied blobs.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/29.jpg"/>

<h2>5.Use a Shared Access Signature key to access a blob:</h2>
<p>•Copy the value of URL property from the Blobs panel of DemoStorage2, navigate to the container that you created first, and then open the azuredeploy.json panel.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/30.jpg"/>
<p>•Open the browser and search for the URL that you have copied and note the error statement.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/31.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/32.jpg"/>
<p>•In the azuredeploy.json panel, generate a shared access signature and the corresponding URL using the following settings then generate the SAS key. o Permissions: Read o Start date/time: specify the current date/time in your current time zone o Expiry date/time: specify the date/time 24 hours ahead of the current time o Allowed IP addresses: none o Allowed protocols: HTTP o Signing key: Key 1</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/33.jpg"/>
<p>•Copy the generated SAS key and browse for it.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/34.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/35.jpg"/>
<p>•Note that this time azuredeploy.json is prompted.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/36.jpg"/>

<h2>Implement and use Azure File Storage:</h2>
<h2>1.Creating Azure File Service Share:</h2>
<p>•Navigate to the DemoStorage2 and display the file sharing properties.</p> 
<p>•In the file sharing panel create a new file share with the following settings o Name: FileShareDS2 o Quota: 5GB</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/37.jpg"/>

<h2>Map a drive to the Azure File Service share from an Azure VM:</h2>
<p>•Navigate to the FilShareDS2 and display the Connect panel.</p>
<p>•Copy the PowerShell commands that connect to the file share from a Windows computer.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/38.jpg"/>
<p>•Then navigate to the DemoVM1 panel and connect to it using RDP protocol and sign in with the respective credentials which you have provided while creating the Virtual Machine.</p>
<p>•Start a Windows PowerShell ISE session in the Virtual Machine and run the command that you have copied in the previous session.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/39.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/40.jpg"/>
<p>•Verify that its output confirms mapping of the Z: drive to the Azure Storage File Service share successfully.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/41.jpg"/>
<p>•Open the File Explorer and navigate to the Z: drive then create a new folder.</p>
<p>•In the created folder create a text document.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/42.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-002/43.jpg"/>

