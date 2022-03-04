# Keycloak integration with Rancher



As a part the workshop we have deployed SUSE Rancher Server, Keycloak and EFK Stack for you.

The credentails for accessing above environemnt has been emailed to you on your registered email address which you have provided during workshop reistration.





## Configuring Keycloak



Click on the dropdown under Master and you will presented with the option "Add realm" .

![keycloak-move-mouse-pointer-towards-master-click-add-realm-4](../images/keycloak-move-mouse-pointer-towards-master-click-add-realm-4.jpg)



Provide the name "rancher", rest all leave as default and hit "Create".

![keycloak-add-realm-view-5-6](../images/keycloak-add-realm-view-5-6.jpg)



Upon successful creation of the  Realm - Rancher it will take you automatically page below where you can configure additional Realm settings. 

Provide Display name as "rancher sso" and leave rest all options as default and hit save.

![keycloak-add-realm-set-display-name-save-success-8](../images/keycloak-add-realm-set-display-name-save-success-8.jpg)



Under the Manage section > Users.

Click on Add user.  <<<<<<<<< Change this image highlight Add user button...

![keycloak-manage-users-click-add-user-9](../images/keycloak-manage-users-click-add-user-9.jpg)



Provide Username as "admin", First Name as "rancher" and Last Name as admin

Click and Save button.

![keycloak-users-add-user-admin-rancher-10](../images/keycloak-users-add-user-admin-rancher-10.jpg)



Once admin user is created, you can notice Success message.

![keycloak-users-add-user-admin-rancher-save-11](../images/keycloak-users-add-user-admin-rancher-save-11.jpg)



Now set the password credentials to admin user by clicking on Credentials tab.

Click Set Password.

![keycloak-users-add-user-admin-rancher-set-password-12](../images/keycloak-users-add-user-admin-rancher-set-password-12.jpg)



Once again you are prompted for Set password

Click on Set password.

![keycloak-users-add-user-admin-rancher-set-password-success-13](../images/keycloak-users-add-user-admin-rancher-set-password-success-13.jpg)



Under Configure section > Clients

Under Client ID > "account-console", copy the Base URL and paste in your browser.



![keycloak-clients-account-console-click-base-url-14](../images/keycloak-clients-account-console-click-base-url-14.jpg)



Click on "Sign In"

![keycloak-account-console-url-sign-in-15](../images/keycloak-account-console-url-sign-in-15.jpg)



You would be presented with login window for Keycloak

Provide admin user credentials for login

![keycloak-clients-account-console-url-sign-in-login-16](../images/keycloak-clients-account-console-url-sign-in-login-16.jpg)



Upon success login, you will be prompted to reset your admin password, you may choose password of your choice.

![keycloak-clients-account-console-url-sign-in-password-reset-17](../images/keycloak-clients-account-console-url-sign-in-password-reset-17.jpg)





Upon successful authentication you wil be presented to account management page.

Click on Sign Out to exit.  <<<<<<<<<<<<, Change the image highligth the rancher admin 



![keycloak-clients-account-console-url-sign-in-signout-page-18](../images/keycloak-clients-account-console-url-sign-in-signout-page-18.jpg)



Under Configure section > Clients > Create 

Create new client as "rancher"   <<<<<<<<,, highlight create button



![keycloak-clients-create-rancher-page-19](../images/keycloak-clients-create-rancher-page-19.jpg)



Create / Name the following as below

Client ID = "rancher"

Client Protocol = "openid-connect"

Rest all default and click on "Save"

![keycloak-clients-create-rancher-page-save-20](../images/keycloak-clients-create-rancher-page-save-20.jpg)



You will be presented the Success message and you will presented with the settings tab 

![keycloak-clients-create-rancher-page-save-success-21](../images/keycloak-clients-create-rancher-page-save-success-21.jpg)



Create / Name the following as below

Client ID = rancher

Name = rancher sso

Client Protocol = openid-connect

Access Type = confidential

Keep rest all as default

![keycloak-clients-create-rancher-access-type-confidential-22](../images/keycloak-clients-create-rancher-access-type-confidential-22.jpg)



The next step involve Rancher URL.

To access the Rancher URL you will have switch to Rancher UI  

Home > Configuration > Users and Authentication > Auth Provider > Keycloak (OIDC)

Under "Endpoints" , look for Rancher URL and copy the URL.  



![keycloak-clients-create-rancher-copy-rancher-url-23](../images/keycloak-clients-create-rancher-copy-rancher-url-23.jpg)



Return back to Keycloak UI

Look for "Valid Redirect URIs" option and paste the Rancher URL copied from Rancher UI.

<<<<<<<<<<<<<< highlight Rancher URI



![keycloak-clients-create-rancher-update-valid-redirect-url-24](../images/keycloak-clients-create-rancher-update-valid-redirect-url-24.jpg)



Keep rest all setting default

Click on Save

![keycloak-clients-create-rancher-click-save-25](../images/keycloak-clients-create-rancher-click-save-25.jpg)



Upon completion you will be provided with Success message.

![keycloak-clients-create-rancher-click-save-success-26](../images/keycloak-clients-create-rancher-click-save-success-26.jpg)



Home > Configure > Clients > Rancher

Move to the Credentials Tab, Copy the Secret key



![keycloak-clients-create-rancher-copy-credentails-secret-27](../images/keycloak-clients-create-rancher-copy-credentails-secret-27.jpg)



Switch Rancher UI window and paste the secrete key as Client Secret as shown below

![keycloak-clients-create-rancher-copy-credentails-in-rancher-dashboard-client-secret-28](../images/keycloak-clients-create-rancher-copy-credentails-in-rancher-dashboard-client-secret-28.jpg)



Switch to Keycloak UI window and click on Mappers Tab 



Click Create button

![keycloak-clients-create-rancher-create-mapper-29](../images/keycloak-clients-create-rancher-create-mapper-29.jpg)



Create / Name as below

Name = Groups Mapper

Mapper Type = Group Membership

Token Claim Name = groups

Full group path = OFF

Add to ID token = OFF

Add to access token = OFF

Add to userinfo = ON

Click on Save

![keycloak-clients-create-rancher-create-mapper-groups-mapper-30](../images/keycloak-clients-create-rancher-create-mapper-groups-mapper-30.jpg)





Upon completion, you will provide with Success message

![keycloak-clients-create-rancher-create-mapper-groups-mapper-success-31](../images/keycloak-clients-create-rancher-create-mapper-groups-mapper-success-31.jpg)



Click on Create button

![keycloak-clients-create-rancher-create-mapper-again-32](../images/keycloak-clients-create-rancher-create-mapper-again-32.jpg)



Create / Name as below

Name = Client Audience

Mapper Type = Audience

Included Client Audience = rancher (use dropdown for client selection )

Add to ID token = OFF

Add to access token = ON

Click on Save

![keycloak-clients-create-rancher-create-mapper-client-audience-33](../images/keycloak-clients-create-rancher-create-mapper-client-audience-33.jpg)





You will presented with Success message as below

![keycloak-clients-create-rancher-create-mapper-client-audience-success-34](../images/keycloak-clients-create-rancher-create-mapper-client-audience-success-34.jpg)





Click on Create button

![keycloak-clients-create-rancher-create-mapper-again-35](../images/keycloak-clients-create-rancher-create-mapper-again-35.jpg)





Create / Name as below

Name = Group Path

Mapper Type = Group Membership (select from dropdown list)

Token Claim Name = full_group_path

Full group path = ON

Add to ID token = OFF

Add to access token = OFF

Add to userinfo = ON

Click on Save

![keycloak-clients-create-rancher-create-mapper-group-path-36](../images/keycloak-clients-create-rancher-create-mapper-group-path-36.jpg)



You will presented with Success message as below

![keycloak-clients-create-rancher-create-mapper-group-path-success-37](../images/keycloak-clients-create-rancher-create-mapper-group-path-success-37.jpg)



Finally all 3 mapper are added as below

![keycloak-clients-create-rancher-create-mapper-complete-38](../images/keycloak-clients-create-rancher-create-mapper-complete-38.jpg)



For detail documentation, please refer to link below

https://rancher.com/docs/rancher/v2.6/en/admin-settings/authentication/keycloak-oidc/



With this, we have successfully completed all required steps in Exercise 2. We are ready to move to the Exercise 3 [Exercise-3-Integrate-Rancher-with-Keycloak](./Exercise-3-Integrate-Rancher-with-Keycloak.md)

