## View Logs using Kibana Dashboard

### Connecting to Kibana Dashboard

![Kibana-initial-screen-shot1](../images/Kibana-initial-screen-shot1.jpg)

login = elastic

Password = < Refer to Lab-Credentials .JSON file>

![Kibana-initial-screen-shot3](../images/Kibana-initial-screen-shot3.jpg)

Navigate below path for creating Index Pattern

Home> Management >  Stack Management > Kibana > Index Patterns

![Kibana-index-pattern-creation-27](../images/Kibana-index-pattern-creation-27.jpg)

Create Index Pattern

Name = fluentd

Timestap field = @timestamp

Click on **'Create Index Pattern'**

![Kibana-index-pattern-creation-28](../images/Kibana-index-pattern-creation-28.jpg)

To view the logs, navigate the below path 

Home > Analytics > Discover

![Kibana-index-pattern-creation-29](../images/Kibana-index-pattern-creation-29.jpg)

![Kibana-index-pattern-creation-30](../images/Kibana-index-pattern-creation-30.jpg)

To filter the logs further, you choose below fields

Available fields > click on '+' symbol besides the field name

1. Kubernetes.pod_name
2. Agent

![Kibana-index-pattern-creation-32](../images/Kibana-index-pattern-creation-32.jpg)

We will see reduced data stream & logs from the pod

![Kibana-index-pattern-creation-31](../images/Kibana-index-pattern-creation-31.jpg)



With this, we have successfully completed Rancher Logging and integration with EFK Stack.

This brings us to end of the Workshop.

We hope you found this technical hands-on workshop informative and helpful.

Form SUSE Team, it was pleasure hosting this workshop.