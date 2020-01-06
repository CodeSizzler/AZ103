<h1>Attaching a managed data disk to Windows Virtual Machine</h1>

<h2>Introduction</h2>
<p>In this article we are going to discuss about attaching managed data disk to Windows Virtual Machine. You can attach number of data disks depending on size of your Virtual Machine. To attach a managed data disk to your Virtual Machine, follow the steps given below.</p>

<h2>Pre-requisites</h2>
<p>To go with this article user should need a valid Azure Subscription and some knowledge on Virtual Machine and data disk.</p>

<h2>Demo</h2>
<p>Log in with your Azure account in Azure Portal using www.portal.azure.com.•	In Azure Portal navigate to Virtual Machine panel that appear on the left side menu. •	Select a Virtual Machine from your list.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-01/001.jpg"/>
<p>Navigate to the Virtual Machine page and click on Disks and select Add Data Disk.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-01/002.jpg"/>
<p>Select Create Disk from drop down option.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-01/003.jpg"/>
<p>In create disk panel name your disk as DemoDisk and leave the rest of settings to default then click on create.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-01/004.jpg"/>
<p>After the process completion navigate to Disk panel and click on save.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-01/005.jpg"/>
<p>Now you can notice that the created disk is listed. Navigate to the overview page of Virtual Machine and click on connect.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-01/006.jpg"/>
<p>Connect to the Virtual Machine by downloading the RDP file and providing the respective credentials. After entering the Virtual Machine navigate to the Disk Management page by searching in start menu.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-01/007.jpg"/>
<p>A pop-up window will appear for the disk initialization click on OK to initialize it.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-01/008.jpg"/>
<p>Identify the disk created by you. It will appear as unallocated. Right click anywhere and select the simple volume option from the drop down.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-01/009.jpg"/>
<p>In simple new volume wizard panel proceed through keeping all the setting to default and complete. A pop-up window will appear which notify you to format the disk. After the process completes click on ok.</p>
<img src="https://codesizzlergit.blob.core.windows.net/103-03-01/010.jpg"/>
