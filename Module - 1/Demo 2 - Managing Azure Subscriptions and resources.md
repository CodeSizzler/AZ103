<h1>Configuring delegation of provisioning and management of Azure resources by using built-in Role-Based Access Control (RBAC) roles and built-in Azure policies</h1>
 

<h2>Steps:</h2>

<h2>1.Creating Azure AD users and groups:</h2>
<p>•Login to Azure Portal http://portal.azure.com using a Microsoft account that has the Owner role in the Azure subscription you intend to use in this lab and is a Global Administrator of the Azure AD tenant associated with that subscription.</p> 
<p>•In Azure Portal navigate to Azure Active Directory.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-02/01.jpg"/>
<p>•From the Azure Active Directory, navigate to the Custom domain names and identify the primary DNS domain name associated the Azure AD tenant or identify it as shown in the figure.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-02/02.jpg"/>
<p>•From the Azure AD Custom domain names, navigate to the Users - All users.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-02/03.jpg"/>
<p>•Select New User and enter the respective values and note don the password generated and click on Create.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-02/04.jpg"/>
<p>•From the Users - All users, navigate to the Groups - All groups and click on create a new group.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-02/05.jpg"/>
<p>•For group type select Security and enter the required values and click on Create.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-02/06.jpg"/>

<h2>2.Creating Azure resource groups:</h2>
<p>•In the Azure portal, navigate to the Resource groups and click on Add.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-02/07.jpg"/>
<p>•Enter the required values and click on review and create. Once your navigation paused click on create.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-02/08.jpg"/>
<p>•From the Resource groups blade, create the second resource group.</p>
<p>•After entering the required values click on review and create. Once your navigation paused click on create.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-02/09.jpg"/>

<h2>3.Delegate management of an Azure resource group via a built-in RBAC role:</h2>
<p>•In the resource group panel click on demoRG1 and navigate to Access Control (IAM) then click on Role Assignments.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-02/10.jpg"/>
<p>•In the role assignment panel click on Add and select Add role assignment.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-02/11.jpg"/>
<p>•Then add the required values and select the demogroup contribution and click on save.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-02/12.jpg"/>

<h2>4.Assigning a built-in Azure policy to an Azure resource group:<h2>
<p>•From the demoRG1 resource group select Policy Compliance and click on Assign Policy.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-02/13.jpg"/>
<p>•Then enter the following details;</p>
	<p>•Scope: demoRG1</p> 
	<p>•Exclusions: leave the entry blank</p> 
	<p>•machine SKUs Policy definition: Allowed virtual</p> 
	<p>•Assignment name: Allowed virtual machine SKUs</p> 
	<p>•Description: Allowed selected virtual machine SKUs (Standard_DS1_v2)</p> 
	<p>•Assigned by: leave the entry set to its default value</p> 
	<p>•Allowed SKUs: Standard_DS1_v2</p> 
	<p>•Create a Managed Identity: leave the entry blank</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-02/14.jpg"/>

<h2>Verify delegation by provisioning Azure resources as a delegated admin and auditing provisioning events:</h2>

<h2>Steps:</h2>

<h2>1.Identify an available DNS name for an Azure VM deployment:</h2>
<p>In Azure Portal, start a PowerShell session in the Cloud Shell.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-02/15.jpg"/>
<p>•Run the following command with the required string.</p>
	<p>Test-AzDnsAvailability -DomainNameLabel <custom-label> -Location '<location-of-az1000101-RG>'</p>
<p>•Verify that the command returned True.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-02/16.jpg"/>

<h2>2.Attempt an automated deployment of a policy non-compliant Azure VM as a delegated admin:</h2>
<p>•Open a new browser in private mode and login to your Azure account using Azure Portal.</p>
<p>•Note that you can only able to view demoRG1.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-02/17.jpg"/>
<p>•Click on Create a resource and search for Template Deployment and navigate to Deploy a custom template.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-02/18.jpg"/>
<p>•On the Custom deployment panel, in the Load a GitHub quickstart template drop-down list, select the 101-vm-simple-linux entry and navigate to the Edit template panel.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-02/19.jpg"/>
<p>•On the Edit template blade, navigate to the Variables section and locate the vmSize entry. Note that the template is using Standard_A1 VM size.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-02/20.jpg"/>
<p>•Discard any changes you might have made to the template and navigate to the Deploy a simple Ubuntu Linux VM.</p>
<p>•From the Deploy a simple Ubuntu Linux VM blade, initiate a template deployment with the following settings and click on purchase.</p>
	<p>•Subscription: the same subscription you selected in the previous exercise</p>  
	<p>•Resource group: demoRG1</p>  
	<p>•Location: the name of the Azure region which you selected in the previous exercise</p> 
	<p>•Admin Username: For your choice</p>  
	<p>•Admin Password: For your choice</p>  
	<p>•Dns Label Prefix: the <custom-label> you identified in the previous task</p>  
	<p>•Ubuntu OS Version: accept the default value</p> 
	<p>•Location: accept the default value</p>  
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-02/21.jpg"/>
<p>•Note that the intiation of the deployment fails. Navigate to the Errors blade and note that the deployment of the resource is not allowed by the policy Allowed virtual machine SKUs.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-02/22.jpg"/>

<h2>3.Perform an automated deployment of a policy compliant Azure VM as a delegated admin:</h2>
<p>•From the Deploy a simple Ubuntu Linux VM panel, navigate to the Edit template.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-02/23.jpg"/>
<p>•On that navigate to navigate to variables section and locate vmSize entry.</p>
<p>•Then replace the value Standard_A1 with Standard_DS1_v2 and save the change.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-02/24.jpg"/>
<p>•Initiate the deployment again. Note that this time the validation will get success.</p> 

<h2>4.Review Azure Activity Log events corresponding to Azure VM deployments:</h2>
<p>•Switch to the normal browser and login to Azure account using Azure Portal.</p> 
<p>•Navigate to demoRG1 resource group.</p> 
<p>•In that resource group panel display its Activity log.</p> 
<p>•In the list of operations, note the ones corresponding to the failed and successful validation events.</p> 
<p>•Refresh the view of the blade and observe events corresponding to the Azure VM provisioning, including the final one representing the successful deployment.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-02/25.jpg"/>


	
	
	

 


























<p>1. Launch the Azure Policy service in the Azure portal by clicking All services then, Everything, then type Policy in the search box and select Policy.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az900-002/1.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az900-002/2.jpg"/>
<p>Note: Azure Policy is also accessible under the All services > Management + governance section in the portal.</p>
<p>2. Go to Authoring > Definitions and take a moment to have a quick browse through the list of built-in policy definitions that are available for you to use.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az900-002/3.jpg"/>
<p>3. Select Assignments on the left side of the Policy page. An assignment is a policy that has been assigned to take place within a specific scope.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az900-002/4.jpg"/>
<p>4. Select Assignments on the left side of the Policy page. An assignment is a policy that has been assigned to take place within a specific scope.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az900-002/5.jpg"/>
<p>5. Select Assign Policy from the top of the Policy - Assignments page and on the subsequent Assign Policy page, select the Scope selector by clicking the ellipsis and setting the following values, then click Select at the bottom of the Scope page.</p>
<p>•Subscription: < choose your own subscription > </p>
<p>•Resource Group: < accept the default value i.e. leave blank > </p> 
<p>Note: A scope determines what resources or grouping of resources the policy assignment gets enforced on. In our case we could assign this policy to a specific resource group, however we will assign the policy at subscription level. Also, be aware that resources can be excluded based on the Scope. Exclusions are optional.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az900-002/6.jpg"/>
<p>6. Select the Policy definition ellipsis button to open the list of available definitions. Azure Policy comes with built-in policy definitions you can use, this is the same list that we saw earlier in the Definitions pane. Many are available, such as the below, but again you can take a quick moment to scroll through and search for ones that may interest you:</p> 
<p>•Require tag and its value</p>
<p>•Append tag and its value</p>
<p>•Require SQL Server version 12.0</p>
<p>In the Available Definitions pane in the Search box type location and click on the Allowed locations definition, then click Select.</p>
<p>Note: This Allowed Locations policy definition will specify a location into which all resources must be deployed. If a different location is chosen deployment will not be allowed. For a partial list of available built-in policies, you can also see them at the https://docs.microsoft.com/en-us/azure/governance/policy/samples/index page.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az900-002/7.jpg"/> 
<p>7. In the Assign policy pane, in the PARAMETERS section, click on the arrow at the end of the Allowed locations box and from the subsequent list choose Japan West. Leave all other values as they are and Click Assign.</p>
<p>Note: The Assignment name is automatically populated with the policy name you selected, but you can change it if you wish. You can also add an optional Description and Assigned by will automatically fill based on whoever is logged in. This field is optional, so custom values can be entered. Leave the Create a Managed Identity option unchecked. However, this box must be checked when the policy or initiative includes a policy with the deployIfNotExists effect.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az900-002/8.jpg"/> 
<p>8. The Allowed locations policy assignment is now listed on the Policy - Assignments pane and it is now in place and available to enforce at the scope level we specified i.e. at subscription level.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az900-002/9.jpg"/>   
<img src="https://codesizzlergit.blob.core.windows.net/az900-002/10.jpg"/>   
<img src="https://codesizzlergit.blob.core.windows.net/az900-002/11.jpg"/>   

<h2>Test Allowed location policy:</h2> 
<p>1. In the Azure Portal, in the FAVORITES list on the left hand side, then click Create virtual machine.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az900-002/12.PNG"/>
<p>2. In the Create a virtual machine pane on the Basics tab fill in the fields with the following values, leaving all other values as default, and Click Review + create:</p>
<p>•Subscription: < select your own subscription. Ensure it is the same subscription you assigned the allowed locations policy to earlier> </p>
<p>•Resource group: click Create new and enter a value i.e. vmpolcheckrg</p>
<p>•Virtual machine name: vmpolcheck1</p>
<p>•Region: select any Datacenter location other than the one that you used as a parameter value earlier in the policy assignment i.e. we assigned Japan West earlier as the allowed Datacenter location, so use (Europe) North Europe now</p>
<p>•Username: azureuser</p> 
<p>•Password: Password0134!</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az900-002/13.PNG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az900-002/14.PNG"/>
<p>3. You will receive a Validation failed message, and click on the Click here to view details message the resultant Errors blade, on the Summary tab note the error message, Resource xyz was disallowed by Policy and the policy name listed as Allowed locations.</p>
<p>You can dig in further for specifics, by clicking on the Raw Error tab and viewing the output and also by clicking on the Allowed locations policy, to view the policy that blocked the deployment.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az900-002/15.jpg"/>

<h2>Delete the policy assignment:</h2> 
<p>1. In the Azure Portal click All Services > Management + governance then Policy and on the Policy pane select Compliance in the left side of the page. Within this pane you can view the compliance state of the various policies you have assigned.</p>
<p>Note:The Allowed location policy is listed as non-compliant in the screenshot, as there are pre-existing resources deployed outside of Japan West, which were created prior to the policy assignment, when using Azure Cloud Shell and other Azure resources.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az900-002/16.PNG"/>
<p>2. Go to Assignments and click on the ellipsis at the end of the Allowed locations policy assignment. Then select Delete Assignment from the resultant menu.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az900-002/17.jpg"/>  
<p>3. Confirm you wish to delete the policy assignment in the Delete assignment dialogue by clicking Yes.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az900-002/18.jpg"/>     
