---
duration: PT0H60M0S
description: Configure Public DNS Zone for OCVS SDDC workloads on NSX-T Overlay
level: Intermediate
roles: IT;Power User;Technology Manager
lab-id: 765b4ce1-5c77-4c9d-b74b-fe33689c45e2
products: en/cloud/oracle-cloud-infrastructure/vmware-solution
keywords: Networking,IaaS
inject-note: true
---
# Configure Public DNS Zone for OCVS SDDC workloads on NSX-T Overlay

## Introduction

This tutorial is a step-by-step guide for configuring public DNS resolution for workloads running on NSX-T Overlay networks within Oracle Cloud VMware Solution.The Oracle Cloud Infrastructure (OCI) team’s focus is to enable you, our customers, so you can perform this administrative task in your environment when necessary by following this tutorial.

### Objectives

The Objective is to let VMware SDDC workloads running on the NSX-T Overlay networks to access the Public DNS servers out of the OCVS SDDC environment.

### Prerequisites

VMware SDDC within your tenancy with appropriate permissions
Overlay Network Configuration on NSX-T

## Step 1: Step title - use sentence casing and imperative verb

For the below configuration and example, we will use the well-known Google DNS Server ip :8.8.8.8.
We will be configuring DNS forwarding on NSX-T to allow SDDC VMs to forward their DNS queries to Google DNS servers

1.	Login to the vCenter and setup a test VM. In this example, we are using Ubuntu 20.04 and is attached to an Overlay NSX-T network. 


## Step 2: Create a VCN

A virtual cloud network (VCN) is a network that you define in Oracle Cloud Infrastructure. It includes subnets, route tables, and gateways.

* When you create PaaS service instances, if you want a public subnet in the `ManagedCompartmentForPaaS` compartment to be assigned automatically to your instances, then skip this section of the tutorial, and go directly to [Create Object Storage Buckets](https://docs.oracle.com/en/cloud/paas/java-cloud/tutorial-infrastructure-prerequisites/#section_4).

* If you want to attach your PaaS service instances to private or public subnets that you create, then follow the instructions in this section to create the VCN and subnets. You must do this the first time you create an Oracle PaaS instance on Oracle Cloud Infrastructure. For subsequent PaaS instances, you can use either the same VCN or a new VCN. This choice is based on whether the PaaS service depends on other PaaS services. For example, a Java Cloud Service instance must be in the same VCN as the Database Cloud Service deployment with which it is associated.

1. In the Oracle Cloud Infrastructure web console, in the region-selector field near the upper right corner, select the region in which you want to create the Oracle PaaS service instances.

   **Note:** Select a region that's within the default data region of your account. For example, if your default data region is EMEA, then select eu-frankfurt-1 or uk-london-1.
   
   ![](images/select-region-oci.png "select an Oracle Cloud Infrastructure region") <!-- Sample standalone image -->
   
   [Description of the illustration select-region-oci.png](files/select-region-oci.txt) <!-- Sample link to non-image asset -->
   
1. Click ![](images/dashboard_menu.png "Services menu") near the upper left corner of the web console. <!-- Sample inline image -->

1. Under **Networking**, select **Virtual Cloud Networks**.

1. On the Virtual Cloud Networks page, click **Create Virtual Cloud Network**.

## Step 3: Step title - use sentence casing and imperative verb

1. First step.

1. Second step.

1. Third step.

## Acknowledgements

List the names and title of authors and contributors. This section is optional; delete if not needed.

- **Authors** - Animesh Dixit (Principal Cloud Architect), name (title)
- **Contributors** - name (title), name (title)

## Learn More

Explore other labs on [docs.oracle.com/learn](https://docs.oracle.com/learn) or access more free learning content on the [Oracle Learning YouTube channel](https://www.youtube.com/user/OracleLearning). Additionally, visit [education.oracle.com/learning-explorer](https://education.oracle.com/learning-explorer) to become an Oracle Learning Explorer.

For product documentation, visit [Oracle Help Center](https://docs.oracle.com).

