<h1>Manage Azure Subscriptions and Resources - Implementing governance and compliance with Azure initiatives and resource locks</h1>
<h2>Implementing Azure tags by using Azure policies and initiatives:</h2>
 
<h2>Steps:</h2>

<h2>1.Provision Azure Resource by using Azure Resource Manager Template:</h2>
<p>•Login to your Azure account with Azure Portal using http://portal.azure.com</p>
<p>•In Azure Portal click on create a new resource and search for Template Deployment.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/01.jpg"/>
<p>•Select Build your own template in the editor in the custom deployment blade.</p>  
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/02.jpg"/>
<p>•In the edit template blade load the template file az-100-01b_azuredeploy.json and save the template.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/03.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/04.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/05.JPG"/>
<p>•Then navigate to the Edit parameters blade and click on Load Template.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/06.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/07.JPG"/>
<p>•Load the parameters file az-100-01b_azuredeploy.parameters.json.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/08.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/09.JPG"/>
<p>•Save the parameter and return to Custom deployment blade.</p>
<p>•From the Custom deployment blade, initiate a template deployment.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/10.jpg"/>
<p>•After deploying the template navigate to Tags and display the resource with Environment tag set to the value Lab.</p>
<p>•Note that only some of the resources deployed in the previous task have this tag assigned.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/11.jpg"/>

<h2>2.Implement a policy and an initiative that evaluate resource tagging compliance:</h2>
<p>•In the Azure Portal navigate to Policy > Policy definition.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/12.jpg"/>
<p>•From the Policy Definitions blade, display the Enforce tag and its value policy definition.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/13.jpg"/>
<p>•From the Enforce tag and its default value policy definition blade, use the duplicate the definition feature to create a new policy with the following settings:</p> 
	<p>•Definition location: the name of the subscription you are using in this lab.</p>
	<p>•Name: az10001b - Audit tag and its value o Description: Audits a required tag and its value. Does not apply to resource groups.</p>  
	<p>•Category: the name of a new category Lab o Policy rule: the existing policy rule with the effect set to audit, such that the policy definition has the following content and save it.</p>
	
	<p>1.	{	</p>
	<p>2.	"mode": "indexed",	</p>
	<p>3.	"policyRule": {		</p>
	<p>4.	"if": { 	</p>	
	<p>5.	"not": { 	</p>
	<p>6.	"field": "[concat('tags[', parameters('tagName'), ']')]",	</p> 	  	
	<p>7.	"equals": "[parameters('tagValue')]"	</p>	 	
	<p>8.	} 	</p>
	<p>9.	},	</p>
	<p>10.	"then": { 	</p>
	<p>11.	"effect": "audit"	</p> 	
	<p>12.	} 	</p>
	<p>13.	}, 	</p>
	<p>14.	"parameters": { 	</p>
	<p>15.	"tagName": { 	</p>
	<p>16.	"type": "String", 	</p>
	<p>17.	"metadata": { 	</p>
	<p>18.	"displayName": "Tag Name", 	</p>
	<p>19.	"description": "Name of the tag, such as 'environment'"		</p>		 
	<p>20.	} 	</p>
	<p>21.	}, 	</p>
	<p>22.	"tagValue": { 	</p>
	<p>23.	"type": "String", 	</p>
	<p>24.	"metadata": { 	</p>
	<p>25.	"displayName": "Tag Value",	</p> 	
	<p>26.	"description": "Value of the tag, such as 'production'"		</p> 
	<p>27.	} 	</p>
	<p>28.	} 	</p>
	<p>29.	} 	</p>
	<p>30.	} 	</p>

<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/14.jpg"/>
<p>•From the Policy - Definitions blade, navigate to the New Initiative definition and create a new initiative definition with the following settings o Definition location: the name of the subscription you are using in this lab o Name: demoRG1 - Tagging initiative o Description: Collection of tag policies.</p> 
	<p>•Category: Lab o Policy rule: the existing policy rule with the effect set to audit, such that the policy definition has the following content:</p> 	
	<p>•POLICIES AND PARAMETERS: demoRG1 - Audit tag and its value o Tag Name: environment o Tag Value: lab.</p> 
<p>•Then navigate to Policy-Assessment blade.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/15.jpg"/>
<p>•From the Policy - Assignments blade, navigate to the Assign initiative blade.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/16.jpg"/>
<p>•Create a new Initiative assessment with the following settings.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/17.jpg"/>
<p>•You will be redirected to the Policy - Compliance blade. Note that COMPLIANCE STATE is set to Not started.</p> 

<h2>3.Implementing a policy that enforces resource tagging compliance:</h2> 
<p>•Navigate to demoRG1-tagging initiative blade and go to Edit initiative definition blade.</p>  
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/18.jpg"/>
<p>•Add the built-in policy definition named Enforce tag and its default value to the initiative and set its parameters and click on save.</p> 
 	<p>•Tag name: Environment</p>   
 	<p>•Tag value: Lab </p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/19.jpg"/>

<h2>4.Evaluate tagging enforcement and tagging compliance:</h2> 
<p>•Click on create new resource and search for Template Deployment.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/20.jpg"/>
<p>•On the Custom deployment blade, select the Build your own template in the editor.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/21.jpg"/>
<p>•In the edit template blade load the template file az-100-01b_azuredeploy.json and save the template.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/22.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/23.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/24.JPG"/>
<p>•Then navigate to the Edit parameters blade and click on Load Template.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/25.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/26.JPG"/>
<p>•Load the parameters file az-100-01b_azuredeploy.parameters.json.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/27.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/28.JPG"/>
<p>•Save the parameter and return to Custom deployment blade.</p> 
<p>•From the Custom deployment blade, initiate a template deployment with the following settings and click on purchase.</p> 
	<p>•Subscription: the name of the subscription you are using in this lab.</p>  
	<p>•Resource group: the name of a new resource group az1000102b-RG.</p>  
	<p>•Location: the name of the Azure region which you chose in the first task of this exercise.</p>  
	<p>•Vm Size: Standard_DS1_v2 o Vm Name:</p> 
	<p>•az1000102b-vm1 o Admin Username:</p> 
	<p>•Student o Admin Password: Pa55w.rd1234</p>
	<p>•Virtual Network Name: az1000102b-vnet1</p>
	<p>•Environment Name: lab</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/29.jpg"/>
<p>•Note the message that indicating validation errors. Review the error details, indicating that deployment of resource az1000102b-vnet1 was disallowed by the policy Enforce tag and its value which is included in the az10001b - Tagging initiative assignment.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/30.jpg"/>
<p>•Close the Custom Deployment blade and go to policy compliance. Identify compliance state. It will be identified as non-compliant.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/32.jpg"/>

<h2>5.Implementing remediation of resource tagging non-compliance:</h2>
<p>•Navigate to the az10001b - Tagging initiative blade and go to Edit initiative definition blade.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/33.jpg"/>
<p>•Add the built-in policy definition named Apply tag and its default value to the initiative and set its parameters to the following values.</h2> 
	<p>•Tag name: Environment</p> 
	<p>•Tag Value: Laab</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/34.jpg"/>
<p>•Delete the custom policy definition named az10001b - Audit tag and its value from the initiative. Also delete the built-in policy definition named Enforce tag and its value from the initiative and save it.</p>   
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/35.jpg"/>
<p>•Open the PowerShell session in the CloudShell and run the following command.</p>   
	<p>Get-AzResource -ResourceGroupName 'az1000101b-RG' | ForEach-Object {Set-AzResource -ResourceId $_.ResourceId -Tag @{environment="lab"} -Force } 	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/36.jpg"/>
<p>•After the command run finish move to the Tag blade and view all resources with the environment tag set to the value lab. Verify that all resources in both resource groups az1000102b-RG and az1000102b-RG are listed.</p>  
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/37.jpg"/>

<h2>6.Evaluate effects of the remediation task on compliance:</h2>
<p>•Click on create new resource and search for Template Deployment.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/38.jpg"/>
<p>•On the Custom deployment blade, select the Build your own template in the editor.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/39.jpg"/>
<p>•In the edit template blade load the template file az-100-01b_azuredeploy.json and save the template.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/40.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/41.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/42.JPG"/>
<p>•Then navigate to the Edit parameters blade and click on Load Template.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/43.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/44.JPG"/>
<p>•Load the parameters file az-100-01b_azuredeploy.parameters.json.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/45.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/46.JPG"/>
<p>•Save the parameter and return to Custom Deployment blade.</p> 
<p>•Initiate a template deployment with following settings:</p>
	<p>•Subscription: the name of the subscription you are using in this lab.</p>
	<p>•Resource group: az1000102b-RG</p> 
	<p>•Location: the name of the Azure region which you chose in the first task of this exercise</p> 
	<p>•Vm Size: Standard_DS1_v2</p>  
	<p>•Vm Name: az1000102b-vm1</p> 
	<p>•Admin Username: Student</p>  
	<p>•Admin Password: Pa55w.rd1234</p>  
	<p>•Virtual Network Name: az1000102b-vnet1</p> 
	<p>•Environment Name: lab</p>  
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/47.jpg"/>
<p>•After adding all the values click on Purchase. Note that this time the initiation will get succeed.</p>
<p>•Then move to the Tag blade and view all resources with the environment tag set to the value lab. Note that all the resources deployed in the previous task have this tag assigned.</p> 
<p>•Navigate to the demoRG1 - Tagging initiative assignment blade. Identify the entry in the COMPLIANCE STATE column. If the column contains the Not started entry, wait until it the compliance scan runs.</p> 
  
<h2>Implementing Azure resource lock:</h2>

<h2>Steps:</h2>

<h2>1.Creating resource group level locks to prevent accidental changes:</h2>
<p>•Navigate to demoRG1 resource group panel.</p> 
<p>•From the demoRG1 resource group blade, display the demoRG1 - Locks blade.</p>  
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/48.jpg"/>
<p>•Add a lock with following settings:</p> 
	<p>•Lock name: demoRG1-roLock</p>  
  	<p>•Lock type: Read only</p> 	 
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/49.jpg"/>

<h2>2.Validating the functionality of resource group-level locks;</h2>
<p>•Navigate to the az1000102b-vm1 virtual machine blade.</p> 
<p>•From the az1000102b-vm1 virtual machine blade, navigate to the az1000102b-vm1 - Tags blade and try to set the value of the environment tag as Dev.  Note that the operation is successful.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/50.jpg"/>
<p>•Navigate to the az1000101b-vm1 virtual machine blade.</p> 
<p>•From the az1000101b-vm1 virtual machine blade, navigate to the az1000101b-vm1 - Tags blade and try to set the value of the environment tag to dev. Note that this time the operation fails. The resulting error message indicates that the resource refused tag assignment, with resource lock being the likely reason.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/51.jpg"/>
<p>•Then navigate to its Access keys blade. Note the resulting error message stating that you cannot access the data plane because a read lock on the resource or its parent.</p>    
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/52.jpg"/>
<p>•Navigate to the az1000101b-RG resource group blade and navigate to Tag blade.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/53.jpg"/>
<p>•From the Tags blade, attempt assigning the environment tag with the value lab to the resource group and note the error message.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-1-01/54.jpg"/>
