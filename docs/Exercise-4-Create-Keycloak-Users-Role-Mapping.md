# Keycloak integration with Rancher



As a part the workshop we have deployed SUSE Rancher Server, Keycloak and EFK Stack for you.

The credentails for accessing above environemnt has been emailed to you on your registered email address which you have provided during workshop reistration.



## Keycloak User creation and role mapping

Configure users in Keycloak along with view/list access to other keycloak users and groups.

To access Keycloak, revisit our email shared which has the URL and credentials for accessing Keycloak server.  You can use your favorite browser and credential provided to Login in Keycloak. 

Since Keycloak is built using self-signed certificated and it's not a valid certificate from authorized CA, your browser will give warning. You can safely click on the link "Proceed to Keycloak-IP.sslip.io (unsafe)" to login.



![keycloak-login-security-certificate-1](../images/keycloak-login-security-certificate-1.jpg)

Click on Administration Console to login into Keycloak.

![keycloak-login-click-administration-console-2](../images/keycloak-login-click-administration-console-2.jpg)



Provide the Keycloak credentials

![keycloak-login-prompt-3](../images/keycloak-login-prompt-3.jpg)



Under Realm "Rancher" > Manage > Users

Click "Add user"

![keycloak-after-integration-click-users-click-view-all-users-1](../images/keycloak-after-integration-click-users-click-view-all-users-1.jpg)



Create / Name as below

Username = superadmin

First Name = superadmin

Last Name = admin

Rest all set to default settings

Click on Save

![keycloak-after-integration-user-create-superadmin-2](../images/keycloak-after-integration-user-create-superadmin-2.jpg)

User creation Success

![keycloak-after-integration-user-create-superadmin-success-3](../images/keycloak-after-integration-user-create-superadmin-success-3.jpg)

Next step is to set the user user credentials which would be used during login 

Click "Set Password"

![keycloak-after-integration-user-create-superadmin-password-set-4](../images/keycloak-after-integration-user-create-superadmin-password-set-4.jpg)

You will be re-prompted to set password again

![keycloak-after-integration-user-create-superadmin-password-set-prompt-5](../images/keycloak-after-integration-user-create-superadmin-password-set-prompt-5.jpg)

Now your user credentials are successfully set

![keycloak-after-integration-user-create-superadmin-password-set-success-6](../images/keycloak-after-integration-user-create-superadmin-password-set-success-6.jpg)

Repeat the above steps of adding new user "c1admin" and setting his credentials

![keycloak-after-integration-user-create-c1admin-7](../images/keycloak-after-integration-user-create-c1admin-7.jpg)

Repeat the above steps of adding new user "c2admin" and setting his credentials

![keycloak-after-integration-user-create-c2admin-8](../images/keycloak-after-integration-user-create-c2admin-8.jpg)

Repeat the above steps of adding new user "dev1" and setting his credentials

![keycloak-after-integration-user-create-dev1-9](../images/keycloak-after-integration-user-create-dev1-9.jpg)

Repeat the above steps of adding new user "dev2" and setting his credentials

![keycloak-after-integration-user-create-dev2-10](../images/keycloak-after-integration-user-create-dev2-10.jpg)

Repeat the above steps of adding new user "dev3" and setting his credentials

![keycloak-after-integration-user-create-dev3-11](../images/keycloak-after-integration-user-create-dev3-11.jpg)

Repeat the above steps of adding new user "dev4" and setting his credentials

![keycloak-after-integration-user-create-dev4-12](../images/keycloak-after-integration-user-create-dev4-12.jpg)

Finally check all required users are created as below

![keycloak-after-integration-user-creation-complete-13](../images/keycloak-after-integration-user-creation-complete-13.jpg)

Modify each user role mappings by clicking Actions "Edit"

<<<<<<<<< highlight the Edit button

![keycloak-after-integration-user-creation-complete-13](../images/keycloak-after-integration-user-creation-complete-13.jpg)

With Edit option you will be presented the tabs as below, select "Role Mappings"

Under Client Roles > select "realm-management" (dropdown)

![keycloak-after-integration-user-role-mappings-superadmin-14](../images/keycloak-after-integration-user-role-mappings-superadmin-14.jpg)

Under Available Roles, select query-users and click on Add selected

Repeat the same step for view-users

![keycloak-after-integration-user-role-mappings-superadmin-add-roles-query-users-15](../images/keycloak-after-integration-user-role-mappings-superadmin-add-roles-query-users-15.jpg)

We have successfully assigned the roles "query-users" and "view-users"

You can now see them under the Effective Roles section

![keycloak-after-integration-user-role-mappings-superadmin-add-roles-complete-16](../images/keycloak-after-integration-user-role-mappings-superadmin-add-roles-complete-16.jpg)

You need to repeat the above steps for Role Assignments  "query-users" and "view-users" for all the Keycloak users we created



## Rancher Authentication

We will now login to Rancher with all the Keycloak users we created

The url for accessing SUSE rancher is already shared over email, please copy and past in your favorite browser window.

You will now notice in UI that you are presented with two options to authenticate in Rancher

1.  Use a Local user
2. Log in with Keycloak

Since we need to check authentication of newly created Keycloak users, we will use the option no. 2         "Log in with Keycloak"

<<<<<<<<<<<< highligh the below image

![rancher-server-after-integration-initial-login-screen-16](../images/rancher-server-after-integration-initial-login-screen-16.jpg)



On clicking with "log in with Keycloak" you would automatically routed to Keycloak URL and you will presented with Keycloak login page

In the below example we are loggin with "superadmin" user and credentials 

![rancher-server-after-integration-initial-login-all-users-superadmin-17](../images/rancher-server-after-integration-initial-login-all-users-superadmin-17.jpg)

You will be prompted to password reset

![rancher-server-after-integration-initial-login-all-users-superadmin-password-reset-18](../images/rancher-server-after-integration-initial-login-all-users-superadmin-password-reset-18.jpg)

Upon successful login you will be routed to Rancher UI

<<<<<<< highlight the below image

![rancher-server-after-integration-initial-login-superadmin-limited-access-view-19](../images/rancher-server-after-integration-initial-login-superadmin-limited-access-view-19.jpg)

If you notice on exploring the UI you will not find lot of Rancher features and existing downstream clusters which is typically visible to Rancher Admin

Log out from this session.

Login with rest of the users created in Keycloak by following above steps

c1admin, c2admin, dev1, dev2, dev3, dev4

![rancher-server-after-integration-initial-login-superadmin-limited-access-view-part-20](../images/rancher-server-after-integration-initial-login-superadmin-limited-access-view-part-20.jpg)



Now we have successfully logged in with all the above Keycloak users

The next step is to verify all the Keycloak users are reflected in its local database

For this we need to login as "admin" user using Keycloak option and using the credentials as set during Excercise-2.



![rancher-server-after-integration-rancher-admin-login-screen-21](../images/rancher-server-after-integration-rancher-admin-login-screen-21.jpg)



Navigate to Home > Configuration > Users & Authentication > Users

Now you can see all Keycloak user are listed with provider "Keycloak" in Rancher local database.

![rancher-server-after-integration-rancher-admin-login-user-authentication-view-all-users-23](../images/rancher-server-after-integration-rancher-admin-login-user-authentication-view-all-users-23.jpg)





With this, we have successfully completed all required steps in Exercise 4. We are ready to move to the Exercise 5 [Exercise 5 - Rancher Roles & Assignment](./Exercise-5-Rancher-Role-Assignment-and-RBAC.md)




