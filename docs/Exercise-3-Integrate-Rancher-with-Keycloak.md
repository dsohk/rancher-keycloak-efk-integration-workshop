# Keycloak integration with Rancher



As a part the workshop we have deployed SUSE Rancher Server, Keycloak and EFK Stack for you.

The credentails for accessing above environemnt has been emailed to you on your registered email address which you have provided during workshop reistration.





## Rancher side configuration for Keycloak



Copy Keycloak URL from Keycloak browser window as below

https://Keycloak.IP.sslip.io    <<<<<<<< This sample URL

Switch to Rancher UI to configure Keycloak (OIDC) 

Home > Configuration > Users and Authentication > Auth Provider > Keycloak (OIDC)

Under Endpoints > Keycloak URL, paste the Keycloak URL (copied earlier)

Keycloak Realm = "rancher"

Client ID = "rancher"



![rancher-server-auth-provider-keycloak-oidc-update-keycloak-url-1](../images/rancher-server-auth-provider-keycloak-oidc-update-keycloak-url-1.jpg)



The Keycloak Client Certificate and Private key has been shared over an email used during registration of this workshop, open them with notepad editor of your choice and copy & paste in the relevant section below.



![rancher-server-copy-keycloak-ssl-certificate-2](../images/rancher-server-copy-keycloak-ssl-certificate-2.jpg)





![rancher-server-copy-keycloak-ssl-private-key-3](../images/rancher-server-copy-keycloak-ssl-private-key-3.jpg)



Paste them in their respective sections as below.

Click on Enable to save the configurations

![rancher-server-user-authentication-auth-provider-complete-settings-click-enable-4](../images/rancher-server-user-authentication-auth-provider-complete-settings-click-enable-4.jpg)





Once you Enable, you are prompted to authenticate to Keycloak for validations of the details provided



![rancher-server-user-authentication-auth-provider-complete-settings-click-enable-keycloak-login-5](../images/rancher-server-user-authentication-auth-provider-complete-settings-click-enable-keycloak-login-5.jpg)



Once you are authenticated successfully, your Keycloak OIDC will tune to active state



![Rancher-configureation-for-keycloak-after-enable-2](../images/Rancher-configureation-for-keycloak-after-enable-2-1646376019275.jpg)







![Rancher-configureation-for-keycloak-after-enable-3](../images/Rancher-configureation-for-keycloak-after-enable-3.jpg)





![rancher-server-login-after-keycloak-integration-complete-9](../images/rancher-server-login-after-keycloak-integration-complete-9.jpg)







![rancher-server-login-after-keycloak-integration-complete-keycloak-login-10](../images/rancher-server-login-after-keycloak-integration-complete-keycloak-login-10.jpg)





![rancher-server-login-after-keycloak-integration-complete-click-users-authentication-11](../images/rancher-server-login-after-keycloak-integration-complete-click-users-authentication-11.jpg)



![rancher-server-login-after-keycloak-integration-complete-click-users-view-admin-user-settings-12](../images/rancher-server-login-after-keycloak-integration-complete-click-users-view-admin-user-settings-12.jpg)





With this, we have successfully completed all required steps in Exercise 3. We are ready to move to the Exercise 4 [Exercise-4-Create-Keycloak-Users-Role-Mapping](./Exercise-4-Create-Keycloak-Users-Role-Mapping.md)


