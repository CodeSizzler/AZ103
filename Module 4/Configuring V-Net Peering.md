<h1>Configuring VNet peering and service chaining</h1>
<p>This lab is going to deal with Azure Virtual Network Peering. VNET peering is a concept of combining two different networks from same or different regions of Azure to become a single network for having an authenticated and secured access for resources. When we use VNET peering, the concept of creating VPN Gateways to connect different Azure Networks is not required since VNET Peering does the same thing for you in a cheaper and easier way.</p>

<h2>Demo Scenario:</h2>
This lab is about deployment of two Virtual Networks up on which a Virtual Machine will be deployed on one VNET and two virtual machines will be deployed up on another VNET in South India Datacenter. The deployment of resources will be carried out using ARM Templates. After the deployment is done, the VNETs will be peered for accessing the Virtual Machine that is of a different Virtual Network. To make this happen, we will also be deploying Routing Tables in Azure.</h2>

<h2>Prerequisites</h2>
<p>1.An Azure Subscription.</p>
<p>2.Knowledge on ARM Templates.</p>
<p>3.Basic Understanding of Networking.</p>
<p>4.ARM Templates – Download the scripts required for doing the following demo from the below given link.</p>

<h2>ARM Templates:</h2>
<p>Before starting this demo download the template files from - http://bit.ly/VnetPeeringCS.</p>

<h2>Steps:</h2>
<h2>1.Deploying two VMs on one VNET using ARM Templates</h2>
<p>Go to + Create a resource and search for Template deployment in the search box. You will get the Template deployment blade. In there click on Create button.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/01.jpg"/>
<p>In there, click on Build your own template in the editor option.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/02.jpg"/>
<p>Now, click on Load file option in the top.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/03.jpg"/>
<p>	Then, select the file named 1 Creating two VMs up on Single VNET from the set of files that you downloaded in the beginning and click Open.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/04.jpg"/>
<p>Once you click on Open, the JSON script in that template will get uploaded into the portal. Then, click on Save button.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/05.jpg"/>
<p>Now, click on Edit parameters option to edit the input parameters for deployment.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/06.jpg"/>
<p>Again, click on Load file option and to upload parameters file.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/07.jpg"/>
<p>This time select 2 Parameters file from the downloaded files and click on Open.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/08.jpg"/>
<p>After the script gets loaded, click on Save button.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/09.jpg"/>
<p>In the deployment blade, create a new resource group like shown below. Make sure to agree the Terms and Conditions in the bottom and click on Purchase.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/10.jpg"/>

<h2>Deploying a VM on a VNET using ARM Templates</h2>
<p>Go to + Create a resource and search for Template deployment in the search box. You will get the Template deployment blade. Click on Create button.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/11.jpg"/>
<p>In there, click on Build your own template in the editor option.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/12.jpg"/>
<p>Now, click on Load file option in the top.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/13.jpg"/>
<p>Then, select the file named 3 Creating VM up on a Single VNET from the set of files that you downloaded in the beginning and click Open.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/14.jpg"/>
<p>Once you click on Open, the JSON script in that template will get uploaded into the portal. Then, click on Save button.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/15.jpg"/>
<p>Now, click on Edit parameters option to edit the input parameters for deployment.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/16.jpg"/>
<p>Again, click on Load file option and to upload parameters file.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/17.jpg"/>
<p>This time select 2 Parameters file from the downloaded files and click on Open.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/18.jpg"/>
<p>After the script gets loaded, click on Save button.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/19.jpg"/>
<p>In the deployment blade, create a new resource group like shown below. Make sure to agree the Terms and Conditions in the bottom and click on Purchase.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/20.jpg"/>

<h2>3.Configuring VNET Peering</h2>
<p>Once after the two VNETs are deployed in the previous two demos, you can start to peer the VENTs.Open the resource group that you created for first two VMs and open the VNET named az1000401-vnet1.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/21.jpg"/>
<p>Navigate to the Peerings menu blade of that VNET and click on + Add button.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/22.jpg"/>
<p>Give a valid name and choose the Peer details as shown below. For Virtual network choose the VNET named az1000402-vnet2 which you created in demo 2. Allow the Virtual network access and disable rest of the settings and click Ok.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/23.jpg"/>
<p>You can note that peering got initialized in the VNET.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/24.jpg"/>
<p>You have to repeat the same process in VM2. Go the resource group you created in demo 2 and open the VNET named az-1000402-vnet2.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/25.jpg"/>
<p>Navigate to the Peerings blade of the VNET and click on + Add button to configure peering with another VNET.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/26.jpg"/>
<p>Give a valid name and choose the Peer details as shown below. For Virtual network choose the VNET named az1000401-vnet1 which you created in demo 2. Allow the Virtual network access and disable rest of the settings and click Ok.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/27.jpg"/>
<p>You can note that peering got initialized in the VNET.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/28.jpg"/>

<h2>4.Configuring IP Forwarding and Creating Routing Table</h2>
<p>Go to virtual machines menu and find the VM named az1000401-vm2 for enabling IP Forwarding.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/29.jpg"/>
<p>Go to the Networking blade and click on the NIC named az1000401-nic2 as shown below.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/30.jpg"/>
<p>Go to the IP configurations menu blade of the NIC and click on Enabled option for IP forwarding and click on Save button.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/31.jpg"/>
<p>Now,let us create a routing table for routing the traffic. To do so, go to + Create a resource and search for Routing table and click on Create.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/32.jpg"/>
<p>Give a name for the routing table and choose a subscription and resource group. Make sure to choose the location as South India, Disable Virtual network gateway propagation and click on Create.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/33.jpg"/>
<p>Open the routing table after it gets deployed and navigate to its Routes blade and click on + Add button.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/34.jpg"/>
<p>Give a name to the route and give its address prefix as 10.104.0.0/16 which is the address range of VNET az1000401-vnet1. For Next hop type select Virtual appliance and to the Next hop address set the IP address as 10.104.1.4 which is the IP address of the NIC of az1000401vm2 and click on Ok.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/35.jpg"/>
<p>In a while, you will be able to find the Newly added route.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/36.jpg"/>
<p>Now, go to Subnets blade of the route table and click on + Associate option.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/37.jpg"/>
<p>In there select the Virtual Network az1000402-vnet2 and the subnet Subnet0 and click on Ok.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/38.jpg"/>
<p>Now, we have associated the routing table along with route to the VNET.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/39.jpg"/>

<h2>5.Configuring Routing in Azure VM az1000401-vm2</h2>
<p>Navigate to VMs menu and open the VM az1000401-vm2 to make RDP connection with it.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/40.jpg"/>
<p>In the overview page of the VM, click on Connect option and click on Download RDP file button and open it.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/41.jpg"/>
<p>In the RDP connection dialog box click on Connect button.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/42.jpg"/>
<p>Enter the User name and password of the VM as shown below if you used the ARM Templates as it is without modifying username and password in it. If modified, enter your own username and password and click on Ok.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/43.jpg"/>
<p>Click on Yes when prompted with certificate like this.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/44.jpg"/>
<p>After logging to the VM, wait for a while so that the Local Server Manager will get opened by itself. In there, click on Add roles and features to add Remote Access role.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/45.jpg"/>
<p>In the following window hit Next without making any changes.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/46.jpg"/>
<p>Again, click on Next.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/47.jpg"/>
<p>Again, click on Next for one more time.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/48.jpg"/>
<p>Now enable the Remote Access checkbox in the roles and click on Next.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/49.jpg"/>
<p>Once again click on Next.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/50.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/51.jpg"/>
<p>In the Role Services click on Routing checkbox.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/52.jpg"/>
<p>When prompted with features, click on Add Features.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/53.jpg"/>
<p>Click on Next again and follow the rest of the steps as shown below.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/54.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/55.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/56.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/57.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/58.jpg"/>
<p>After your installation gets succeeded, click on the warning that gets displayed in top and click on Open the Getting Started Wizard.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/59.jpg"/>
<p>After clicking in there, you can find the warning sign gone.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/60.jpg"/>
<p>Now,let us configure and enable routing and remote access. To do so, go to Tools and click on Routing and Remote Access option.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/61.jpg"/>
<p>In the Routing and Remote Access console right click on server that is displayed and choose Configure and Enable Routing and Remote Access.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/62.jpg"/>
<p>In the setup wizard, click on Next.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/63.jpg"/>
<p>Choose Custom configuration and click on Next.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/64.jpg"/>
<p>Now select LAN routing and click on Next button.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/65.jpg"/>
<p>Finally click on Finish.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/66.jpg"/>
<p>After hitting on Finish, you will get a Routing and Remote Access dialog box. In there click on Start service button to start the service.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/67.jpg"/>
<p>You must get a message displayed as shown below. If you don’t get, check the previous steps once again.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/68.jpg"/>
<p>Now, let us go to the Local Server Manager and open Firewall settings. To do so, go to Tools and choose Windows Firewall with Advanced Security.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/69.jpg"/>
<p>In the firewall window, go to Inbound Rules and enable File and Printer Sharing (Echo Request – ICMPV4-In) rule by clicking on Enable Rule option.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/70.jpg"/>

<h2>6.Validating Service Chaining</h2>
<p>Navigate to the VM menu once again and make RDP access to the VM az1000401-vm1 and open the local server manager and repeat same steps that you did earlier for enabling the Firewall rule. To do so, go to Tools and choose Windows Firewall with Advanced Security.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/71.jpg"/>
<p>In the firewall window, go to Inbound Rules and enable File and Printer Sharing (Echo Request – ICMPV4-In) rule by clicking on Enable Rule option.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/72.jpg"/>

<h2>7.Testing the Service Chaining between Peered Networks</h2>
<p>We have all set with the VNET Peering and configuration of VMs to allow connections via routes. Let us test the Peering now by making RDP to the VM az1000402-vm3 and open PowerShell and run the below given command. In the command, the IP address 10.104.0.4 is the IP address of the NIC of az1000401-vm1. On a successful execution of the command it is clear that we have routed the request between two networks.</p>
	<p>Test-NetConnection -ComputerName 10.104.0.4 -TraceRoute		</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-001/73.jpg"/>
<p>Here we have implemented the concept of VNET Peering and Service Chaining in Azure for routing the user traffic between two different networks in Azure.</p>

