## Rancher Logging using EFK Stack

In this **Exercise-6**, we will deploy and configure Rancher Logging and deploy sample Log Generator App.



### Connecting to Elastic Search

Lets verify the if Elastic search engine is up and running, view the **elastic search URL** and login with "**elastic**" user and credentials

Open lab-credentials file 

Look for keyword **"elastic_url"**, **"elastic_user"** and **"elastic_password"** 

Copy and past Elastic URL link in your favourite browser.

Elastic URL = **"elastic_url"**

user = **elastic**

password = **"elastic_password"**

![Elastic-login-screen-shot1](../images/Elastic-login-screen-shot1.jpg)

![Elastic-login-screen-shot2](../images/Elastic-login-screen-shot2.jpg)



![Elastic-login-screen-shot3](../images/Elastic-login-screen-shot3.jpg)

The above details in the browser confirms Elastic search services are up and running.

### Connecting to Kibana Dashboard

Now lets verify the if Kibana service dashboard is available, view the Kibana URL

Open lab-credentials file 

Look for keyword **"kibana_url"**, **"elastic_user"** and **"elastic_password"** 

Copy and past Kibana URL link in your favourite browser.

Kibana URL = **"kibana_url"**

user = **elastic**

password = **"elastic_password"**

![Kibana-initial-screen-shot1](../images/Kibana-initial-screen-shot1.jpg)

![Kibana-initial-screen-shot3](../images/Kibana-initial-screen-shot3.jpg)

Click on **"Explore on my own"**

![Kibana-initial-screen-shot4](../images/Kibana-initial-screen-shot4.jpg)

Next step is to deploy Rancher logging



### Deploying Rancher Logging

Home > Explore Cluster > rke2-cluster1 > App & Marketplace > Charts

Click **Logging**

![Rancher-screen-apps-market-place-logging-1](../images/Rancher-screen-apps-market-place-logging-1.jpg)

Click on **Install**

![Rancher-screen-apps-market-place-logging-2](../images/Rancher-screen-apps-market-place-logging-2.jpg)

Continue with **default options** and click on **Next**

![Rancher-screen-apps-market-place-logging-3](../images/Rancher-screen-apps-market-place-logging-3.jpg)

Continue with **default options** and click on "**Install**"

![Rancher-screen-apps-market-place-logging-4](../images/Rancher-screen-apps-market-place-logging-4.jpg)

**Logging** deployed successfully as depicted in the image below

![Rancher-screen-apps-market-place-logging-5](../images/Rancher-screen-apps-market-place-logging-5.jpg)

Upon successful provisioning of Rancher Logging, you will see logging option available, upon expanding you will find **four** options. 

1. **ClusterFlows**

2. **ClusterOutputs**

3. **Flows**

4. **Outputs**

![Rancher-screen-apps-market-place-logging-6](../images/Rancher-screen-apps-market-place-logging-6.jpg)



#### Configure Secrets

Prior to configuring cluster output, lets configure secrets which would be required during cluster output configuration

Home > Explore Cluster > rke2-cluster1 > Storage > Secrets

Click **Create**

![Rancher-logging-configuration-storage-secrets-7](../images/Rancher-logging-configuration-storage-secrets-7.jpg)

Select "**Opaque**" option

![Rancher-logging-configuration-storage-secrets-8](../images/Rancher-logging-configuration-storage-secrets-8.jpg)

Use below options to populate the form

Namespace = **cattle-logging-system**

Name = **my-elastic**

Key = **password**

Value = < **elastic_password** >  Refer lab-credentails

![Rancher-logging-configuration-storage-secrets-9](../images/Rancher-logging-configuration-storage-secrets-9.jpg)

#### Configure Cluster Outputs

Home > Explore Cluster > rke2-cluster1 > Logging > ClusterOutputs

Click **Create**

![Rancher-logging-configuration-cluster-output-10](../images/Rancher-logging-configuration-cluster-output-10.jpg)

Select from dropdown

Output = **Elasticsearch**

![Rancher-logging-configuration-cluster-output-11](../images/Rancher-logging-configuration-cluster-output-11.jpg)



Target

Scheme = **https**

Host = < **elastic server IP address** >  Refer lab-credentials

Index Name = **fluentd**

Access 

User = **elastic**

Secret Key from Secret = **my-elastic** (from the dropdown)

key = **password**  (from the dropdown)

Click on **Create**

![Rancher-logging-configuration-cluster-output-12](../images/Rancher-logging-configuration-cluster-output-12.jpg)

Hit 3 vertical dots to **Edit YAML**

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

We have configured the cluster level output for **rke2-cluster1** to Elastic Search

#### Deploy Sample App - Log Generator

Now we will deploy sample application which will generate continuous logs and we will forward these logs to Elastic Search

Home > Explore Cluster > rke2-cluster1 >Workload > Deployments

Click **Create**

![Rancher-logging-configuration-app-deployment-0](../images/Rancher-logging-configuration-app-deployment-0.jpg)

Click on Icon with up arrow key **"Import YAML"**

![Rancher-logging-configuration-app-deployment-17](../images/Rancher-logging-configuration-app-deployment-17.jpg)



Copy the below yaml definition code into the pop up window and click on **import**

```
apiVersion: apps/v1
kind: Deployment
metadata:
 name: log-generator
spec:
 selector:
   matchLabels:
     app.kubernetes.io/name: log-generator
 replicas: 1
 template:
   metadata:
     labels:
       app.kubernetes.io/name: log-generator
   spec:
     containers:
     - name: nginx
       image: banzaicloud/log-generator:0.3.2
```



![Rancher-logging-configuration-app-deployment-18](../images/Rancher-logging-configuration-app-deployment-18.jpg)

This will create the deployment name "**Log-generator**". Its a simple deployment with 1 replicas for the log generator pod which will generate logs. 

Click **Close**

![Rancher-logging-configuration-app-deployment-19](../images/Rancher-logging-configuration-app-deployment-19.jpg)

We can see our Deployments "**Log generator**" is **Active** & up & working with (1/1) pod & 1 pod is available. 

![Rancher-logging-configuration-app-deployment-20](../images/Rancher-logging-configuration-app-deployment-20.jpg)

To view the logs, click on the 3 vertical dots & click on '**View Logs**'

![Rancher-logging-configuration-app-deployment-21](../images/Rancher-logging-configuration-app-deployment-21.jpg)

Below are the logs generated by the pod. 

![Rancher-logging-configuration-app-deployment-22](../images/Rancher-logging-configuration-app-deployment-22.jpg)



#### Configure Flows

Final step is to configure Flow.

Home > Explore Cluster > rke2-cluster1 > Logging 

Click **Flows**

Namespace = **default**

Name = **my-app-log**

In the Matches Form, you can specify Pods by giving Pod Labels, Nodes by specifying which nodes you would like to collect logs. 

You can also limit logs from specific containers. 

In our case we will leave it as default. 

![Rancher-logging-configuration-app-deployment-23](../images/Rancher-logging-configuration-app-deployment-23.jpg)

In the Output form, click on the drop down to select the Cluster Output we created "**my-elastic**"

Cluster Output = **my-elastic**

![Rancher-logging-configuration-app-deployment-24](../images/Rancher-logging-configuration-app-deployment-24.jpg)

Click on '**Create**'

![Rancher-logging-configuration-app-deployment-25](../images/Rancher-logging-configuration-app-deployment-25.jpg)

Click on the 3 vertical got to edit the YAML definition for the flow to include the below parse. Copy the below lines under spec: section, as depicted in the image below

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

Upon adding the parse you final flow definition would look like below. 

Click **Save**

![Rancher-logging-configuration-app-deployment-26](../images/Rancher-logging-configuration-app-deployment-26.jpg)

Logging Flow created successfully. 

With this, we have successfully completed all required steps in **Exercise 6: "Configure Rancher Logging"**. 

In the next section we will view the application logs generated from rke2-cluster into Elastic search.

We are now ready to move to the **Exercise 7: [Exercise 7: View Logs using Kibana Dashboard](./Exercise-7-View-Logs-Using-Kibana-Dashboard.md)**