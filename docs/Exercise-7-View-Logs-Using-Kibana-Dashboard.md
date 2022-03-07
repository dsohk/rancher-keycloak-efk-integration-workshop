

# Rancher Logging using EFK Stack



## View Logs using Kibana Dashboard

Open Kibana Dashboard 

Kibana > Stack Management > Kibana > Index Patterns

![Kibana-index-pattern-creation-27](../images/Kibana-index-pattern-creation-27.jpg)

Name = fluentd

Timestap field = @timestamp

Click on **'Create Index Pattern'**

![Kibana-index-pattern-creation-28](../images/Kibana-index-pattern-creation-28.jpg)

Analytics > Discover > Available fields > Select field

1. Kubernetes.pod_name
2. Agents

![Kibana-index-pattern-creation-29](../images/Kibana-index-pattern-creation-29.jpg)



![Kibana-index-pattern-creation-30](../images/Kibana-index-pattern-creation-30.jpg)

We will see reduced data stream & logs from the pods will be visible. 

![Kibana-index-pattern-creation-31](../images/Kibana-index-pattern-creation-31.jpg)



![Kibana-index-pattern-creation-32](../images/Kibana-index-pattern-creation-32.jpg)













With this, we have successfully completed integration of Keycloak with Rancher and successfully demonstrated Rancher Roles assignments and RBAC.

In the next section we will showcase EFK stack integration with SUSE Rancher.



