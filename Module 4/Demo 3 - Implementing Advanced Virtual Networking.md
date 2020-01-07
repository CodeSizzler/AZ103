<h1>Implementing Advanced Virtual Networking</h1>

<h2>Introduction</h2>
<p>This article helps you to learn about implementing advanced Virtual Network using Azure portal.</p>

<h2>Pre-requisite</h2>
<p>To perform this you must have valid Azure subscription and some basic knowledge on Azure Virtual Network, Load Balancer, Virtual Machine.</p>

<h2>Demo</h2>
<p>Log-in to Azure portal with your Azure account using www.portal.azure.com. In Azure portal click on create a new resource and search for Template Deployment. Use the search list initiate a custom deployment.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/001.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/02.JPG"/>
<p>In the custom deployment panel click on Build your own template in the editor.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/03.jpg"/>
<p>In the edit template panel click on load file and upload the az-10103_01_azuredeploy.json file.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/04.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/05.jpg"/>
<p>After uploading the template file click on save.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/06.jpg"/>
<p>When you click on save it will navigate you to custom deployment panel. In the custom deployment panel click on Edit parameter panel and load the az-10103_01_1_azuredeploy.parameters.json parameter file.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/07.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/08.JPG"/>
<p>After uploading the template file click on save.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/09.jpg"/>
<p>In the custom deployment panel initiate a custom deployment with following settings:</p>
	<p>•Subscription: Select a valid subscription</p>
	<p>•Resource group: Create a new resource group DemoRG</p>
	<p>•Location: Select a valid subscription</p>
	<p>•Admin Username: For your choice</p>
	<p>•Admin Password: For your choice</p>
	<p>•Vm Name Prefix: Default</p>
	<p>•Vm Size: Standard_DS1_v2</p>
	<p>•Virtual Network Name: Demo-vnet</p>
	<p>•Virtual Network Resource Group: DemoRG</p>
	<p>•Subnet0Name: subnet0</p>
	<p>•Availability Set Name: Demovm-avset</p>
	<p>•Modules Url: Default</p>
	<p>•Configuration Function: Default</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/10.jpg"/>
<p>Don’t wait for the deployment completes. Click on create a new resource and search for Template Deployment.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/11.jpg"/>
<p>Use the search list to initiate a custom deployment.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/12.jpg"/>
<p>In the custom deployment panel click on Build your own template in the editor.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/13.jpg"/>
<p>In the edit template panel click on load and upload the az-10103_01_azuredeploy.json template file and click on save.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/14.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/15.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/16.jpg"/>
<p>When you click on save it navigate you to the custom deployment panel. In the custom deployment panel click on edit parameter icon.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/17.jpg"/>
<p>In the edit parameter panel upload the az-101-03_01_2_azuredeploy.parameters.json parameter file and save the file.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/18.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/19.JPG"/>
<p>When you click on save it will navigate you to custom deployment panel. In the custom deployment panel initiate a custom deployment with following settings.</p>
	<p>•Subscription: Select a valid subscription</p> 
	<p>•Resource group: create a new resource group DemoRG2</p> 
	<p>•Location: Select a valid location</p> 
	<p>•Admin Username: For your choice</p> 
	<p>•Admin Password: For your choice</p> 
	<p>•Vm Name Prefix: Demo-vm2</p> 
	<p>•Nic Name Prefix: Demovm2-nic</p> 
	<p>•Vm Size: Standard_DS1_v2</p>  
	<p>•Virtual Network Name: Demovm2-vnet</p> 
	<p>•Virtual Network Resource Group: DemoRG2</p> 
	<p>•Subnet0Name: subnet0</p> 
	<p>•Availability Set Name: Demovm-avset</p> 
	<p>•Modules Url: Default</p> 
	<p>•Configuration Function: Default</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/20.jpg"/>
<p>In Azure portal click on create a new resource and search for Load Balancer.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/21.jpg"/>
<p>Use the search list to deploy a Load Balancer.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/22.jpg"/>
<p>Configure the following the following settings and click on Review+Create.
	<p>•Subscription: Select a valid subscription</p> 
	<p>•Resource Group: Use the on which you have created during custom deployment DemoRG</p> 
	<p>•Name: CodesizzlerLB</p> 
	<p>•Region: Select a valid location</p> 
	<p>•Type: Public</p> 
	<p>•SKU: Basic</p>
	<p>•Public IP address: Create new</p> 
	<p>•Public IP address name: CodesizzlerLB-pip</p> 
	<p>•Assignment: Dynamic</p> 
	<p>•Add a public IPv6 address: No</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/23.jpg"/>
<p>Once your validation gets paused click on create.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/24.jpg"/>
<p>Wait until the deployment completes. After the deployment completes navigate to the created Load Balancer.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/25.jpg"/>
<p>In the load balance panel display its backend pools.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/26.jpg"/>
<p>In the backend pool panel add a backend pool with following setting.</p>
   	<p>•Name: CodesizlerLB-Backend</p> 
	<p>•IP version: IPv4</p> 
	<p>•Associated to: Availability set</p> 
	<p>•Availability set: Demovm-avset</p> 
	<p>•Virtual machine: DemoVM1</p> 
	<p>•Network IP configuration: Default</p> 
	<p>•Virtual machine: DemoVM2</p> 
	<p>•Network IP configuration: Default</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/27.jpg"/>
<p>After adding the backend pool navigate to CodesizzlerLB-Health Prob and click on Add.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/28.jpg"/>
	<p>Add a health prob with following configurations.</p>
	<p>•Name: CodesizzleLB-Healthprob</p> 
	<p>•Protocol: TCP</p> 
	<p>•Port: 80</p> 
	<p>•Interval: 5 seconds</p> 
	<p>•Unhealthy threshold: 2 Consecutive</p>  
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/29.jpg"/>
<p>After adding the health prob navigate to Load Balancing Rules and add a load balancing rule with following configurations.</p>
	<p>•Name: CodesizzlerLB-Rule 
	<p>•IP Version: IPv4</p> 
	<p>•Frontend IP address: LoadBalancerFrontEnd</p> 
	<p>•Protocol: TCP</p> 
	<p>•Port: 80</p> 
	<p>•Backend port: 80</p> 
	<p>•Backend pool: CodesizzlerLB-Backend</p> 
	<p>•Health probe: CodesizzlerLB-Healthprob</p> 
	<p>•Session persistence: None</p> 
	<p>•Idle timeout: 4</p> 
	<p>•Floating IP: Disabled</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/30.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/31.JPG"/>
<p>In Azure portal click on create a new resource and search for Load Balancer.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/32.jpg"/>
<p>Create a new Load Balancer for the second region.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/33.jpg"/>
	<p>•Name: CodesizzlerLB2</p> 
	<p>•Type: Public</p> 
	<p>•SKU: Basic</p>
	<p>•Public IP address: create a new public IP address named az1010302w-lb-pip</p> 
	<p>•Assignment: Dynamic</p> 
	<p>•Subscription: Select a valid subscription</p> 
	<p>•Resource group: DemoRG2</p> 
	<p>•Location: Select a valid location</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/34.jpg"/>
<p>Click on create when your validation gets paused.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/35.jpg"/>
<p>Navigate to the newly create Load Balancer.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/36.jpg"/>
<p>In the Load Balancer panel navigate to backend pool and click on Add.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/37.jpg"/>
<p>Create a backend pool with following configurations.</p>
	<p>•Name: CodesizzlerLB2--Backend</p> 
	<p>•IP version: IPv4</p> 
	<p>•Associated to: Availability set</p> 
	<p>•Availability set: Demovm-avset</p>
	<p>•Virtual machine: Demo-vm20</p> 
	<p>•Network IP configuration: Default</p> 
	<p>•Virtual machine: Demo-vm21</p> 
	<p>•Network IP configuration: Default</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/38.jpg"/>
<p>After adding the backend pool navigate to Health Prob and create a new health prob with following settings.</p>
	<p>•Name: CodesizzlerLB2-Healthprob</p> 
	<p>•Protocol: TCP</p> 
	<p>•Port: 80</p> 
	<p>•Interval: 5 seconds</p> 
	<p>•Unhealthy threshold: 2 consecutive failures</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/39.jpg"/>
<p>After creating the health prob navigate to Load Balancing rule and create a load balancing rule with following settings.</p>
	<p>•Name: CodesizzlerLB2Rule</p> 
	<p>•IP Version: IPv4</p> 
	<p>•Frontend IP address: LoadBalancerFrontEnd</p> 
	<p>•Protocol: TCP</p> 
	<p>•Port: 80</p> 
	<p>•Backend port: 80</p> 
	<p>•Backend pool: CodesizzlerLbBackendpool</p> 
	<p>•Health probe: CodesizzlerLB2-Healthprob</p> 
	<p>•Session persistence: None</p> 
	<p>•Idle timeout (minutes): 4</p> 
	<p>•Floating IP: Disabled</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/40.jpg"/>
<p>Navigate to CodesizzlerLB and display its inbound NAT Rule.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/41.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/42.jpg"/>
<p>Add an inbound NAT Rule with following settings. 
	<p>•Name: CodesizzlerVmRDP 
	<p>•Frontend IP address: LoadBalancedFrontEnd 
	<p>•IP Version: IPv4</p>  
	<p>•Protocol: TCP</p>  
	<p>•Port: 33890</p>  
	<p>•Target virtual machine: Demo-vm0</p>  
	<p>•Network IP configuration: Default</p>  
	<p>•Port mapping: Custom</p>  
	<p>•Floating IP: Disabled</p>  
	<p>•Target port: 3389</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/43.jpg"/>
<p>Create another inbound NAT Rule with following settings.</p>
	<p>•Name: Codesizzlervm1RDP</p>  
	<p>•Frontend IP address: LoadBalancedFrontEnd</p>  
	<p>•IP Version: IPv4</p>  
	<p>•Service: Custom</p>  
	<p>•Protocol: TCP</p>  
	<p>•Port: 33891</p>  
	<p>•Target virtual machine: Demo-vm1</p>  
	<p>•Network IP configuration: Default</p>  
	<p>•Port mapping: Custom</p>  
	<p>•Floating IP: Disabled</p> 
	<p>•Target port: 3389</p>  
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/44.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/45.jpg"/>
<p>Navigate to CodesizzlerLB2 and display its inbound NAT Rule.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/46.jpg"/>
<p>Click on add to add an inbound NAT Rule.C</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/47.jpg"/>
<p>Add an inbound NAT Rule with following configurations.</p>
	<p>•Name: CodesizzlerVmRDP</p> 
	<p>•Frontend IP address: LoadBalancedFrontEnd</p> 
	<p>•IP Version: IPv4</p> 
	<p>•Service: Custom</p> 
	<p>•Protocol: TCP</p> 
	<p>•Port: 33890</p> 
	<p>•Target virtual machine:</p>  
	<p>•Network IP configuration: Default</p> 
	<p>•Port mapping: Custom</p> 
	<p>•Floating IP: Disabled</p> 
	<p>•Target port: 3389</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/48.jpg"/>
<p>Add another rule with following settings.</p>
	<p>•Name: Codesizzlervm1</p>  
	<p>•Frontend IP address: LoadBalancedFrontEnd</p>  
	<p>•IP Version: IPv4</p>  
	<p>•Service: Custom</p>  
	<p>•Protocol: TCP</p>  
	<p>•Port: 33891</p>  
	<p>•Target virtual machine:</p>   
	<p>•Network IP configuration: Default</p>  
	<p>•Port mapping: Custom</p>  
	<p>•Floating IP: Disabled</p>  
	<p>•Target port: 3389</p>  
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/49.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/50.jpg"/>
<p>In Azure portal navigate to CodesizzlerLB.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/51.jpg"/>
<p>In the overview panel of CodesizzlerLB note the public IP address of the storage account.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/52.jpg"/>
<p>Open a browser and browse with the public IP address of the storage account.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/53.jpg"/>
<p>Note that it shows the IIS home page.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/54.jpg"/>
<p>Start a PowerShell session as administrator and run the following command to connect with your Virtual Machine. Replace the IPaddress string with the IP address that you have identified in the previous step. that you have identified in the previous step.</p>
	<p>mstsc /v:<IPaddress>:33890 	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/55.jpg"/>
<p>When it prompts connect with the Virtual Machine with the credentials that you have provided wile deploying the Virtual Machine.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/56.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/57.jpg"/>
<p>After entering the Virtual Machine open the command prompt and run the following command to verify that you are connected to the Demo-vm0.</p>
	<p>hostname 	</p>
<p>Terminate the Virtual Machine session and navigate to Azure portal. In Azure portal navigate to CodesizzlerLB2 and copy the public IP address.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/58.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/59.jpg"/>
<p>Open a browser and browse with the IP address. Note that it shows the IIS home page.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/60.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/61.jpg"/>
<p>Start a PowerShell session as administrator and run the following command to connect with your Virtual Machine. Replace the IPaddress string with the IP address that you have identified in the previous step.</p>
	<p>mstsc /v:<IPaddress>:33890 	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/62.jpg"/>
<p>When it prompts log-in to the Virtual Machine by providing the credentials which you have provided while deploying the Virtual Machine.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/63.jpg"/>
<p>Click on yes to connect with Virtual Machine.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/64.jpg"/>
<p>After entering the Virtual Machine open the command prompt and run the following command to verify that you are connected to the Demo-vm2.</p>
	<p>hostname 	</p>
<p>In Azure portal navigate to CodesizzlerLB-pip.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/65.jpg"/>
<p>In the CodesizzlerLB-pip display the configuration blade.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/66.jpg"/>
<p>In the configuration panel give a DNS name and click on save.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/67.jpg"/>
<p>Navigate to COdesizzlerLB2-pip.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/68.jpg"/>
<p>Display the configuration panel of CodesizzlerLB2-pip. In the configuration panel give a DNS name and click on save.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/69.jpg"/>
<p>In Azure portal click on create a new resource and search for Traffic Manager.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/70.jpg"/>
<p>Use the search list to create a Traffic Manager. Click on create a Traffic Manager.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/71.jpg"/>
<p>Create a Traffic Manager with following configurations.</p>
	<p>•Name: cstmp</p> 
	<p>•Routing method: Weighted</p> 
	<p>•Subscription: Select a valid subscription</p> 
	<p>•Resource group: create a new resource group TrafficManagerRg</p> 
	<p>•Location: Select a valid location</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/72.jpg"/>
<p>Wait until the deployment completes. After deployment completes navigate to the deployed Traffic Manager.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/73.jpg"/>
<p>Display the configuration panel of the Traffic Manager and review the settings.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/74.jpg"/>
<p>Navigate to the Endpoint panel and click on Add to add a Traffic Manager endpoint.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/75.jpg"/>
<p>Add an endpoint with following configurations.</p>
	<p>•Type: Azure endpoint</p> 
	<p>•Name: cstmpendpoint</p> 
	<p>•Target resource type: Public IP address</p> 
	<p>•Target resource: CodesizzlerLB-pip</p> 
	<p>•Weight: 100</p> 
	<p>•Custom Header settings: leave blank</p> 
	<p>•Add as disabled: leave blank</p> 
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/76.jpg"/>
<p>Add another endpoint with following configuration.</p>
	<p>•Type: Azure endpoint</p>  
	<p>•Name: cstmpendpoint2</p>  
	<p>•Target resource type: Public IP address</p>  
	<p>•Target resource: CodesizzlerLB2-pip</p>  
	<p>•Weight: 100</p>  
	<p>•Custom Header settings: leave blank</p>  
	<p>•Add as disabled: leave blank</p>  
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/77.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/78.jpg"/>
<p>After adding the endpoints wait until the monitor status turns to Online.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/79.jpg"/>
<p>Navigate to the overview panel of Traffic Manager and note the DNS name.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-003/80.jpg"/>
<p>Start a PowerShell as administrator and run the following command by replacing the dns name string with the one which you have identified in the previous step.</p>
	<p>nslookup <TM_DNS_name> 	</p>
<p>Note that the output matches to your Traffic Manager endpoint. Wait for few minutes and run the same command and note that the output matches the another Traffic Manager endpoint.</p>
 



	 




