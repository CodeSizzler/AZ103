<h1>Configuring compute and storage resources of Azure Virtual Machine</h1>

<h2>Introduction</h2>
<p>In this article we are going to discuss about configuring compute and storage resources of a Virtual Machine.</p>

<h2>Pre-requisites</h2>
<p>To perform this demo you must have valid Azure subscription and some basic knowledge on Azure Virtual Machine and VMSS.</p>

<h2>Demo</h2>
<p>Log in with your Azure account in Azure Portal using www.portal.azure.com. In Azure Portal click on create a new resource and search for Template Deployment.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/01.jpg"/>
<p>In custom template deployment select Build own template editor.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/02.jpg"/>
<p>In that load the template file az-100-03b_01_azuredeploy.json and save it. It will navigate you to the custom deployment panel.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/03.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/04.jpg"/>
<p>After navigating to the custom deployment panel click on Edit Parameter and load the file az-100-03b_01_azuredeploy.parameters.json and save it.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/05.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/06.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/07.jpg"/>
<p>After saving the parameter initiate the template deployment with the required configurations.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/08.jpg"/>
<h2>Deploying an Azure Virtual Machine Scale Set using ARM Template</he>
<p>In Azure Portal click on create a new resource and search for Template Deployment.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/09.jpg"/>
<p>In custom template deployment panel select Build own template editor.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/10.jpg"/>
<p>In the edit template panel load the template file az-100-03b_02_azuredeploy.json and save it. It will navigate you to Custom Deployment panel.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/11.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/12.jpg"/>
<p>n the custom deployment panel click on Edit Parameter and load the template file az-100-03b_02_azuredeploy.parameters.json and save it.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/13.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/14.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/15.jpg"/>
<p>After saving the parameter initiate the template deployment with the required configurations.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/16.jpg"/>
<h2>Configuring compute and storage resources of Virtual Machines</h2>
<p>In Azure Portal navigate to DemoRG1 resource group and display DemoVM panel. From there navigate to DemoVM-Size panel.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/17.jpg"/>
<p>Increase the Virtual Machine size to DS2_v2 Standard and click on resize.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/18.jpg"/>
<p>Then navigate to DemoRG1 panel and display the deployment blade.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/19.jpg"/>
<p>In the deployment panel display the overview page of Microsoft.Template. It shows the recent successful deployment.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/20.jpg"/>
<p>Click on redeploy option. It will navigate you to custom deployment panel.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/21.jpg"/>
<p>In the custom deployment panel navigate to edit parameter panel and review the parameters. Save the parameter and return to custom deployment panel. Restore the settings that you provided before and initiate the deployment.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/22.jpg"/>
<p>Then navigate to DemoVM panel and display the disk blade.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/23.jpg"/>
<p>Create a managed disk with the required settings settings.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/24.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/25.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/29.jpg"/>
<p>After creating the first managed disk create an another managed disk.</p>
<p>Then navigate to DemoVM panel and connect to Virtual Machine using RDP protocol with the credentials provided while creating the Virtual Machine.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/26.jpg"/>
<p>After connecting to the Virtual Machine navigate to server manager and navigate File and Storage Service panel.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/27.jpg"/>
<p>Use New Storage Pool vizard to create a new storage pool and New Virtual Disk vizard to create a new Virtual Disk. Create a new volume with required settings.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/28.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/30.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-02/31.jpg"/>
