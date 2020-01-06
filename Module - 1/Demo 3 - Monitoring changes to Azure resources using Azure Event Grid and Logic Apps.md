<h1>Monitoring changes to Azure resources using Azure Event Grid and Logic Apps</h1>

<h2>Introduction</h2>
<p>This article helps you to monitor Azure resources using Azure Event Grid and Azure Logic App.</p>

<h2>Prerequisites</h2>
<p>To preform this demo user must have a valid Azure subscription and some knowledge on Logic App and Event Grid.</p>

<h2>Demo</h2>
<p>Log-in to Azure portal with your Azure account using www.portal.azure.com. In Azure portal click on Create a new resource and search for Storage account. Use the search list and create a storage account with following configurations.</p>  
	<p>•Subscription: Select a valid subscription</p> 
	<p>•Resource group: Create a new resource group DemoStorageRG</p> 
	<p>•Storage account name: codesizzlerstorage</p> 
	<p>•Location: Select a valid location</p> 
	<p>•Performance: Standard</p> 
	<p>•Account type: General purpose v1</p> 
	<p>•Replication: LRS</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/01.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/02.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/03.JPG"/>
<p>After configuring the above settings click on Advanced. In the advanced settings panel review the settings and click on Review+Create.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/04.jpg"/>
<p>Once your validation gets paused click on create.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/05.jpg"/>
<p>In Azure portal click on Create a new resource and search for Logic App.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/06.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/07.JPG"/>
<p>Create a Logic App with following settings and click on create.</p>
	<p>•Name: CodesizzlerLogiApp</p>  
	<p>•Subscription: Select a valid subscription</p>  
	<p>•Resource group: Create a new resource group LogicAppRg</p>  
	<p>•Location: Select a valid location</p>  
	<p>•Log analytics: Off</p>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/08.jpg"/>
<p>After creating Logic App start a PowerShell session in Cloud Shell panel.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/09.jpg"/>
<p>In the PowerShell panel run the following commands to create a new Active Directory application.</p>
	<p>$password = 'Codesizzler@1'	</p> 
	<p>$securePassword = ConvertTo-SecureString -Force -AsPlainText -String		</p> 
	<p>$password$codesizzlerapp = New-AzADApplication -DisplayName 'codesizzlerapp' -	</p>
	<p>HomePage 'http://codesizzlerapp' -IdentifierUris 'http://codesizzlerapp' Password	</p> 
	<p>$securePassword	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/10.jpg"/>
<p>After creating the Active Directory application run the following command to create a new Azure AD service principal.</p>
	<p>New-AzADServicePrincipal -ApplicationId $aadApp1010201b.ApplicationId.Guid 	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/11.jpg"/>
<p>After running the command note the output you will use it after in this session.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/12.jpg"/>
<p>Run the following command to display the subscription properties.</p>
	<p>Get-AzSubscription 	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/13.jpg"/>
<p>In Azure portal navigate to the subscription that you are using in this demo. In the subscription panel click on Access control (IAM) panel assign a reader role to codesizzlerapp service principle.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/14.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/15.JPG"/>
<p>Configure the following settings:</p>
	<p>•Role: Reader.</p> 
	<p>•Assign access to: Azure AD user, group or service principle.</p> 
	<p>•Select: In the select panel past the Application ID that you have identified in the previous step.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/16.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/17.JPG"/>
<p>After adding the role run the following command to register with Event Grid rsource provider.</p>
	<p>Register-AzResourceProvider -ProviderNamespace Microsoft.EventGrid 	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/18.jpg"/>
<p>Navigate to CodesizzlerLogicApp, in the Logic App designer panel click on Blank Logic App.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/19.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/20.jpg"/>
<p>In the Search connectors and triggers text box search for Event Grid and select When a resource event occurs (preview) Azure Event Grid to the designer work space.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/21.jpg"/>
<p>Click on connect with service principle and configure the following settings:</p>
	<p>•Connection name: Codesizzler</p>  
	<p>•Client ID: Past the application ID that you found earlier in this session</p> 
	<p>•Client secret: Codesizzler@1</p> 
	<p>•Tenant: Tenant ID found earlier in this session</p>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/22.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/23.JPG"/>
<p>In the When a resource event occurs tile provide the following details.</p>
	<p>•Subscription: Provide the subscription ID that you have identified in the previous step</p> 
	<p>•Resource type: Microsoft.Resources.resourceGroups</p> 
	<p>•Resource name: Provide the subscription ID that you have identified earlier in this step</p> 
	<p>•Event type item-1: Microsoft.Resources.ResourceWriteSuccess</p> 
	<p>•Event type item-2: Microsoft.Resources.ResourceDeleteSuccess</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/24.jpg"/>
<p>After adding the Event Grid tile click on +New step and search for Outlook. When it prompts select Outlook.com</p>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/25.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/26.jpg"/>
<p>After adding outlook use the Search connection and action to select Send an email.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/27.jpg"/>
<p>Click on sign-in, when it prompts log-in with your office account.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/28.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/29.JPG"/>
<p>When it prompts provide the access.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/30.jpg"/>
<p>In the send an email tile provide the following and click on save.</p>
	<p>•To: A valid mail id for which you need to send the mail</p> 
	<p>•Subject: Click on Subject and type Resource update</p> 
	<p>•Body: Select Event time, Event type, ID, Subject, Topic</p>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/31.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/32.jpg"/>
<p>Navigate to the CodesizzlerLogicApp panel and click on See trigger history.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/33.jpg"/>
<p>In the trigger history copy the Call-back URL.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/34.jpg"/>
<p>In Azure portal navigate to LogicAppRg and click on azureeventgrid.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/35.jpg"/>
<p>In the event panel click on Web Hook.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/36.jpg"/>
<p>When it prompts configure the following settings and click on create.</p>
	<p>•Name: Codesizzler</p> 
	<p>•Event type: For event type select Resource Write Success Resource Delete Success</p> 
	<p>•End-point type: Web Hook</p> 
	<p>•End-point: Click on select an end-point, when it prompts paste the Call back URL which you have identified in the previous step.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/37.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/38.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/39.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/40.jpg"/>
<p>In Azure portal navigate to the codesizzlerstorage account.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/41.jpg"/>
<p>In the storage account panel navigate to Configuration panel and disable the Secure Transfer option.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/42.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/43.JPG"/>
<p>Save the changed settings and navigate to the CodesizzlerLogicApp and monitor the Run History. Note that all the steps has succeeded including the last one.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/44.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/45.JPG"/>
<p>Open a browser and log in the mail id which you have provided in the send an email tile. Note that a mail from Microsoft Outlook has been received.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az-103-1-03/46.jpg"/>
