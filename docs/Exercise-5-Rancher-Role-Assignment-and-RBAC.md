# Keycloak integration with Rancher



As a part the workshop we have deployed SUSE Rancher Server, Keycloak and EFK Stack for you.

The credentails for accessing above environemnt has been emailed to you on your registered email address which you have provided during workshop reistration.





## Rancher Role Assignment and RBAC

By now we know that the Keycloak users have very little access to the Rancher platform

For the users to perform the tasks they would need adequate permissions

<<<<<<<, to be update from documentation



![Rancher-server-global-Permissions-1](../images/Rancher-server-global-Permissions-1.jpg)



![Rancher-server-cluster-permissions-2](../images/Rancher-server-cluster-permissions-2.jpg)



![Rancher-server-projects-namespace-roles-permissions-3](../images/Rancher-server-projects-namespace-roles-permissions-3.jpg)



login as "admin" user using Keycloak option and using the credentials as set during Excercise-2.

Navigate to Home > Configuration > Users & Authentication > Users

Click on the checkbox of superadmin user and click on 3 vertical dots and click Edit Config

<<<<<<<<<< highligh below image

![rancher-server-after-integration-rancher-admin-assign-role-4](../images/rancher-server-after-integration-rancher-admin-assign-role-4.jpg)

The default Global Permissions are set to Standard User

We need to elevate his access to higher level to "Administrator" which has full permissions at the Rancher platform level and Downstream clusters.

![rancher-server-after-integration-rancher-admin-default-role-standard-user-5](../images/rancher-server-after-integration-rancher-admin-default-role-standard-user-5.jpg)

Select "Administrator" and click Save

![rancher-server-after-integration-rancher-admin-assign-role-administrator-click-save-6](../images/rancher-server-after-integration-rancher-admin-assign-role-administrator-click-save-6.jpg)

Re-login to Rancher UI using Keycloak option

![rancher-server-after-integration-superadmin-login-after-role-assignment-7](../images/rancher-server-after-integration-superadmin-login-after-role-assignment-7.jpg)

Now you can see more options such as Continuous Delivery, Cluster Manager etc and all the downstream clusters

![rancher-server-after-integration-superadmin-after-role-assignment-access-view-8](../images/rancher-server-after-integration-superadmin-after-role-assignment-access-view-8.jpg)



Now, we will elevate the "c1admin" user to have full permissions to "rke2-cluster1" only

Home > Explore CLUSTER > select "rke2-cluster1"

![rancher-server-after-integration-rancher-admin-assign-role-c1admin-rke2-cluster1-9](../images/rancher-server-after-integration-rancher-admin-assign-role-c1admin-rke2-cluster1-9.jpg)



rke2-cluster1 > RBAC > select Cluster Members

![rancher-server-after-integration-rancher-admin-assign-role-c1admin-rke2-cluster1-click-rbac-cluster-members-10](../images/rancher-server-after-integration-rancher-admin-assign-role-c1admin-rke2-cluster1-click-rbac-cluster-members-10.jpg)



Click Add button to add Cluster Members

![rancher-server-after-integration-rancher-admin-assign-role-c1admin-rke2-cluster1-click-rbac-cluster-members-add-11](../images/rancher-server-after-integration-rancher-admin-assign-role-c1admin-rke2-cluster1-click-rbac-cluster-members-add-11.jpg)

Select "Owner" as the desired Cluster Permission and click "Create"

![rancher-server-after-integration-rancher-admin-assign-role-c1admin-rke2-cluster1-click-rbac-cluster-members-add-create-12](../images/rancher-server-after-integration-rancher-admin-assign-role-c1admin-rke2-cluster1-click-rbac-cluster-members-add-create-12.jpg)

Upon success, we can now see user "c1admin" now has the role "Cluster Owner"

![rancher-server-after-integration-rancher-admin-assign-role-c1admin-rke2-cluster1-click-rbac-cluster-members-add-create-success-13](../images/rancher-server-after-integration-rancher-admin-assign-role-c1admin-rke2-cluster1-click-rbac-cluster-members-add-create-success-13.jpg)

Lets validate by login as "c1admin" user on the Rancher UI

![rancher-server-after-integration-c1admin-login-after-role-assignment-14](../images/rancher-server-after-integration-c1admin-login-after-role-assignment-14.jpg)

Now we can see rke2-cluster1 under Explore Cluster option

![rancher-server-after-integration-c1admin-login-after-role-assignment-access-view-15](../images/rancher-server-after-integration-c1admin-login-after-role-assignment-access-view-15.jpg)

Please repeat above steps for elevating "c2admin" user to access cluster "rke2-cluster2" only





![17-rancher-server-after-integration-custom-project-role-creation-17](../images/17-rancher-server-after-integration-custom-project-role-creation-17.jpg)





![18-rancher-server-after-integration-custom-cluster-role-creation-grant-resources-18](../images/18-rancher-server-after-integration-custom-cluster-role-creation-grant-resources-18.jpg)











![19-rancher-server-after-integration-custom-cluster-role-creation-19](../images/19-rancher-server-after-integration-custom-cluster-role-creation-19.jpg)





![20-rancher-server-after-integration-dev1-user-member-role-assign-20](../images/20-rancher-server-after-integration-dev1-user-member-role-assign-20.jpg)



![21-rancher-server-after-integration-dev1-user-custom-role-assign-21](../images/21-rancher-server-after-integration-dev1-user-custom-role-assign-21.jpg)





![22-rancher-server-after-integration-dev2-user-custom-role-assign-22](../images/22-rancher-server-after-integration-dev2-user-custom-role-assign-22.jpg)



![23-rancher-server-after-integration-dev2-user-custom-role-assign-view-all-projects-23](../images/23-rancher-server-after-integration-dev2-user-custom-role-assign-view-all-projects-23.jpg)







![24-rancher-server-after-integration-all-users-role-assignment-24](../images/24-rancher-server-after-integration-all-users-role-assignment-24.jpg)





![25-rancher-server-after-integration-dev1-user--after-role-assignment-access-view-25](../images/25-rancher-server-after-integration-dev1-user--after-role-assignment-access-view-25.jpg)



![26-rancher-server-after-integration-dev1-user-create-project-26](../images/26-rancher-server-after-integration-dev1-user-create-project-26.jpg)





![27-rancher-server-after-integration-dev1-user--after-role-assignment-create-project-27](../images/27-rancher-server-after-integration-dev1-user--after-role-assignment-create-project-27.jpg)











![28-rancher-server-after-integration-dev1-user--after-role-assignmet-project-container-default-resource-limit-28](../images/28-rancher-server-after-integration-dev1-user--after-role-assignmet-project-container-default-resource-limit-28.jpg)









![29-rancher-server-after-integration-dev1-user--after-role-assignmet-test-project-created-29](../images/29-rancher-server-after-integration-dev1-user--after-role-assignmet-test-project-created-29.jpg)



![30-rancher-server-after-integration-dev1-user--after-role-assignment-create-namespace-only-30](../images/30-rancher-server-after-integration-dev1-user--after-role-assignment-create-namespace-only-30.jpg)



With this, we have successfully completed integration of Keycloak with Rancher and successfully demonstrated Rancher Roles assignments and RBAC.

In the next section we will showcase EFK stack integration with SUSE Rancher.




