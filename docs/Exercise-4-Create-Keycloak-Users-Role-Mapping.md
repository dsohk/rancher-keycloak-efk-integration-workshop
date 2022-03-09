# Keycloak integration with Rancher

In this **Exercise-4**, we will create Keycloak Users and Groups

### **Create Keycloak Users**

**admin1** 

**admin2**

**dev1**

**dev2**

**dev3**

**dev4**

**superadmin**

### **Create Keycloak Groups**

**cluster-admin-group1**

**cluster-admin-group2**

**senior-dev-group**

**junior-dev-group**

**super-admin-group**

### **Associate User to Group**

**admin1 ---> cluster-admin-group1**

**admin2 ---> cluster-admin-group2**

**dev1   ----> senior-dev-group**

**dev2   ----> senior-dev-group**

**dev3   ----> junior-dev-group**

**dev4   ----> junior-dev-group**

**superadmin ---> super-admin-group**



## Create Keycloak Users and Groups

Login to **Keycloak UI**

Open lab-credentials file 

Look for keyword **"keycloak_url"**, **"keycloak_admin_user"** and **"keycloak_admin_password"**

Copy and past Keycloak URL link in your favourite browser.

Keycloak URL = **"keycloak_url"**

user = **admin**

password = **keycloak_admin_password**

![keycloak-login-click-administration-console-2](../images/keycloak-login-click-administration-console-2.jpg)

![keycloak-login-prompt-3](../images/keycloak-login-prompt-3.jpg)

### **Create Keycloak Users**

HOME > Manage > Users

Click **"Add user"**

![keycloak-after-integration-click-users-click-view-all-users-1](../images/keycloak-after-integration-click-users-click-view-all-users-1.jpg)

Create / Name as below

Username = **superadmin**

First Name = **superadmin**

Last Name = **admin**

Rest all set to default settings

Click on **Save**

![keycloak-after-integration-user-create-superadmin-2](../images/keycloak-after-integration-user-create-superadmin-2.jpg)

User creation **Success** message

![keycloak-after-integration-user-create-superadmin-success-3](../images/keycloak-after-integration-user-create-superadmin-success-3.jpg)

Next step is to set the **superadmin** user password under **Credentials** tab

Click **"Set Password"**

![keycloak-after-integration-user-create-superadmin-password-set-4](../images/keycloak-after-integration-user-create-superadmin-password-set-4.jpg)

You will be re-prompted to **set password** again

![keycloak-after-integration-user-create-superadmin-password-set-prompt-5](../images/keycloak-after-integration-user-create-superadmin-password-set-prompt-5.jpg)

Now your user Set Password **Success** message

![keycloak-after-integration-user-create-superadmin-password-set-success-6](../images/keycloak-after-integration-user-create-superadmin-password-set-success-6.jpg)

Repeat the above steps for adding new user **"admin1"** and set login credentials under Credentials tab

Create / Name as below

Username = **admin1**

First Name = **admin1**

Last Name = **admin**

Rest all set to default settings

Click on **Save**

![Keycloak-user-admin1-4](../images/Keycloak-user-admin1-4.jpg)

Repeat above steps of **user creation** and **setting credentials** for following users

**admin1** 

**admin2**

**dev1**

**dev2**

**dev3**

**dev4**

**superadmin**

Finally check all required users are created as below and set with login credentials

![Keycloak-all-users-5](../images/Keycloak-all-users-5-1646377041936.jpg)

Now modify Role Mappings for each user by clicking on "**Edit**" 

Click on **Edit** for **admin1** user

![Keycloak-all-users-5](../images/Keycloak-all-users-5-1646382569208.jpg)

Select **"Role Mappings"** tab

Click on **Client Roles** (dropdown) and select **"realm-management"**

![keycloak-admin1-realm-mangement-role-mapping-6](../images/keycloak-admin1-realm-mangement-role-mapping-6.jpg)

Under **Available Roles**, select **view-users** option and click on **Add selected**

![keycloak-admin1-realm-mangement-role-mapping-7](../images/keycloak-admin1-realm-mangement-role-mapping-7.jpg)

**"view-users"** roles assigned successfully

You can notice them under the **Effective Roles** section

![keycloak-admin1-realm-mangement-role-mapping-8](../images/keycloak-admin1-realm-mangement-role-mapping-8.jpg)

You need to repeat the above steps of **Role Assignments**  "view-users" for all the **Keycloak users** as below

**admin1** 

**admin2**

**dev1**

**dev2**

**dev3**

**dev4**

**superadmin**



### **Create Keycloak Groups**

Now **Create Groups**

Home > Manage > Groups

Click **New**

Name = **cluster-admin-group1**

![keycloak-create-group-cluster-admin-group1-9](../images/keycloak-create-group-cluster-admin-group1-9.jpg)

Group created **Success** messages

![keycloak-create-group-cluster-admin-group1-10](../images/keycloak-create-group-cluster-admin-group1-10.jpg)

Click on **Role Mappings** tab and add **Available Roles** as below

![keycloak-create-group-cluster-admin-group1-11](../images/keycloak-create-group-cluster-admin-group1-11.jpg)

Select **Available Roles** and click on **Add selected**

![keycloak-create-group-cluster-admin-group1-12](../images/keycloak-create-group-cluster-admin-group1-12.jpg)

Add selected **Success** message

![keycloak-create-group-cluster-admin-group1-13](../images/keycloak-create-group-cluster-admin-group1-13.jpg)

Repeat above steps for all **Groups** as listed below

**cluster-admin-group1**

**cluster-admin-group2**

**senior-dev-group**

**senior-dev-group**

**junior-dev-group**

**junior-dev-group**

**super-admin-group**

Finally verify all **Groups** are created as below

![keycloak-create-group-cluster-admin-group1-add-user-admin1-18](../images/keycloak-create-group-cluster-admin-group1-add-user-admin1-18.jpg)



### **Associate User to Group**

**admin1 ---> cluster-admin-group1**

**admin2 ---> cluster-admin-group2**

**dev1   ----> senior-dev-group**

**dev2   ----> senior-dev-group**

**dev3   ----> junior-dev-group**

**dev4   ----> junior-dev-group**

**superadmin ---> super-admin-group**

Now add user "**admin1**" to group "**cluster-admin-group1**"

![keycloak-create-group-cluster-admin-group1-add-user-admin1-14](../images/keycloak-create-group-cluster-admin-group1-add-user-admin1-14.jpg)

Home > Manage > Users

Select **admin1** user and click on **Edit**

![keycloak-create-group-cluster-admin-group1-add-user-admin1-15](../images/keycloak-create-group-cluster-admin-group1-add-user-admin1-15.jpg)

Click on **Groups** Tab

![keycloak-create-group-cluster-admin-group1-add-user-admin1-16](../images/keycloak-create-group-cluster-admin-group1-add-user-admin1-16.jpg)

Select **cluster-admin-group1** from **Available Groups** and click on **Join**

![keycloak-create-group-cluster-admin-group1-add-user-admin1-17](../images/keycloak-create-group-cluster-admin-group1-add-user-admin1-17.jpg)



Now repeat above steps of adding users to respective groups as below.

**admin1 ---> cluster-admin-group1**

**admin2 ---> cluster-admin-group2**

**dev1   ----> senior-dev-group**

**dev2   ----> senior-dev-group**

**dev3   ----> junior-dev-group**

**dev4   ----> junior-dev-group**

**superadmin ---> super-admin-group**



Now assign **admin** user to all **groups**

Home > Manage > Users

Select **admin** user and click on **Edit**

Click on **Groups** Tab 

Click on **Join** on all groups from **Available Groups**

Ensure all **Groups** are listed under **Group Membership **as below

![keycloak-assign-admin-user-to-all-groups-19](../images/keycloak-assign-admin-user-to-all-groups-19.jpg)



Now, Switch to Rancher UI interface and add all **keycloak groups** as shown below

**cluster-admin-group1**

**cluster-admin-group2**

**senior-dev-group**

**senior-dev-group**

**junior-dev-group**

**junior-dev-group**

**super-admin-group**

![Rancher-configureation-for-keycloak-after-enable-4](../images/Rancher-configureation-for-keycloak-after-enable-4.jpg)



![Rancher-configureation-for-keycloak-after-enable-5](../images/Rancher-configureation-for-keycloak-after-enable-5.jpg)

Click on **Save** Button

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



On clicking with "**log in with Keycloak**" you would automatically routed to **Keycloak URL** and you will presented with **Keycloak login page**

In the below example we are login with "**superadmin"** user and credentials 

![rancher-server-after-integration-initial-login-all-users-superadmin-17](../images/rancher-server-after-integration-initial-login-all-users-superadmin-17.jpg)

You will be prompted to **password reset**

![rancher-server-after-integration-initial-login-all-users-superadmin-password-reset-18](../images/rancher-server-after-integration-initial-login-all-users-superadmin-password-reset-18.jpg)

Upon successful login you will be re-routed back to **Rancher UI**

![rancher-server-after-integration-initial-login-superadmin-limited-access-view-19](../images/rancher-server-after-integration-initial-login-superadmin-limited-access-view-19.jpg)

If you notice on exploring the UI you will not find lot of Rancher features and any downstream clusters which is typically visible to Rancher Admin

Log out from this session.

Login with rest of the users created in Keycloak by following above steps

**admin1, admin2, dev1, dev2, dev3, dev4, superadmin**



Now we have successfully logged in with all the above **Keycloak users**

The next step is to verify all the **Keycloak users** are reflected in its local database

For this we need to login as "**admin**" user using **Log in with Keycloak** option and using the credentials as set in the above steps

![rancher-server-after-integration-rancher-admin-login-screen-21](../images/rancher-server-after-integration-rancher-admin-login-screen-21.jpg)

Navigate to Home > Configuration > Users & Authentication > Users

Now you can see all **Keycloak users** are listed with provider **"Keycloak"** in Rancher.

![Rancher-after-configuration-list-all-users-8](../images/Rancher-after-configuration-list-all-users-8.jpg)

With this, we have successfully completed all required steps in **Exercise 4: Create Keycloak User and Groups**. 

We are ready to move to the **Exercise 5: [Exercise 5 - Rancher Roles & Assignment](./Exercise-5-Rancher-Role-Assignment-and-RBAC.md)**
