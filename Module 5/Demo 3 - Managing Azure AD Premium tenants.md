<h1>Managing Azure AD Premium tenants</h1>

<h2>Introduction</h2>
<p>In this article you are going to learn about how to manage your Azure Active Directory using Azure portal.</p>

<h2>Steps:</h2>
<h2>1.Managing Azure AD users and groups:</h2>
<p>Log-in with your Azure account using www.portal.azure.com. In this demo you are going to use the previously created codesizzlertenant Active Directory. In Azure Portal navigate to codesizzlertenant overview panel and click on start a free trail.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/01.jpg"/>
<p>In that panel click on activate and activate your Azure Active Directory Premium P2 free Premium trail.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/02.jpg"/>
<p>After activating free trail navigate to user blade and click on create a new user with following settings:</p>
	<p>•Name: user1</p>
	<p>•User name: user1@codesizzlerdemotenant.onmicrosoft.com</p>
	<p>•Profile: set the profile configured with sales department</p>
	<p>•Properties: Default</p>
	<p>•Groups: 0 group</p>
	<p>•Directory role: User</p>
	<p>•Password: Note the default password by selecting show password</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/03.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/04.JPG"/>
<p>Create another user with following settings:</p>
	<p>•Name: user2</p>
	<p>•User name: user2@codesizzlerdemotenant.onmicrosoft.com</p>
	<p>•Profile: set the profile unconfigured with finance department</p>
	<p>•Properties: Default</p>
	<p>•Groups: 0 group</p>
	<p>•Directory role: User</p>
	<p>•Password: Note the default password by selecting show password</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/05.jpg"/>
<p>In Azure Portal navigate to codesizzlertenant >User-All user >user1-profile panel and set the location to United States.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/06.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/07.JPG"/>
<p>After setting the location navigate to licence panel and select your Active Directory Premium P2 license. Do the same process for user2. Navigate to codesizzlertenant >User-All user >user2-profile panel and set the location to United States.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/08.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/09.JPG"/>
<p>After setting the location navigate to licence panel and select your Active Directory Premium P2 license.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/10.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/11.JPG"/>
<p>Navigate to License and enable all your Active Directory Premium P2 licensing options.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/12.jpg"/>
<p>Sign out from the portal and sign-in with the same account.</p>
<p>After sign-in navigate to codesizzlertenant >Groups-All groups and create a new group with following settings:</p>
	<p>•Group type: Security</p>
	<p>•Group name: sales</p>
	<p>•Group description: Users of sales department</p>
	<p>•Membership type: default</p>
	<p>•Dynamic user members: add dynamic query with simple rule</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/14.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/15.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/16.jpg"/>
<p>Create another group with following setting:</p>
	<p>•Group type: Security</p>
	<p>•Group name: sales and finance</p>
	<p>•Group description: Users of sales department</p>
	<p>•Membership type: default</p>
	<p>•Dynamic user members Advanced rule: (user.department -eq "Sales") -or (user.department -eq "Finance")</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/17.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/18.JPG"/>
<p>View the group membership of sales and sales and finance groups note that they are under progress and wait until the process completes.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/19.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/20.JPG"/>
<p>After the process completes navigate to codesizzlertenant >Password reset.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/21.jpg"/>
<p>In password reset blade view the properties panel and configure the security with following settings for sales group and save it.</p>
	<p>•Self-service password reset enabled: Selected</p>
	<p>•Selected group: Sales</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/22.jpg"/>
<p>Then navigate to authentication panel and configure with following settings and save it.</p>
	<p>•Number of methods required to reset: 1</p>
	<p>•Methods available to users: E-mail, Mobile phone, Security question</p>
	<p>•Number of security questions required to register: 3</p>
	<p>•Number of security questions required to reset: 3</p>
	<p>•Select security questions: select any 5 question for your choice</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/23.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/24.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/25.jpg"/>
<p>After setting the authentication method navigate to registration panel to ensure the following settings are configured.</p>
	<p>•Require users to register when signing in: Yes</p>
	<p>•Number of days before users are asked to re-confirm: 180</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/26.jpg"/>
<p>Open a private browser and log-in with codesizzlertenant account and when it prompted change the password. It will prompt with More information required message and continue to don't lose access to your account page and provide respective details to change the password.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/27.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/28.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/29.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/30.JPG"/>
<p>Sign out the codesizzlertenant account and open a new private browser. In that navigate to Azure Portal and user codesizzlertenant user account to log-in. Click on forget password and set a new password by verifying your account.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/31.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/32.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/33.jpg"/>
<p>Check that you can use the new password to log-in with your Azure account.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/34.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/35.JPG"/>

<h2>2.Managing Azure AD integrated SaaS applications:</h2>
<p>In Azure Portal navigate to codesizzlertenant-Overview >Enterprise application.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/36.jpg"/>
<p>In that panel click on add an application and search for Microsoft OneDrive in the application gallery.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/37.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/38.JPG"/>
<p>Click on Microsoft OneDrive – Overview and view getting started panel. Configure Single Sign-in with password-based configuration.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/39.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/40.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/41.jpg"/>
<p>Return to Microsoft Onedrive panel and click on assign a user for testing.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/42.jpg"/>
<p>Add an assignment for sales and finance group with following settings:</p>
	<p>•Users and groups: Sales and Finance</p>
	<p>•Select role: Default access</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/43.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/44.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/45.jpg"/>
<p>Log-out form Azure Portal and close the browser. Open a new browser navigate to application access using http://myapps.microsoft.com and log-in with user2 account. After log-in click on Microsoft OneDrive icon.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/46.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/47.JPG"/>
<p>Open a new browsing window and navigate to http://myapps.microsoft.com. Signin with user2 account credentials. Verify that you can able to access Microsoft OneDrive application without re-authenticate.</p>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/48.JPG"/>
<img src="https://codesizzlergit.blob.core.windows.net/az103-5-003/49.JPG"/>
