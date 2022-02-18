# Keycloak integration with Rancher



As a part the workshop we have deployed SUSE Rancher Server, Keycloak and EFK Stack for you.

The credentails for accessing above environemnt has been emailed to you on your registered email address which you have provided during workshop reistration.





## Accessing SUSE Rancher server

The url for accessing SUSE rancher is already shared over email, please copy and past in your favorite browser window.



Since Rancher is built using self-signed certificated and it's not a valid certificate from authorized CA, your browser will give warning. You can safely click on link "Proceed to rancher-IP.sslip.io (unsafe)" to login.



![rancher-server-login-security-certificate-1](../images/rancher-server-login-security-certificate-1-16450745768191.jpg)



Your Rancher credentials are email to you, so use the credential provided to login. 



![rancher-server-login-prompt-2](../images/rancher-server-login-prompt-2-1645004752972.jpg)





Once you login, you will be at the Rancher Homepage, You should be able to see 3 Cluster which are pre-provisioned as part of the workshop.



![rancher-server-initial-login-dashboard-3](../images/rancher-server-initial-login-dashboard-3-16450749401012.jpg)

For management of the cluster you can navigate to Global Apps > Cluster Management > Clusters

![rancher-server-click-cluster-management-4](../images/rancher-server-click-cluster-management-4-16450749715183.jpg)

You will all cluster in the cluster list.

![rancher-server-cluster-management-view-5](../images/rancher-server-cluster-management-view-5-16450749978104.jpg)

For this workshop we are instresed in User & Authentication.  To Navigate to the section where you can create & manage User, 

Home > Configuration > Users and Authentication

![rancher-server-click-users-authentication-6](../images/rancher-server-click-users-authentication-6-16450750196325.jpg)



Under User & Authentication, you can view/create User, Role & configure and manage external Authentication Provider.  

Under Users, you will local admin for Rancher. Rancher provide a unquie ID to the user for it's records.

![rancher-server-users-homepage-7-1](../images/rancher-server-users-homepage-7-1.jpg)

To access list of available External Authentication provider click on Auth Provider. 

![rancher-server-users-authentication-auth-provider-7](../images/rancher-server-users-authentication-auth-provider-7.jpg)

For our workshop we will be using Keycloak OIDC. Below is the configuration we will require to the configure KeyClock with Rancher. 

![rancher-server-users-authentication-auth-provider-click-keycloak-oidc-8](../images/rancher-server-users-authentication-auth-provider-click-keycloak-oidc-8-16450758685396.jpg)



In the upcoming section, we will configure Keycloak.





## Accessing Keycloak server

To access Keycloak, revisit our email shared which has the URL and credentials for accessing Keycloak server.  You can use your favorite browser and credential provided to Login in Keycloak. 

Since Keycloak is built using self-signed certificated and it's not a valid certificate from authorized CA, your browser will give warning. You can safely click on the link "Proceed to Keycloak-IP.sslip.io (unsafe)" to login.

In-case if you URL fail to load, check the URL. It should be "https://keycloak.IP.sslip.io"  

![keycloak-access-url-error](../images/keycloak-access-url-error.jpg)

![keycloak-login-security-certificate-1](../images/keycloak-login-security-certificate-1.jpg)

Click on Administration Console to login into Keycloak.

![keycloak-login-click-administration-console-2](../images/keycloak-login-click-administration-console-2.jpg)





Provide the Keycloak credentials



![keycloak-login-prompt-3](../images/keycloak-login-prompt-3.jpg)



Upon successful login, you will be presented below keycloak homepage

![keycloak-initial-login-dashboard-4](../images/keycloak-initial-login-dashboard-4.jpg)

