## Rancher Logging using EFK Stack

### Connecting to Elastic Search

Lets verify the if Elastic search engine is up and running, view the elastic search URL and login with "elastic" user and credentials

![Elastic-login-screen-shot1](../images/Elastic-login-screen-shot1.jpg)

Provide login credentials

User = elastic

Password = < shared >



![Elastic-login-screen-shot2](../images/Elastic-login-screen-shot2.jpg)



![Elastic-login-screen-shot3](../images/Elastic-login-screen-shot3.jpg)

The above details in the browser confirms Elastic search services are up and running.

### Connecting to Kibana Dashboard

Now lets verify the if Kibana service dashboard is available, view the Kibana URL

![Kibana-initial-screen-shot1](../images/Kibana-initial-screen-shot1.jpg)

login = elastic

Password = < Shared >

![Kibana-initial-screen-shot3](../images/Kibana-initial-screen-shot3.jpg)

Click on "Explore on my own"

![Kibana-initial-screen-shot4](../images/Kibana-initial-screen-shot4.jpg)

Next step is to deploy Rancher logging

### Deploying Rancher Logging

Home > Explore Cluster > rke2-cluster1 > App & Marketplace > Charts > Logging

![Rancher-screen-apps-market-place-logging-1](../images/Rancher-screen-apps-market-place-logging-1.jpg)

Click on Install

![Rancher-screen-apps-market-place-logging-2](../images/Rancher-screen-apps-market-place-logging-2.jpg)

Continue with default options and click on Next

![Rancher-screen-apps-market-place-logging-3](../images/Rancher-screen-apps-market-place-logging-3.jpg)

Continue with default options and click on "Install"

![Rancher-screen-apps-market-place-logging-4](../images/Rancher-screen-apps-market-place-logging-4.jpg)

Logging deployed successfully as depicted in the image below

![Rancher-screen-apps-market-place-logging-5](../images/Rancher-screen-apps-market-place-logging-5.jpg)

Upon successful provisioning of Rancher Logging, you will see logging option available, upon expanding you will find four options. 

1. ClusterFlows

2. ClusterOutputs

3. Flows

4. Outputs

![Rancher-screen-apps-market-place-logging-6](../images/Rancher-screen-apps-market-place-logging-6.jpg)



#### Configure Secrets

Prior to configuring cluster output, lets configure secrets which would be required during cluster output configuration

Home > Explore Cluster > rke2-cluster1 > Storage > Secrets > Create

![Rancher-logging-configuration-storage-secrets-7](../images/Rancher-logging-configuration-storage-secrets-7.jpg)

Select "Opaque" option

![Rancher-logging-configuration-storage-secrets-8](../images/Rancher-logging-configuration-storage-secrets-8.jpg)

Use below options to populate the form

Namespace = cattle-logging-system

Name = my-elastic

Key = password

Value = < Elastic User Password Shared >

![Rancher-logging-configuration-storage-secrets-9](../images/Rancher-logging-configuration-storage-secrets-9.jpg)

#### Configure Cluster Outputs

Home > Explore Cluster > rke2-cluster1 > Logging > ClusterOutputs > Create

![Rancher-logging-configuration-cluster-output-10](../images/Rancher-logging-configuration-cluster-output-10.jpg)

Select from dropdown

Output = Elasticsearch

![Rancher-logging-configuration-cluster-output-11](../images/Rancher-logging-configuration-cluster-output-11.jpg)



Target

Scheme = https

Host = < elastic server IP address >

Index Name = fluentd

Access 

User = elastic

Secret Key from Secret = my-elastic (from the dropdown)

key = password  (from the dropdown)

Click on Create

![Rancher-logging-configuration-cluster-output-12](../images/Rancher-logging-configuration-cluster-output-12.jpg)

Hit 3 vertical dots to Edit YAML

![Rancher-logging-configuration-cluster-output-13](../images/Rancher-logging-configuration-cluster-output-13.jpg)

Copy the below lines under **"spec:"** section, as depicted in the image below

```
    ssl_verify: false
    ssl_version: TLSv1_2
```

![Rancher-logging-configuration-cluster-output-14](../images/Rancher-logging-configuration-cluster-output-14.jpg)

Copy the below lines under **"spec:"** section, as depicted in the image below

```
    include_timestamp: true
    buffer:
      timekey: 1m
      timekey_wait: 30s
      timekey_use_utc: true
```



![Rancher-logging-configuration-cluster-output-15](../images/Rancher-logging-configuration-cluster-output-15.jpg)

Final ClusterOutputs should look as below

![Rancher-logging-configuration-cluster-output-16](../images/Rancher-logging-configuration-cluster-output-16.jpg)

We have configured the cluster level output for rke2-cluster1 to Elastic Search

#### Deploy Sample App - Log Generator

Now we will deploy sample application which will generate continuous logs and we will forward these logs to Elastic Search

Home > Explore Cluster > rke2-cluster1 >Workload > Deployments > Create

![Rancher-logging-configuration-app-deployment-0](../images/Rancher-logging-configuration-app-deployment-0.jpg)



![Rancher-logging-configuration-app-deployment-17](../images/Rancher-logging-configuration-app-deployment-17.jpg)





![Rancher-logging-configuration-app-deployment-18](../images/Rancher-logging-configuration-app-deployment-18.jpg)





![Rancher-logging-configuration-app-deployment-19](../images/Rancher-logging-configuration-app-deployment-19.jpg)





![Rancher-logging-configuration-app-deployment-20](../images/Rancher-logging-configuration-app-deployment-20.jpg)





![Rancher-logging-configuration-app-deployment-21](../images/Rancher-logging-configuration-app-deployment-21.jpg)



![Rancher-logging-configuration-app-deployment-22](../images/Rancher-logging-configuration-app-deployment-22.jpg)



#### Configure Flows

![Rancher-logging-configuration-app-deployment-23](../images/Rancher-logging-configuration-app-deployment-23.jpg)



![Rancher-logging-configuration-app-deployment-24](../images/Rancher-logging-configuration-app-deployment-24.jpg)



![Rancher-logging-configuration-app-deployment-25](../images/Rancher-logging-configuration-app-deployment-25.jpg)



Copy the below lines under spec: section, as depicted in the image below

```
  filters:
    - tag_normaliser: {}
    - parser:
        remove_key_name_field: true
        reserve_data: true
        parse:
          type: nginx
  match:
     - select:
         labels:
           app.kubernetes.io/name: log-generator
```





![Rancher-logging-configuration-app-deployment-26](../images/Rancher-logging-configuration-app-deployment-26.jpg)















With this, we have successfully completed integration of Keycloak with Rancher and successfully demonstrated Rancher Roles assignments and RBAC.

In the next section we will showcase EFK stack integration with SUSE Rancher.




