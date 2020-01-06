<h1>Implementing Azure Site Recovery between Azure regions</h1>
<h2>Introduction</h2>
<p>In this article we are going to discuss about replicating Azure Virtual Machines from one region to another region. Also we will perform failover testing to check out the site recovery.</p>

<h2>Prerequisites</h2>
<p>To perform this demo user must have a valid Azure subscription and some basic knowledge on:</p>
	<p>•Template deployment</p>
	<p>•Azure Site Recovery</p>

<h2>Template files</h2>
<p>Download the templates and parameter files for Az-101 from - http://bit.ly/ASRtemplatefiles</p>

<h2>Demo</h2>
<p>Log-in with your account in Azure Portal using www.portal.azure.com. In Azure portal click on create a new resource and search for Template Deployment.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-004/01.jpg"/>
<p>In the custom deployment panel select Build your own template in the editor and upload the template file az-101-01_azuredeploy.json.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-004/02.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-004/03.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-004/04.jpg"/>
<p>After uploading the template file save it and return to custom deployment panel.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-004/05.jpg"/>
<p>In the custom deployment panel click on edit parameter and upload the parameter file az-101-01_azuredeploy.parameters.json.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-004/06.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-004/07.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-004/08.jpg"/>
<p>After uploading the parameter file save it and return the custom deployment panel.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-004/09.jpg"/>
<p>In the custom deployment panel initiate a custom deployment with following settings:</p>
	<p>•Subscription: Select a valid subscription</p>
	<p>•Resource group: Create a new resource group DemoRG1</p>
	<p>•Location: Select a valid location</p>
	<p>•Location: Select a valid location</p>
	<p>•Admin Username: DemoUser</p>
	<p>•Admin Password: Codesizzler@</p>
	<p>•Image Publisher: MicrosoftWindowsServer</p>
	<p>•Image Offer: WindowsServer</p>
	<p>•Image SKU: 2016-Datacenter-Server-Core-smalldisk</p>
	<p>•Virtual Machine Size: Standard_DS1_v2</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-004/10.jpg"/>
<p>After initiating the deployment click on create a new resource and search for Backup and Site Recovery (OMS).</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-004/11.jpg"/>
<p>In the Recover Site Vault create a site recovery vault with following settings and click on create.</p>
	<p>•Name: CodesizzlerRecovery</p>
	<p>•Subscription: Select a valid subscription</p>
	<p>•Resource group: Create a new resource group RecoverRG</p>
	<p>•Location: Select the location which is different from the location of Virtual Machine</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-004/12.jpg"/>
<p>In Azure portal navigate to the newly created CodesizzlerRecovery blade and click on +Replication.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-004/13.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-004/14.jpg"/>
<p>Configure the following replication settings:</p>
	<p>•Source: Azure</p>
	<p>•Source location: Same Azure region of the Virtual Machine</p>
	<p>•Azure virtual machine deployment model: Resource Manager</p>
	<p>•Source subscription: Select a valid subscription</p>
	<p>•Source resource group: Resource group of DemoVM</p>
	<p>•Virtual machines: DemoVM</p>
	<p>•Target location: Select the valid location that is different from the VM location</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-004/15.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-004/16.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-004/17.JPG"/>
<p>After configuring all the settings click on Enable Replication. Wait until the replication process completes.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-004/18.jpg"/>
<p>Navigate to Codesizzler-Replicated items and review the Health and status, Failover readiness, Latest recovery points, and Infrastructure view.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-004/19.jpg"/>
<p>Navigate to the replicated DemoVM panel and note the value of RPO.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-004/20.jpg"/>
<p>Start a failover test for Demo-vnet-asr.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-004/21.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-004/22.jpg"/>
