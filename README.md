# Kubernetes Management with SUSE Rancher on Microsoft Azure

## Abstract and learning objectives

This is an in-depth workshops designed to give DevOps and IT teams the hands-on skills they need to deploy and manage Kubernetes everywhere with SUSE Rancher running on Microsoft Azure.

The content will be delivered by technical experts and aim to educate anyone interested in learning how to use containers or Kubernetes.

During these virtual hands-on workshops, our technical experts will provide an introduction to Rancher, Docker, and Kubernetes and then walk through the steps for deploying a Kubernetes cluster.

The key topics that will be covered at the workshop include:

- Docker and Kubernetes Concepts and Architecture
- Installation and Configuration of Rancher Server
- Kubernetes Cluster Deployment
- Application Deployment and Access

## Overview

TODO: Describe a scenario here.

## Solution architecture

Derek to provide the lab architecture.

1 VM - Rancher server (RKE2), Keycloak with persistent storage 

2 VM - Downstream RKE2 clusters (single node cluster)

3 VM - RKE2 HA cluster (3 nodes) running EFK stack 

All of the above environment will be pre-installed and made available for the workshop. The access  the workshop environment will be emailed to you on your registered email address for the workshop.

In this workshop we will help you integrating Keycloak as an external authentication provider with Rancher, we will demonstrate authentication and authorization. further we will also look at integration of EFK stack integration with Rancher.

  

This is what we are going to build in this workshop. We will create a resource group to contain the resources to be deployed in this workshop. Then, we will deploy �Rancher Server as a VM within this resource group. We will then configure the Rancher Server to automate the provisioning of Kubernetes (based on RKE2) into the same resource group but different subnets. We will then explore some management and application deployment features in Rancher.

[![Lab Solution Diagram](https://github.com/vijaymlinux/rancher-on-azure-workshop/raw/main/docs/images/suse-rancher-lab-diagram.png)](https://github.com/vijaymlinux/rancher-on-azure-workshop/blob/main/docs/images/suse-rancher-lab-diagram.png)



This repository contains all the scripts and Kubernetes manifests for complimenting its hands-on workshop.

- [Exercise-1-Accessing-Rancher-and-Keycloak](./docs/Exercise-1-Accessing-Rancher-and-Keycloak.md)
- [Exercise-2-Configure-Keycloak.md](./docs/Exercise-2-Configure-Keycloak.md)
- [Exercise-3-Integrate-Rancher-with-Keycloak](./docs/Exercise-3-Integrate-Rancher-with-Keycloak.md)
- [Exercise-4-Create-Keycloak-Users-Role-Mapping](./docs/Exercise-4-Create-Keycloak-Users-Role-Mapping.md)
- [Exercise 5 - Rancher Roles & Assignment](./docs/Exercise-5-Rancher-Role-Assignment-and-RBAC.md)
- 
- [Part 6 - Lab Clean Up](https://github.com/dsohk/rancher-devsecops-workshop/blob/main/docs/part-6.md)
- 

## Agenda

09:15 – 09:30 – Introduction (15 mins)

- Workshop Objectives
- 

09:30 – 9:45 - Keycloak integration with Rancher

- Configuring Keycloak

- Integration with Rancher

  

09:45 – 10:15 - Authentication & Authorisation

- Creating users in Keycloak
- User authentication
- Configure and Assign roles
- Authorisation

11:00 – 11:15 BREAK

11:15 – 12:15 – EFK (Elastic, FluentD and Kibana) integration with Rancher

- Configuring Kibana

- Configuring Rancher logging (FluentD)

- Log shipping to Elastic Search

- View logs in Kibana

- Report Generation

  

13:15 - 13:30 - Q&A



## Having trouble?

First, verify you have followed all written lab instructions (including the Before the Hands-on lab document).

Next, submit an issue with a detailed description of the problem.

Do not submit pull requests. Our content authors will make all changes and submit pull requests for approval.

If you are planning to present a workshop, review and test the materials early! We recommend at least two weeks prior.

Please allow 5 - 10 business days for review and resolution of issues.