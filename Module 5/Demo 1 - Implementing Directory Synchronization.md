<h1>Implementing Directory Synchronization</h1>

<p>Active Directory is a traditional service that is being used for managing the user groups and computers in an organization. Managing users in a large organization is very easy with the help of Active Directory. Corporates have now started to use cloud services for providing latent free secure services to their customers. Active Directory is also a service that is offered by cloud service providers using which the users and devices can me managed via internet from remote locations as well. We can use the Azure Active Directory service for managing users the same way the OnPremises Active Directory does. The Azure Active Directory does support us to synchronize on-premises AD resources to Azure AD to manage them from cloud.</p>
<h2>Demo Scenario:</h2>
<p>Consider that you were maintaining users of your organization in the onpremises Active Directory and now you are interested in synchronizing the Active Directory data from on-premises to Azure Active Directory for managing the users from cloud via internet. In the following demo, we will be creating an Azure Virtual Machine and will be configuring Active Directory Domain Controller and then will be creating a demo user in the AD. Then we will be implementing AD Sync to Azure Active Directory from on-premises Active Directory.</p>

<h2>Steps:</h2>
<h2>1.Deploying Azure VM hosting an Active Directory Domain Controller</h2>
<p>Before deploying the VM, let us check for the DNS that is not used in Azure for assigning to Azure AD Domain Controller. To do so, login to the Azure portal and open Cloud Shell by clicking on the option as shown below. Click on Create storage if it prompts to. Wait for a while so that the Cloud Shell gets configured.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/01.jpg"/>
<p>Run the below given command in the Cloud Shell by replacing the Domain Name Label that is highlighted in yellow color with your own label. If you get a response as True, then the DNS that you have give is unique and can be used. If you get response as False, the DNS is already used somewhere and you have to use something else. Note the DNS label that gives you a response as True as we will be using it in the later part of the demo.</p>
 	<p>Test-AzDnsAvailability -DomainNameLabel 	codesizzlerdemo	 -Location 'SouthIndia'	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/02.jpg"/>
<p>Now, let us deploy a VM in Azure that hosts a Domain Controller. To do so, go to + Create a resource and search for Template Deployment and click on Create button.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/03.jpg"/>
<p>In the template deployment blade choose active-directory-new-domain under the Load GitHub quickstart template and click on Select template button.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/04.jpg"/>
<p>Create a new Resource Group for the VM and select an appropriate location. Enter some valid login credentials for getting authenticated with VM. For the Domain Controller enter any domain name that you want. For DNS Prefix, enter the DNS label that you gave as an input in the Cloud Shell command. Leave the rest as default and click on Purchase.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/05.jpg"/>
<p>The VM deployment will take more than 30 mins. Meanwhile follow the next steps.</p>

<h2>Creating Active Directory Tenant</h2>
<p>Let us create a new AD Tenant for performing AD Sync. TO do so, click on Create a resource and search for Azure Active Directory and click on Create.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/06.jpg"/>
<p>Give the name of your organization for Organization name. Give a valid name for Initial domain name as it will be acting as the DNS for your new directory. Choose a valid location and click on Create button and wait for a while.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/07.jpg"/>
<p>After the new directory gets deployed, you will get a notification as shown below. Click there and login to the new tenant using same Azure credentials.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/08.jpg"/>
<p>In the new tent, you will be displayed with your Active Directory blade as shown below. You can find that you have actually created a tenant on your own.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/09.jpg"/>
<p>Navigate to the Custom domain names option in the left side menu to see your DNS. For this demo we will be using the default DNS which is marked in the screenshot. If you wish to use a custom domain, you can add it in here for the tenant and use it.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/10.jpg"/>
<p>Now, let us add a new user in this tenant with Global Administrator rights to configure the AD Sync. To do so, click on Users -> All users and choose + New user.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/11.jpg"/>
<p>Give the user a valid name and provide the username as you wish to. Make sure to use the DNS that you noted earlier. Assign the directory role as Global administrator and tick the Show password option and copy it to clipboard and then click on Create.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/12.jpg"/>
<p>After you click on create, the user will get created.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/13.jpg"/>
<p>Now open an incognito window and navigate to portal.azure.com and login with the credentials of newly created user in the newly created tenant.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/14.jpg"/>
<p>When you sign in, you will be prompted to reset the password. Reset the password with a new password and login.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/15.jpg"/>
<p>You can now note that you have logged into the new tenant that you created earlier. You can see the tenant name in the top right corner for confirmation.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/16.jpg"/>
<p>Come back to the default directory in which you deployed the VM in the beginning and go to Virtual machines menu in the left side click on adVM.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/17.jpg"/>
<p>Click on Connect and click on Download RDP File and make RDP connection to your VM. Make sure that the VM is completely deployed. Usually, this VM takes more than 30 mins to get deployed. Check the deployment menu in the resource group for finding whether the deployment is done.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/18.jpg"/>

<h2>3.Configuring On-Premises AD in Azure to Perform AD Sync</h2>
<p>After logging into the VM, go to start menu and open Active Directory Administrative Center.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/19.jpg"/>
<p>Click on the Local option of your domain in the left side menu. Then click on New -> Organizational Unit in the right side.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/20.jpg"/>
<p>Give the name as ToSync and click on Ok button.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/21.jpg"/>
<p>After the Organizational Unit gets created, right click on it and go to New -> User.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/22.jpg"/>
<p>Enter the Full name for the user. Give User UPN login as aduser1 and choose the domain that you created. Provide a password for the account. For Other password options tick password never expires option and click on Ok.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/23.jpg"/>
<p>You can find your newly created user in the ToSync organizational unit.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/24.jpg"/>
<p>Now, let us install the AD Connect to perform AD Sync. For downloading the setup, we must have to disable the IE Enhanced Configuration in the VM. To do so, open the Local Server Manager and go to Local Server option. There click on IE Enhanced Security Configuration option.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/25.jpg"/>
<p>Turn off the setting for both user and administrator and click on Ok.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/26.jpg"/>
<p>Navigate to the browser and open the below given link and click on Download.https://www.microsoft.com/en-us/download/details.aspx?id=47594 </p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/27.jpg"/>
<p>After downloading the setup open it and agree the terms and click on Continue.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/28.jpg"/>
<p>Click on Customize option to customize the settings.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/29.jpg"/>
<p>Don’t select any additional options and click on Install.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/30.jpg"/>
<p>In the User Sign-In select Password Hash Synchronization and click on Next.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/31.jpg"/>
<p>Next, connect to the AD by using the credentials of the user account that you created in the new Active Directory Tenant and click on Next.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/32.jpg"/>
<p>After getting authenticated, choose the domain the you created for the Forest option and click on Add Directory.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/33.jpg"/>
<p>Then choose Create new AD Account. For authentication, enter the domain named followed by a back slash with the username. Also provide a password and click on Ok.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/34.jpg"/>
<p>After the directory getting configured, click on Next.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/35.jpg"/>
<p>You will be shown with a warning since we have not configured the custom domain for the Azure AD. Tick the Continue without matching all UPN suffixes to verified domains and click on Next.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/36.jpg"/>
<p>In Domain/OU Filtering, choose ToSync option alone and click on Next.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/37.jpg"/>
<p>Leave the other settings as default and click on Next.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/38.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/39.jpg"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/40.jpg"/>
<p>At last tick Start the synchronization process when configuration completes and click on Install.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/41.jpg"/>
<p>After the complete installation gets over, click on Exit. Now, we have all set the Azure AD Sync setup ready.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/42.jpg"/>
<p>To verify the Sync, go to Azure portal from the VM and login using the credentials of the new tenant directory.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/43.jpg"/>
<p>Then,navigate to Active Directory -> Users -> All Users. You will be able to find the demo user whom you created in the on-premises AD. Click on the user to view the profile.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/44.jpg"/>
<p>Find the details in the profile and they will be same as what as they are. Look at the Jon info category in which the Department field will be set as empty.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/45.jpg"/>
<p>Now, let us make changes to the AD user to check the synchronization. To do so, go to Active Directory Administrative Center in the start menu.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/46.jpg"/>
<p>Go to the user in there and click on the properties.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/47.jpg"/>
<p>Provide some valid data for the Department property of the user and click on Ok button.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/48.jpg"/>
<p>After saving the changes, go to start and open the PowerShell and run the below given command to perform Synchronization right away.</p>
	<p>Start-ADSyncSyncCycle -PolicyType Delta 	</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/49.jpg"/>
<p>Now, go back to the portal and refresh the User Page to find the change in the Jon info of the user as Technical under the Department option.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-001/50.jpg"/>
<p>Thus, we have configured the Azure Active Directory Sync in the following demo that can sync all your AD credentials from on-premises to Azure Active Directory.</p>
