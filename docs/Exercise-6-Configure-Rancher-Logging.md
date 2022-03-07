

# EFK stack integration with Rancher



As a part the workshop we have deployed SUSE Rancher Server, Keycloak and EFK Stack for you.

The credentails for accessing above environemnt has been emailed to you on your registered email address which you have provided during workshop reistration.





## Rancher Logging using EFK Stack



Lets verify the if Elastic search engine is up and running, view the elastic search URL and login with "elastic" user and credentials

![Elastic-login-screen-shot1](../images/Elastic-login-screen-shot1.jpg)





![Elastic-login-screen-shot2](../images/Elastic-login-screen-shot2.jpg)



![Elastic-login-screen-shot3](../images/Elastic-login-screen-shot3.jpg)



Now lets verify the if Kibana service dashboard is up and running, view the kibana  URL and login with "elastic" user and credentials



![Kibana-initial-screen-shot1](../images/Kibana-initial-screen-shot1.jpg)

![Kibana-initial-screen-shot3](../images/Kibana-initial-screen-shot3.jpg)



![Kibana-initial-screen-shot4](../images/Kibana-initial-screen-shot4.jpg)





![Rancher-screen-apps-market-place-logging-1](../images/Rancher-screen-apps-market-place-logging-1.jpg)



![Rancher-screen-apps-market-place-logging-2](../images/Rancher-screen-apps-market-place-logging-2.jpg)





![Rancher-screen-apps-market-place-logging-3](../images/Rancher-screen-apps-market-place-logging-3.jpg)





![Rancher-screen-apps-market-place-logging-4](../images/Rancher-screen-apps-market-place-logging-4.jpg)



![Rancher-screen-apps-market-place-logging-5](../images/Rancher-screen-apps-market-place-logging-5.jpg)



![Rancher-screen-apps-market-place-logging-6](../images/Rancher-screen-apps-market-place-logging-6.jpg)





![Rancher-logging-configuration-storage-secrets-7](../images/Rancher-logging-configuration-storage-secrets-7.jpg)





![Rancher-logging-configuration-storage-secrets-8](../images/Rancher-logging-configuration-storage-secrets-8.jpg)





![Rancher-logging-configuration-storage-secrets-9](../images/Rancher-logging-configuration-storage-secrets-9.jpg)





![Rancher-logging-configuration-cluster-output-10](../images/Rancher-logging-configuration-cluster-output-10.jpg)



![Rancher-logging-configuration-cluster-output-11](../images/Rancher-logging-configuration-cluster-output-11.jpg)





![Rancher-logging-configuration-cluster-output-12](../images/Rancher-logging-configuration-cluster-output-12.jpg)



![Rancher-logging-configuration-cluster-output-13](../images/Rancher-logging-configuration-cluster-output-13.jpg)

Copy the below lines under spec: section, as depicted in the image below



```
    ssl_verify: false
    ssl_version: TLSv1_2
```

![Rancher-logging-configuration-cluster-output-14](../images/Rancher-logging-configuration-cluster-output-14.jpg)

Copy the below lines under spec: section, as depicted in the image below

```
    include_timestamp: true
    buffer:
      timekey: 1m
      timekey_wait: 30s
      timekey_use_utc: true
```



![Rancher-logging-configuration-cluster-output-15](../images/Rancher-logging-configuration-cluster-output-15.jpg)



![Rancher-logging-configuration-cluster-output-16](../images/Rancher-logging-configuration-cluster-output-16.jpg)







![Rancher-logging-configuration-app-deployment-0](../images/Rancher-logging-configuration-app-deployment-0.jpg)



![Rancher-logging-configuration-app-deployment-17](../images/Rancher-logging-configuration-app-deployment-17.jpg)





![Rancher-logging-configuration-app-deployment-18](../images/Rancher-logging-configuration-app-deployment-18.jpg)





![Rancher-logging-configuration-app-deployment-19](../images/Rancher-logging-configuration-app-deployment-19.jpg)





![Rancher-logging-configuration-app-deployment-20](../images/Rancher-logging-configuration-app-deployment-20.jpg)





![Rancher-logging-configuration-app-deployment-21](../images/Rancher-logging-configuration-app-deployment-21.jpg)



![Rancher-logging-configuration-app-deployment-22](../images/Rancher-logging-configuration-app-deployment-22.jpg)



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




