# Keycloak integration with Rancher



As a part the workshop we have deployed SUSE Rancher Server, Keycloak and EFK Stack for you.

The credentails for accessing above environemnt has been emailed to you on your registered email address which you have provided during workshop reistration.



## Create Keycloak Users and Groups

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

Repeat the above steps of adding new user "admin1" and setting his credentials



![Keycloak-user-admin1-4](../images/Keycloak-user-admin1-4.jpg)





Finally check all required users are created as below



![Keycloak-all-users-5](../images/Keycloak-all-users-5-1646377041936.jpg)

Modify each user role mappings by clicking Actions "Edit"

<<<<<<<<< highlight the Edit button

![Keycloak-all-users-5](../images/Keycloak-all-users-5-1646382569208.jpg)

With Edit option you will be presented the tabs as below, select "Role Mappings"

Under Client Roles > select "realm-management" (dropdown)

![keycloak-admin1-realm-mangement-role-mapping-6](../images/keycloak-admin1-realm-mangement-role-mapping-6.jpg)

Under Available Roles, select view-users and click on Add selected



![keycloak-admin1-realm-mangement-role-mapping-7](../images/keycloak-admin1-realm-mangement-role-mapping-7.jpg)

We have successfully assigned the roles "view-users"

You can now see them under the Effective Roles section



![keycloak-admin1-realm-mangement-role-mapping-8](../images/keycloak-admin1-realm-mangement-role-mapping-8.jpg)



You need to repeat the above steps for Role Assignments  "view-users" for all the Keycloak users we created



Now Create Groups

![keycloak-create-group-cluster-admin-group1-9](../images/keycloak-create-group-cluster-admin-group1-9.jpg)



![keycloak-create-group-cluster-admin-group1-10](../images/keycloak-create-group-cluster-admin-group1-10.jpg)





![keycloak-create-group-cluster-admin-group1-11](../images/keycloak-create-group-cluster-admin-group1-11.jpg)



![keycloak-create-group-cluster-admin-group1-12](../images/keycloak-create-group-cluster-admin-group1-12.jpg)



![keycloak-create-group-cluster-admin-group1-13](../images/keycloak-create-group-cluster-admin-group1-13.jpg)



Now add user "admin1" to group "cluster-admin-group1"

![keycloak-create-group-cluster-admin-group1-add-user-admin1-14](../images/keycloak-create-group-cluster-admin-group1-add-user-admin1-14.jpg)



![keycloak-create-group-cluster-admin-group1-add-user-admin1-15](../images/keycloak-create-group-cluster-admin-group1-add-user-admin1-15.jpg)





![keycloak-create-group-cluster-admin-group1-add-user-admin1-16](../images/keycloak-create-group-cluster-admin-group1-add-user-admin1-16.jpg)



![keycloak-create-group-cluster-admin-group1-add-user-admin1-17](../images/keycloak-create-group-cluster-admin-group1-add-user-admin1-17.jpg)



![keycloak-create-group-cluster-admin-group1-add-user-admin1-18](../images/keycloak-create-group-cluster-admin-group1-add-user-admin1-18.jpg)



Now repeat above steps of adding users to respective groups as below.

admin1 ---> cluster-admin-group1

admin2 ---> cluster-admin-group2

dev1   ----> senior-dev-group

dev2   ----> senior-dev-group

dev3   ----> junior-dev-group

dev4   ----> junior-dev-group

superadmin ---> super-admin-group



Now assign admin user to all groups

![keycloak-assign-admin-user-to-all-groups-19](../images/keycloak-assign-admin-user-to-all-groups-19.jpg)







Switch to Rancher UI interface and add all keycloak groups as shown below

![Rancher-configureation-for-keycloak-after-enable-4](../images/Rancher-configureation-for-keycloak-after-enable-4.jpg)



![Rancher-configureation-for-keycloak-after-enable-5](../images/Rancher-configureation-for-keycloak-after-enable-5.jpg)





![Rancher-configureation-for-keycloak-after-enable-6](../images/Rancher-configureation-for-keycloak-after-enable-6.jpg)





![Rancher-configureation-for-keycloak-after-enable-7](../images/Rancher-configureation-for-keycloak-after-enable-7.jpg)





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

superadmin, admin1, admin2, dev1, dev2, dev3, dev4

![rancher-server-after-integration-initial-login-superadmin-limited-access-view-part-20](../images/rancher-server-after-integration-initial-login-superadmin-limited-access-view-part-20.jpg)



Now we have successfully logged in with all the above Keycloak users

The next step is to verify all the Keycloak users are reflected in its local database

For this we need to login as "admin" user using Keycloak option and using the credentials as set during Excercise-2.



![rancher-server-after-integration-rancher-admin-login-screen-21](../images/rancher-server-after-integration-rancher-admin-login-screen-21.jpg)



Navigate to Home > Configuration > Users & Authentication > Users

Now you can see all Keycloak user are listed with provider "Keycloak" in Rancher local database.



![Rancher-after-configuration-list-all-users-8](../images/Rancher-after-configuration-list-all-users-8.jpg)



With this, we have successfully completed all required steps in Exercise 4. We are ready to move to the Exercise 5 [Exercise 5 - Rancher Roles & Assignment](./Exercise-5-Rancher-Role-Assignment-and-RBAC.md)




