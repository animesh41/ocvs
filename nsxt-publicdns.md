---
duration: PT0H60M0S
description: Create and configure a virtual network on Oracle Cloud Infrastructure.
level: Beginner
roles: DevOps;Developer
lab-id: 765b4ce1-5c77-4c9d-b74b-fe33689c45e2
products: phoenix-1/iaas;en/cloud/oracle-cloud-infrastructure/oci
keywords: Networking,IaaS
inject-note: true
---
# Tutorial Title - Use title casing and imperative verb, not gerund (E.g., Create a Virtual Cloud Network)

## Introduction

Provide a brief description of the lab. This can include background information, intended audience, and important notes for getting started. 

**Note:** This is a sample note. Copy and edit this note throughout your tutorial as needed.
**Tip:** This is a sample tip. Copy and edit this tip throughout your tutorial as needed.

### Objectives

List what users can expect to accomplish upon completing this tutorial/lab.

- Learn how to provision a new Autonomous Database
- Objective 2
- Objective 3

### Prerequisites

List what users are expected to complete or have before starting this tutorial/lab. This section is optional; delete if not needed.

- Prerequisite 1
- Prerequisite 2
- Prerequisite 3

<!-- Create as many step sections as needed. If you need only one step section, remove all other step sections and the text "Step 1: " from your step title. -->

## Step 1: Step title - use sentence casing and imperative verb

Enter a brief description here if needed.

1. Enter your first step. Make sure to put UI labels and text in **bold**.

   Provide more step info here if needed.

1. Enter your second step. This is an example of a `code phrase`.

1. Enter your third step. This is an example of a code block:

   ```
   $ cd ~
   $ mkdir git
   $ cd git
   $ git config --system core.longpaths true
   ```
   This is another example of a code block, but with the second line indented:
   
   ```
   # reboot
        The system is going down for reboot NOW!
   ```

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

## Next Steps

Provide information about the next tutorial/lab. Alternatively, provide links to additional resources. This section is optional; delete if not needed.

- [Sample link - Oracle](https://www.oracle.com)
- [Sample link - Oracle](https://www.oracle.com)
- [Sample link - Oracle](https://www.oracle.com)

## Acknowledgements

List the names and title of authors and contributors. This section is optional; delete if not needed.

- **Authors** - name (title), name (title)
- **Contributors** - name (title), name (title)

## Learn More

Explore other labs on [docs.oracle.com/learn](https://docs.oracle.com/learn) or access more free learning content on the [Oracle Learning YouTube channel](https://www.youtube.com/user/OracleLearning). Additionally, visit [education.oracle.com/learning-explorer](https://education.oracle.com/learning-explorer) to become an Oracle Learning Explorer.

For product documentation, visit [Oracle Help Center](https://docs.oracle.com).

