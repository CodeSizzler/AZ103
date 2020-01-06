<h1>Adding Content Delivery Network to Azure Web app</h1>

<h2>Introduction</h2>
<p>This article helps you to add the CDN configurations to your web app using Azure portal.</p>

<h2>Prerequisites</h2>
<p>To perform this demo you must have valid Azure subscription and some knowledge on Web app, CDN.</p>

<h2>Demo</h2>
<p>Log-in to Azure portal with your Azure account using www.portal.azure.com. In Azure portal start a Bash session within the Cloud Shell. After starting the Bash session run the following command to create a directory and change the directory to the created directory.</p>
	<p>mkdir quickstart	</p>
	<p>cd $HOME/quickstart	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-001/01.jpg"/>
<p>After changing the directory run the following command to clone the sample repository to your directory.</p>
	<p>git clone https://github.com/Azure-Samples/html-docs-hello-world.git</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-001/02.jpg"/>
<p>After cloning the repository run the following commands. The following command will make a change in directory which contains the sample code and creates a Web app. It will automatically creates a default resource group to your Web app.</p>
	<p>cd html-docs-hello-world 	</p>
	<p>az webapp up --location westeurope --name <app_name>	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-001/03.jpg"/>
<p>Navigate to the created resource group and access your Web app. In the overview copy the app URL and browse for it.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-001/04.jpg"/>
<p>Navigate back to the Bash session and run the following command to open the index.html file to update your app service.</p>
	<p>Nano index.html 	</p>
<p>Open the index.html file and make a change to the <h1> tag as shown in the below image.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-001/05.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-001/06.jpg"/>
<p>Save the changes and exit the editor.</p>
<p>Note: To save the changes type ^O and to exit the editor type ^X.</p>
<p>After exiting the editor run the following command in the Bash session to update and redeploy your Web app.</p>
	<p>az webapp up --location <location> --name <app_name>	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-001/07.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-001/08.jpg"/>
<p>Once updating the Web app close the Bash session and navigate to the Azure portal. In Azure portal navigate to the created Web app. From the overview panel navigate to the Networking blade.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-001/09.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-001/10.jpg"/>
<p>In the networking bade click on configure Azure CDN to your web app option.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-001/11.jpg"/>
<p>When it prompts configure the following settings and click on create.</p>
	<p>•CDN profile: Create a new CDN profile</p>
	<p>•Name: Provide a valid name</p>
	<p>•Pricing tier: The pricing tier should be in standard or premium tier</p>
	<p>•CDN endpoint name: Give a valid endpoint name</p>
	<p>•Origin host name: Default</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-001/12.jpg"/>
<p>Wait until the endpoint gets created. Once the endpoint is created copy and browse for it, you can able to see the bootstrap.css file.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-001/13.jpg"/>
<p>Navigate to the created endpoint. In the overview panel you can able to find an option called Purge, click on that option. This option helps your CDN to refresh its cache.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-001/14.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-001/15.JPG"/>
<p>When it prompts provide the content paths which you are going to purge.After providing the paths click on purge.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-001/16.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-001/17.JPG"/>
<p>Then navigate to the Cache configuration panel and change the setting to cache every unique URL and save the settings. Thus you have added a CDN to your web app.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-001/18.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-2-001/19.JPG"/>
