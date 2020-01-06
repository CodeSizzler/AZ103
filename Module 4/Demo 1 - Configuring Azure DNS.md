<h1>Configuring Azure DNS</h1>
<h2>Introduction</h2>
<p>In this article you are going to learn about how to configure the Azure DNS for a public domain.</p>

<h2>Pre-requisite</h2>
<p>To perform this demo you must have valid Azure subscription and some basic knowledge on Azure DNS.</p>

<h2>Configuring Azure DNS for public domains</h2>

<h2>Steps:</h2>
<h2>1.Create a public DNS zone</h2>
<p>Log-in with your Azure account using www.portal.azure.com
<p>Click on create a new resource and search for DNS zone.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-002/01.jpg"/>
<p>In that panel create a new DNS zone with following settings:K</p>
	<p>Name: codesizzler.com</p>
	<p>Subscription: Select a valid subscription</p>
	<p>Resource group: Create a new resource group DNSrg1</p>
	<p>Resource group location: Select a valid location</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-002/02.jpg"/>

<h2>2.Create a DNS record in public DNS zone</h2>
<p>In Azure Portal start a PowerShell session and run the following comments to create a public IP address resource.</p>
	<p>Invoke-RestMethod http://ipinfo.io/json | Select-Object -ExpandProperty IP</p>
	<p>$rg = Get-AzResourceGroup -Name DNSrg</p>
 	<p>New-AzPublicIpAddress -ResourceGroupName $rg.ResourceGroupName -Sku Basic</p>
	<p>AllocationMethod Dynamic -Name DNSrg-pip -Location $rg.Location	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-002/03.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-002/04.jpg"/>
<p>Navigate to DNSrg resource group and display the newly created public DNS zone.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-002/05.jpg"/>
<p>In that panel create a new record set with following settings</p>
	<p>Name: dsnvmpip</p>
	<p>Type: A</p>
	<p>Alias record set: No</p>
	<p>TTL: 1</p>
	<p>TTL unit: Hours</p>
	<p>IP ADDRESS: the one which you have identified earlier in this task</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-002/06.jpg"/>
<p>Also create another record set with following settings</p>
	<p>Name: myazurepip</p>
	<p>Type: A</p>
	<p>Alias record set: Yes</p>
	<p>Alias type: Azure resource</p>
	<p>Choose a subscription: Select a valid subscription</p>
	<p>Azure resource: Create a new resource group DNSrg-pip</p>
	<p>TTL: 1</p>
	<p>TTL unit: Hours</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-002/07.jpg"/>

<h2>3.Validating Azure DNS based on name resolution for public domain</h2>
<p>In the DNS zone panel note the name of first server.</p>
<p>Start a command prompt and run the following command with respective string.</p>
	<p>nslookup mylabvmpip.codesizzler.com ns1-04.azure-dns.com 	</p>
	<p>nslookup myazurepip.codesizzler.com ns1-04.azure-dns.com 	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-002/08.jpg"/>
<p>Note that the IP address matches to the IP address that you identified first.</p>

<h2>Configuring Azure DNS for private domains</h2>

<h2>Steps:</h2>
<h2>1.Provisioning a multi V-Net environment</h2>
<p>In Azure Portal start a PowerShell session and run the following commands to create a multi v-net environment.</p>
	<p>$rg1 = Get-AzResourceGroup -Name 'DNSrg' 	</p>
	<p>$rg2 = New-AzResourceGroup -Name 'DNSrg2' -Location $rg1.Location	</p>
	<p>$subnet1 = New-AzVirtualNetworkSubnetConfig -Name DNSsubnet1 -AddressPrefix '10.104.0.0/24'	</p>
 	<p>$vnet1 = New-AzVirtualNetwork -ResourceGroupName $rg2.ResourceGroupName -Location	</p>
	<p>$rg2.Location -Name DNSeg2Vnet1 -AddressPrefix 10.104.0.0/16 -Subnet $subnet1 	</p>
	<p>$subnet2 = New-AzVirtualNetworkSubnetConfig -Name DNSsubnet2 -AddressPrefix '10.204.0.0/24'	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-002/09.jpg"/>

<h2>2.Create a private DNS zone</h2>
<p>In Azure Portal start a PowerShell session and run the following comments to create a private DNS zone.</p>
	<p>New-AzDnsZone -Name adatum.local -ResourceGroupName $rg2.ResourceGroupName ZoneType</p>
	<p>Private -RegistrationVirtualNetworkId @$DNSeg2Vnet1.Id ResolutionVirtualNetworkId @$DNSrg2Vnet2.Id</p>
	<p>Get-AzDnsZone -ResourceGroupName $rg2.ResourceGroupName</p>

<h2>3.Deploying Azure Virtual Machine into Azure Virtual Network</h2>
<p>In Azure Portal Start a PowerShell and upload the following template files az-100-04b_01_azuredeploy.json, az-100-04b_02_azuredeploy.json, and az-10004_azuredeploy.parameters.json.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-002/10.jpg"/>
<p>After uploading the template files run the following commands to install Virtual Machines in the existing Virtual Networks.</p>
	<p>New-AzResourceGroupDeployment -ResourceGroupName $rg2.ResourceGroupName	</p>
	<p>TemplateFile "$home/az-100-04b_02_azuredeploy.json" -TemplateParameterFile	</p>
	<p>"$home/az-100-04_azuredeploy.parameters.json" -AsJob		</p>
	<p>New-AzDnsRecordSet -ResourceGroupName az1000402b-RG -Name www -RecordType A -	</p>
	<p>ZoneName adatum.local -Ttl 3600 -DnsRecords (New-AzDnsRecordConfig -IPv4Address "10.104.0.4")	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-002/11.jpg"/>
<p>Wait until the deployment completes. To know the status of deployment runt the command Get-Job.</p>

<h2>4.Validating Azure DNS based name reservation and resolution for the private domain</h2>
<p>In Azure Portal navigate to 401-vm1 panel and connect to it with the RDP file using respective credentials.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-002/12.jpg"/>
<p>In the Virtual Machine open the command prompt and run the following command</p>
	<p>nslookup az1000402b-vm1.adatum.local 	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-002/13.jpg"/>
<p>Note the output and navigate to the local machine.</p>
<p>In Azure Portal start a PowerShell session and run the following command to create an additional DNS record.</p>
	<p>New-AzDnsRecordSet -ResourceGroupName $rg2.ResourceGroupName -Name www -RecordType A -ZoneName adatum.local -Ttl 3600 -DnsRecords (New-AzDnsRecordConfig -IPv4Address "10.104.0.4")	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-002/14.jpg"/>
<p>Switch to Virtual Machine and run the following command in command prompt.</p>
	<p>nslookup www.adatum.local 	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-4-002/15.jpg"/>
