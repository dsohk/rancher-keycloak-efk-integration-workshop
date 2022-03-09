# **SUSE Virtual Hands-on Workshop Onboarding Enterprise-grade Container Platform Experience with SUSE Rancher**



## Abstract and learning objectives

### Central Authentication

Forcing users to enter their credentials every time they want to use kubernetes clusters deployed across multi-cloud and hybrid environment will lead to several problems. Common problems include lowered user productivity, increased administration costs and security issues.
As companies and organizations are adding more cloud native services to their kubernetes clusters spread across multi-cloud and hybrid environment it is becoming an increasingly important problem.
This workshop is designed to showcase how to reduce or completely mitigate this problem by allowing users to sign on once and centralizing access control decisions.

### Central Logging

System logs are critical function in any software-intensive systems, generally logs are recorded to specify the state of the system or events in the system at important points in time. Unfortunately, log entries are captured in an ad-hoc and unstructured fashion, hence limiting their usefulness for
analytics and troubleshooting the systems. This workshop is designed to showcase how to reduce this problem by centralising the logs and assist in generating smart analytics and faster response to resolution.



## Overview

### SUSE Rancher:

**Open Source Container Management Platform**
Your organization is deploying Kubernetes clusters to accelerate digital transformation. SUSE Rancher unifies these clusters to ensure consistent operations, workload management, and enterprise-grade security – from core to cloud to edge.

**Supports any Certified Kubernetes Distribution**
SUSE Rancher supports any CNCF-certified Kubernetes distribution. For on-premises workloads, we offer the RKE. We support all the public cloud distributions, including EKS, AKS, and GKE. At the edge, we offer K3s.

**Simplifies Multi-Cluster Operations**
SUSE Rancher provides simple, consistent cluster operations, including provisioning, version management, visibility and diagnostics, monitoring and alerting, and centralized audit.

**Unifies Security, Policy, and User Management**
SUSE Rancher lets you automate processes and applies a consistent set of user access and security policies for all your clusters, no matter where they’re running.

**Drives Adoption with Shared Tools & Services**
SUSE Rancher provides a rich catalogue of services for building, deploying, and scaling containerized applications, including app packaging, CI/CD, logging, monitoring, and service mesh.

### Keycloak:

Keycloak is an open source software product to allow single sign-on with Identity and Access Management aimed at modern applications and services.

### EFK Stack:

EFK stands for Elasticsearch, Fluentd, and Kibana. EFK is a popular and the best open-source choice for the Kubernetes log aggregation and analysis.

Elasticsearch is a distributed and scalable search engine commonly used to sift through large volumes of log data.

Fluentd is a log shipper. It is an open source log collection agent which support multiple data sources and output formats.

Kibana is UI tool for querying, data visualization and dashboards. It is a query engine which allows you to explore your log data through a web interface, build visualizations for events log, query-specific to filter information for detecting issues



## Solution Architecture

**1 VM - Rancher server (RKE2), Keycloak and Elastic Search Instance**

**2 VM - Downstream RKE2 clusters (single node cluster)**

All of the above environment will be pre-installed and made available for the workshop. The login credentials and URL's will be shared via web link.

In this workshop we will help you integrating Keycloak as an external authentication provider with Rancher, we will demonstrate authentication and authorization. further we will also look at integration of EFK stack integration with Rancher.



This repository contains following Exercise to complete tasks related to Centralised Authentication using Keycloak and Centralised Logging using EFK Stack.

- [Exercise-1: Accessing-Rancher-and-Keycloak](./docs/Exercise-1-Accessing-Rancher-and-Keycloak.md)

- [Exercise-2: Configure-Keycloak.md](./docs/Exercise-2-Configure-Keycloak.md)

- [Exercise-3: Integrate-Rancher-with-Keycloak](./docs/Exercise-3-Integrate-Rancher-with-Keycloak.md)

- [Exercise-4: Create-Keycloak-Users-Role-Mapping](./docs/Exercise-4-Create-Keycloak-Users-Role-Mapping.md)

- [Exercise 5: Rancher Roles & Assignment](./docs/Exercise-5-Rancher-Role-Assignment-and-RBAC.md)

- [Exercise 6: Configure Rancher Logging](./docs/Exercise-6-Configure-Rancher-Logging.md)

- [Exercise 7: View Logs Using Kibana Dashboard](./docs/Exercise-7-View-Logs-Using-Kibana-Dashboard.md)

  

## Agenda

09:15 – 09:30 – Introduction (15 mins)

- Workshop Objectives

09:30 – 9:45 - Keycloak integration with Rancher

- Configuring Keycloak

- Integration with Rancher


09:45 – 10:15 - Authentication & Authorisation

- Creating users in Keycloak
- User authentication
- Configure and Assign roles
- Authorisation

10:15 – 10:20 BREAK

10:20 – 11:00 – EFK (Elastic, FluentD and Kibana) integration with Rancher

- Configuring Kibana

- Configuring Rancher logging (FluentD)

- Log shipping to Elastic Search

- View logs in Kibana

- Report Generation


11:00 - 11:30 - Q&A