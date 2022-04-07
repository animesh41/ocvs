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

## Deploy a Test VM 

For the below configuration and example, we will use the well-known Google DNS Server ip :8.8.8.8.
We will be configuring DNS forwarding on NSX-T to allow SDDC VMs to forward their DNS queries to Google DNS servers

Login to the vCenter and setup a test VM. In this example, we are using Ubuntu 20.04 and is attached to an Overlay NSX-T network. 


## Configure a Public DNS Zone with the Public DNS Server IP

1. Under DNS Zones, create a new DNS Zone as Public and set the Public DNS server , in this case 8.8.8.8.

2. Under DNS Services, add the DNS Service IP (192.168.30.254) and attach to Tier1 Gateway. Use the DNS zone created in previous step as the Default DNS zone.

## Configure NSX-T Overlay Segment and DHCP Configuration

3. Create a new Overlay Segment on NSX-T and configure DNS by adding the DNS service IP. The VMs or Clients attached to this segment will use the DNS service IP as the endpoint. Use the edit DHCP config

4. Validate that the settings have taken effect on the Ubuntu machine. If the machine is already powered on, a reboot may be required.

## Configure NSX-T NAT Rules

5. Next, configure NSX-T NAT rule to allow SDDC VMs to access external networks or public networks. Here, we are doing SNAT for the Segment network 192.168.20.0/24 to NSX-T HA VIP IP

6. Similarly, as the DNS Service IP is altogether a different IP for it to forward requests to 8.8.8.8, a separate NAT rule must be written. Here, we are writing a SNAT rule for 192.168.30.254/32 IP 

## Edit VCN Configuration

8.	Now, that the configuration is complete from NSX-T end, for the DNS query response to reach back to the SDDC VMs, a return route is required on the VCN NSX Edge Uplink1 route tables for the segments and the DNS service IP. 

If everything is good, then once you try to ping google.com or anything else on internet it should be able to resolve from the VM running on NSX-T overlay.


## Acknowledgements

List the names and title of authors and contributors. This section is optional; delete if not needed.

- **Authors** - Animesh Dixit (Principal Cloud Architect), name (title)
- **Contributors** - name (title), name (title)

## Learn More

Explore other labs on [docs.oracle.com/learn](https://docs.oracle.com/learn) or access more free learning content on the [Oracle Learning YouTube channel](https://www.youtube.com/user/OracleLearning). Additionally, visit [education.oracle.com/learning-explorer](https://education.oracle.com/learning-explorer) to become an Oracle Learning Explorer.

For product documentation, visit [Oracle Help Center](https://docs.oracle.com).

