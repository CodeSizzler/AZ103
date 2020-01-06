<h1>Managing Azure Subscription and Resources</h1>

<h2>Introduction</h2>
<p>This article helps you to configure delegation of provisioning and management of Azure resources by using built-in Role-Based Access Control (RBAC) roles and built-in Azure policies</p>

<h2>Pre-requisite</h2>
<p>To perform this demo you must have valid Azure subscription and some basic knowledge on Azure Active Directory, Role Based Access Control.</p>

<h2>Steps:</h2>
<h2>1.Creating Azure AD users and groups:</h2>
<p>Login to Azure Portal http://portal.azure.com using a Microsoft account that has the Owner role in the Azure subscription you intend to use in this lab and is a Global Administrator of the Azure AD tenant associated with that subscription.</p>
<p>In Azure Portal navigate to Azure Active Directory.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-002/01.jpg"/>
<p>From the Azure Active Directory, navigate to the Custom domain names and identify the primary DNS domain name associated the Azure AD tenant or identify it as shown in the figure.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-002/02.jpg"/>
<p>From the Azure AD Custom domain names, navigate to the Users - All users.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-002/03.jpg"/>
<p>Select New User and enter the respective values and note don the password generated and click on Create.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-002/04.jpg"/>
<p>From the Users - All users, navigate to the Groups - All groups and click on create a new group.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-002/05.jpg"/>
<p>For group type select Security and enter the required values and click on Create.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-002/06.jpg"/>

<h2>2.Creating Azure resource groups:</h2>
<p>In the Azure portal, navigate to the Resource groups and click on Add.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-002/07.jpg"/>
<p>Enter the required values and click on review and create. Once your navigation paused click on create.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-002/08.jpg"/>
<p>From the Resource groups blade, create the second resource group.</p>
<p>After entering the required values click on review and create. Once your navigation paused click on create.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-002/09.jpg"/>

<h2>3.Delegate management of an Azure resource group via a built-in RBAC role:</h2>
<p>In the resource group panel click on demoRG1 and navigate to Access Control (IAM) then click on Role Assignments.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-002/10.jpg"/>
<p>In the role assignment panel click on Add and select Add role assignment.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-002/11.jpg"/>
<p>Then add the required values and select the demogroup contribution and click on save.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-002/12.jpg"/>

<h2>4.Assigning a built-in Azure policy to an Azure resource group:</h2>
<p>From the demoRG1 resource group select Policy Compliance and click on Assign Policy.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-002/13.jpg"/>
<p>•Then enter the following details:</p>
	<p>•Scope: demoRG1</p>
	<p>•Exclusions: leave the entry blank</p>
	<p>•Policy definition: Allowed virtual machine SKUs</p>
	<p>•Assignment name: Allowed virtual machine SKUs</p>
	<p>•Description: Allowed selected virtual machine SKUs (Standard_DS1_v2</p>
	<p>•Assigned by: leave the entry set to its default value</p>
	<p>•Allowed SKUs: Standard_DS1_v2</p>
	<p>•Create a Managed Identity: leave the entry blank</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-002/14.jpg"/>

<h2>Verify delegation by provisioning Azure resources as a delegated admin and auditing provisioning events:</h2>
<h2>1.Identify an available DNS name for an Azure VM deployment:</h2>
<p>In Azure Portal, start a PowerShell session in the Cloud Shell.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-002/15.jpg"/>
<p>Run the following command with the required string.</p>
	<p>Test-AzDnsAvailability -DomainNameLabel <custom-label> -Location '<location-of-az1000101-RG>'	</p>
<p>Verify that the command returned True.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-002/16.jpg"/>

<h2>2.Attempt an automated deployment of a policy non-compliant Azure VM as a delegated admin:</h2>
<p>Open a new browser in private mode and login to your Azure account using Azure Portal.</p>
<p>Note that you can only able to view demoRG1.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-002/17.jpg"/>
<p>Click on Create a resource and search for Template Deployment and navigate to Deploy a custom template.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-002/18.jpg"/>
<p>On the Custom deployment panel, in the Load a GitHub quickstart template drop-down list, select the 101-vm-simple-linux entry and navigate to the Edit template panel.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-002/19.jpg"/>
<p>On the Edit template blade, navigate to the Variables section and locate the vmSize entry. Note that the template is using Standard_A1 VM size.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-002/20.jpg"/>
<p>Discard any changes you might have made to the template and navigate to the Deploy a simple Ubuntu Linux VM.</p>
<p>From the Deploy a simple Ubuntu Linux VM blade, initiate a template deployment with the following settings and click on purchase.</p>
	<p>•Subscription: the same subscription you selected in the previous exercise</p>
	<p>•Resource group: demoRG1</p>
	<p>•Location: the name of the Azure region which you selected in the previous exercise</p>
	<p>•Admin Username: For your choice</p>
	<p>•Admin Password: For your choice</p>
	<p>•Dns Label Prefix: the <custom-label> you identified in the previous task</p>
	<p>•Ubuntu OS Version: accept the default value</p>
	<p>•Location: accept the default value</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-002/21.jpg"/>
<p>Note that the intiation of the deployment fails. Navigate to the Errors blade and note that the deployment of the resource is not allowed by the policy Allowed virtual machine SKUs.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-002/22.jpg"/>

<h2>3.Perform an automated deployment of a policy compliant Azure VM as a delegated admin:</h2>
<p>From the Deploy a simple Ubuntu Linux VM panel, navigate to the Edit template.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-002/23.jpg"/>
<p>On that navigate to navigate to variables section and locate vmSize entry.</p>
<p>Then replace the value Standard_A1 with Standard_DS1_v2 and save the change.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-002/24.jpg"/>
<p>Initiate the deployment again. Note that this time the validation will get success.</p>

<h2>4.Review Azure Activity Log events corresponding to Azure VM deployments:</h2>
<p>Switch to the normal browser and login to Azure account using Azure Portal.</p>
<p>Navigate to demoRG1 resource group.</p>
<p>In that resource group panel display its Activity log.</p>
<p>In the list of operations, note the ones corresponding to the failed and successful validation events.</p>
<p>Refresh the view of the blade and observe events corresponding to the Azure VM provisioning, including the final one representing the successful deployment.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-002/25.jpg"/>
