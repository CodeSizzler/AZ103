<h1>Deploying and Managing Azure Virtual Machines</h1>

<h2>Introduction</h2>
<p>In this article we are going to discuss about Managing and Deploying Virtual Machines using ARM Templates, PowerShell in Azure Portal. Also learn to analyse the Virtual machine and to deploy a Linux Virtual Machine over the existing server.</p>

<h2>Pre-requisites</h2>
<p>To perform this demo you must have valid Azure subscription and some basic knowledge on Azure Virtual Machine, Power Shell, Putty.ex, ARM Templates.</p>

<h2>Demo</h2>

<h2>Deploying an Azure VM using Windows Server 2016 Datacentre into an availability set using Azure Portal</h2>

<p>Log in with your Azure account in Azure Portal using www.portal.azure.com. Click on Create a new resource and select Windows server 2016 Datacentre.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/01.jpg"/>
<p>In create a Virtual Machine panel deploy a virtual machine with required settings.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/02.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/03.jpg"/>
<p>Once your validation gets passed click on create.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/04.jpg"/>

<h2>Deploying an Azure Virtual Machine running Windows Server 2016 Datacenter into the existing availability set using Azure PowerShell</h2>
<p>In Azure Portal start a PowerShell session.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/05.jpg"/>
<p>After opening the PowerShell run the commands to deploy an Azure Virtual Machine into the existing availability set. Once the command run gets complet, then your Virtual Machine will get created.</p>
<p>You can download the command script here - http://bit.ly/103vmscript</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/06.jpg"/>

<h2>Deploying two Azure VMs running Linux into an availability set by using Azure Resource Manager template</he>
<p>In Azure Portal click on create a new resource and search for Template Deployment.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/07.jpg"/>
<p>In custom template deployment panel select Build own template editor.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/08.jpg"/>
<p>In the edit template panel load the lab file az-100-03_azuredeploy.json and save the parameter.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/09.jpg"/>
<p>After loading the template file, it will automatically navigate to custom deployment panel. Then click on Edit Parameter and upload the lab file, 03_azuredeploy.parameters.json and save the parameter and return to the custom deployment panel.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/10.jpg"/>
<p>In the custom deployment panel, initiate a template deployment with required settings. Then click on purchase.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/11.jpg"/>

<h2>Configuring networking settings of Azure VM running in Windows and Linux operating systems</h2>
<p>In Azure Portal navigate to DemoVM panel and display the IP-Configuration panel. Change the Ip address from dynamic to static and set it to 10.103.0.100 then save it.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/12.jpg"/>
<p>Then navigate to the networking panel. Review the inbound port rule of network security rule and add a inbound security rule to the existing group.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/13.jpg"/>
<p>Add an inbound rule with the required settings.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/14.jpg"/>
<p>After adding the inbound port rule connect to the Virtual Machine.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/15.jpg"/>
<p>After entering the VM open the command prompt and run the following command.</p>
	<p>nslookup DemoVm30</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/16.jpg"/>
<p>Take a note on out put and close the command prompt. Then open the Server Manager and turn off the IE Enhanced Security Configuration.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/17.jpg"/>
<p>Download putty.ex using the link https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/18.jpg"/>
<p>Use putty.ex to connect to the VM using it’s private IP and SSH. After the authentication page prompted register with the following credentials. When it prompts provide the valid credentials.</p> 
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/19.jpg"/>
<p>After registering close the VM and return to local machine.</p>

<h2>Deploying and configuring Azure VM scale sets</h2>
<p>In Azure Portal start a PowerShell session and run the following command. Note that the command returns true. Then close the PowerShell session.</p>
	<p>Test-AzDnsAvailability -DomainNameLabel codesizzler -Location 'CentralUS'</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/20.jpg"/>
<p>In Azure Portal click on create a new resource and search for Virtual Machine scale set.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/21.jpg"/>
<p>In that create a VMSS with the required settings.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/22.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/23.jpg"/>
<p>In Azure Portal navigate to DMVMScaleSet to display it Extension panel and add a PowerShell desired state extension with following settings.</p>
	<p>o	Configuration Modules or Script: Upload the file az-100- 03_install_iis_vmss.zip</p>
	<p>o	Module-qualified Name of Configuration: az-100- 03_install_iis_vmss.ps1\IISInstall</p>
	<p>o	Configuration Arguments: Leave it empty</p>
	<p>o	Configuration Data PSD1 File: Leave it empty</p>
	<p>o	WMF Version: latest</p>
	<p>o	Data Collection: Disable</p>
	<p>o	Version: 2.76</p>
	<p>o	Auto Upgrade Minor Version: Yes</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/24.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/25.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/26.jpg"/>
<p>Navigate to DMVMScaleSet and display the Instances panel. And Initiate upgrade. After the process completion move to the overview panel and copy the PublicIP. Navigate to the browser and search with the PublicIP it will display the IIS home page.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/27.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/28.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-03/29.jpg"/>
