

# Keycloak integration with Rancher

In this **Exercise-5**, we will assign required Roles and Permission for Keycloak Groups



## **Rancher Role Assignment using RBAC**

By now we know that the Keycloak users have very little access to the Rancher platform

For the users to perform the tasks they would need adequate permissions

Rancher Roles are classified into 3 levels

Global Level Roles

Cluster Level Roles

Project Level Roles

![Rancher-server-global-Permissions-1](../images/Rancher-server-global-Permissions-1.jpg)

![Rancher-server-cluster-permissions-2](../images/Rancher-server-cluster-permissions-2.jpg)

![Rancher-server-projects-namespace-roles-permissions-3](../images/Rancher-server-projects-namespace-roles-permissions-3.jpg)



## Assigning Global permission to Manage Rancher Platform

**superadmin** user is a regular user created in **keycloak**.

By default, Rancher assigns Standard User Role which allows him create and manage new clusters, however they will not be able to manage any other clusters as well as rancher management platform.

For him to manage Rancher management platform we need to elevate his permissions in Rancher and granting him global permissions of administrator.

Lets check the existing permissions **superadmin** user have in Rancher and elevate him to permissions of administrator.

login as "**admin**" user using **Log in with Keycloak** option and using the credentials as set during Exercise-4.

Navigate to Home > Configuration > Users & Authentication > Users

Click on the checkbox of **superadmin** user and click on 3 vertical dots and click **Edit Config**

![rancher-list-all-users-Screen-1](../images/rancher-list-all-users-Screen-1.jpg)



![rancher-list-all-users-Screen-2](../images/rancher-list-all-users-Screen-2.jpg)

The default Global Permissions are set to **Standard User**

We need to elevate his access to higher level to **"Administrator"** which has full permissions at the Rancher platform level and Downstream clusters.

![rancher-server-after-integration-rancher-admin-default-role-standard-user-5](../images/rancher-server-after-integration-rancher-admin-default-role-standard-user-5.jpg)

Select "**Administrator**" and click **Save**

![rancher-server-after-integration-rancher-admin-assign-role-administrator-click-save-6](../images/rancher-server-after-integration-rancher-admin-assign-role-administrator-click-save-6.jpg)

Re-login to Rancher UI using Keycloak option

![rancher-server-after-integration-superadmin-login-after-role-assignment-7](../images/rancher-server-after-integration-superadmin-login-after-role-assignment-7.jpg)

Now you can see more options such as Continuous Delivery, Cluster Manager etc and all the downstream clusters

![rancher-server-after-integration-superadmin-after-role-assignment-access-view-8](../images/rancher-server-after-integration-superadmin-after-role-assignment-access-view-8.jpg)





## Assigning Cluster level permission to Manage individual clusters


Based on Organization structure we have 3 admins and 4 developers.
In the previous step we have elevated **superadmin** user to manage Rancher platform and all downstream cluster.
Now we have to explicitly assign the rest of the 2 admins to manage their own respective cluster.

In order to grant them explicit permissions to respective clusters we will need to grant user a cluster level permissions.

Now, we will now grant user "**admin1**" user as "**Cluster Owner**" role, so that **admin1** user can have full control of the cluster and all its resources.



login as "**admin**" user using **Log in with Keycloak** option and using the credentials as set during **Exercise-4.**

Home > Explore CLUSTER > select "rke2-cluster1"

![rancher-server-after-integration-rancher-admin-assign-role-c1admin-rke2-cluster1-9](../images/rancher-server-after-integration-rancher-admin-assign-role-c1admin-rke2-cluster1-9.jpg)

rke2-cluster1 > RBAC > select Cluster Members

![rancher-server-after-integration-rancher-admin-assign-role-c1admin-rke2-cluster1-click-rbac-cluster-members-10](../images/rancher-server-after-integration-rancher-admin-assign-role-c1admin-rke2-cluster1-click-rbac-cluster-members-10.jpg)



Click **Add** button

![rancher-list-add-new-member-Screen-3](../images/rancher-list-add-new-member-Screen-3.jpg)

Click on **Select Member** and type "**cluster-admin-group1**"

![rancher-list-add-new-member-Screen-4](../images/rancher-list-add-new-member-Screen-4.jpg)

Select **Cluster Permissions** as "**Owner**"

Click on **Create** button

![rancher-list-add-new-member-Screen-5](../images/rancher-list-add-new-member-Screen-5.jpg)

You can notice Group "**cluster-admin-group1**" added as **Cluster Owner**

![rancher-list-add-new-member-Screen-6](../images/rancher-list-add-new-member-Screen-6.jpg)

Logout from **admin** user from Rancher UI

Now, Lets validate access rights/permissions by login as "**admin1**" user on the **Rancher UI**

![rancher-list-add-new-member-Screen-7](../images/rancher-list-add-new-member-Screen-7.jpg)

Now we can see **rke2-cluster1** only under Explore Cluster option

![rancher-server-after-integration-c1admin-login-after-role-assignment-access-view-15](../images/rancher-server-after-integration-c1admin-login-after-role-assignment-access-view-15.jpg)



![rancher-list-add-new-member-Screen-8](../images/rancher-list-add-new-member-Screen-8.jpg)

Apps and Market place are only accessible to cluster owners

![rancher-list-add-new-member-Screen-9](../images/rancher-list-add-new-member-Screen-9.jpg)



We have successfully assigned user "admin1" user to manage cluster "rke2-cluster1"

Similarly you can repeat the above steps for user "admin2" for cluster "rke2-cluster2".

So for we have configured role and permissions for cluster administrators, in the next step we will have developers access to their respective projects /namespaces. 



## Manage Project/Namespaces

In the development team we have mix of senior and junior developers. The senior developers because of their role and experience are granted rights to create projects and namespaces. Junior developers are restricted to create namespaces only for their own development work.

Till now we have used default built-in roles and permissions, lets explore ways to create custom roles and permissions to meet very specific needs.

**dev1** user will be assigned as built-in cluster member role as well as a custom role to create and manage projects and namespaces.

**dev2** user will be assigned custom role only to create and manage namespaces in existing projects.

**dev2** user is not allowed to create any new projects.



### Create Custom Project Role

login as "**admin**" user using **Log in with Keycloak** option and using the credentials as set during **Exercise-4.**

Home >  Users & Authentication > Roles > Project/Namespaces 

Click on **Create Project /Namespaces Role**

![30-rancher-server-after-integration-custom-role-creation-31](../images/30-rancher-server-after-integration-custom-role-creation-31.jpg)

Name = **"custom-project-role1"**

Under Grant Resources > Verbs > add below

create

delete

get

list

patch

update

watch

Resource = **"Namespaces"** (from dropdown)

![17-rancher-server-after-integration-custom-project-role-creation-17](../images/17-rancher-server-after-integration-custom-project-role-creation-17.jpg)

In the previous step we have created custom project/namespace role. It cannot be assigned to users directly. They have to be first associated to custom cluster role and thereafter to the user. 

Next step is to create, custom cluster role

Home >  Users & Authentication > Roles > Cluster 

Click on **Create Cluster Role**

![30-rancher-server-after-integration-custom-cluster-role-creation-32](../images/30-rancher-server-after-integration-custom-cluster-role-creation-32.jpg)

Name = **"custom-cluster-role1"**

Under Inherit From tab> select custom-project-role "**custom-project-role1**"

![19-rancher-server-after-integration-custom-cluster-role-creation-19](../images/19-rancher-server-after-integration-custom-cluster-role-creation-19.jpg)

Keep default options under **Grant Resources** and click on **Create**

![18-rancher-server-after-integration-custom-cluster-role-creation-grant-resources-18](../images/18-rancher-server-after-integration-custom-cluster-role-creation-grant-resources-18.jpg)

Logout from **admin** user

login as "**admin1**" user using **Log in with Keycloak** option and using the credentials as set during **Exercise-4.**

Home> Explore Cluster > rke2-cluster1 > RBAC > Cluster Members 

Click **Add**

Under Select Members dropdown option, select user "**dev1**"

Under **Cluster Permissions** > 

select "**Member**"  and click on **Create**

![rancher-list-add-new-member-Screen-10](../images/rancher-list-add-new-member-Screen-10-1646750372189.jpg)

To add and manage namespace explicitly the way we wanted using the custom role, we will now assign cluster permissions "**custom-cluster-role1**" and click **Create**

![rancher-list-add-new-member-Screen-11](../images/rancher-list-add-new-member-Screen-11.jpg)

Logout from **admin**1 user

login as "**dev1**" user using **Log in with Keycloak** option and using the credentials as set during **Exercise-4.** 

![25-rancher-server-after-integration-dev1-user--after-role-assignment-access-view-25](../images/25-rancher-server-after-integration-dev1-user--after-role-assignment-access-view-25.jpg)

You can notice **dev1** user has both create Project and create Namespace option

![26-rancher-server-after-integration-dev1-user-create-project-26](../images/26-rancher-server-after-integration-dev1-user-create-project-26.jpg)

Create **New Project**

Home > Explore Cluster > rke2-cluster1> Projects/Namesapces 

Click on **Create Project**

Name = **dev1-user-project1**

![27-rancher-server-after-integration-dev1-user--after-role-assignment-create-project-27](../images/27-rancher-server-after-integration-dev1-user--after-role-assignment-create-project-27.jpg)

Under Project/Namespaces > **"dev1-user-project1"** 

Click on **Create Namespace**

![29-rancher-server-after-integration-dev1-user--after-role-assignmet-test-project-created-29](../images/29-rancher-server-after-integration-dev1-user--after-role-assignmet-test-project-created-29.jpg)

Logout from **dev1** user

login as "**admin1**" user using **Log in with Keycloak** option and using the credentials as set during **Exercise-4.** 

Home> Explore Cluster > rke2-cluster1 > RBAC > Cluster Members

Click **Add**

Under Select Members dropdown option, select user "**dev2**"

Under Cluster Permissions > select "**custom-cluster-role1**"  and click on Create 

Here, We have granted him custom cluster role only

![rancher-list-add-new-member-Screen-12](../images/rancher-list-add-new-member-Screen-12.jpg)



Since we need to give him access to view project level view, so we assign built-in  additional custom role "view all projects" and click create

![rancher-list-add-new-member-Screen-13](../images/rancher-list-add-new-member-Screen-13.jpg)

Finally we have assigned all built-in and custom roles for users "dev1" and "dev2"

![rancher-list-add-new-member-Screen-14](../images/rancher-list-add-new-member-Screen-14-1646751042375.jpg)



Logout from **admin1** user

login as "**dev2**" user using **Log in with Keycloak** option and using the credentials as set during **Exercise-4.** 

You can notice **dev2** user doesn't have option for creating new projects, but create new namespace in the existing Projects.

![30-rancher-server-after-integration-dev1-user--after-role-assignment-create-namespace-only-30](../images/30-rancher-server-after-integration-dev1-user--after-role-assignment-create-namespace-only-30.jpg)



With this, we have successfully completed all required steps in **Exercise 5: "Rancher role assignment and RBAC"**. 

We are now ready to move to the **Exercise 6: [Exercise 6: Configure Rancher Logging](./Exercise-6-Configure-Rancher-Logging.md)**
