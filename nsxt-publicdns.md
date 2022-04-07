---
duration: PT0H60M0S
description: Configure Public DNS for OCVS SDDC workloads on NSX-T Overlay
level: Intermediate
roles: IT;Power User;Technology Manager
lab-id: 765b4ce1-5c77-4c9d-b74b-fe33689c45e2
products: en/cloud/oracle-cloud-infrastructure/vmware-solution
keywords: Networking,IaaS
inject-note: true
---
# Configure Public DNS for OCVS SDDC workloads on NSX-T Overlay

## Introduction

This tutorial is a step-by-step guide for configuring public DNS resolution for workloads running on NSX-T Overlay networks within Oracle Cloud VMware Solution.The Oracle Cloud Infrastructure (OCI) team’s focus is to enable you, our customers, so you can perform this administrative task in your environment when necessary by following this tutorial.

### Objectives

The Objective is to let VMware SDDC workloads running on the NSX-T Overlay networks to access the Public DNS servers out of the OCVS SDDC environment.

### Prerequisites

VMware SDDC within your tenancy with appropriate permissions
VMware SDDC VCN attached to a NAT or Internet Gateway 
Overlay Network Configuration on NSX-T

## Deploy a Test VM 

For the below configuration and example, we will use the well-known Google DNS Server ip :8.8.8.8.
We will be configuring DNS forwarding on NSX-T to allow SDDC VMs to forward their DNS queries to Google DNS servers

1. Login to the vCenter and setup a test VM. In this example, we are using Ubuntu 20.04 attached to an Overlay NSX-T network. 

<img width="776" alt="image" src="https://user-images.githubusercontent.com/12230297/162179421-7bc034b2-a8de-46f6-9453-ef20cc8d8334.png">

## Configure a Public DNS Zone with the Public DNS Server IP

2. Under NSX-T Networking > DNS Zones, create a new DNS Zone as Public and set the Public DNS server IP , in this case 8.8.8.8.

<img width="865" alt="image" src="https://user-images.githubusercontent.com/12230297/162179599-ab0e1ade-cc80-402e-923f-0bd59abbe597.png">

3. Under DNS Services, add the DNS Service IP (192.168.30.254) and attach to Tier1 Gateway. Use the DNS zone created in previous step as the Default DNS zone. 

<img width="863" alt="image" src="https://user-images.githubusercontent.com/12230297/162179654-38082cf2-b82a-4818-aec7-479ab603273f.png">


## Configure NSX-T Overlay Segment and DHCP Configuration

4. Create a new Overlay Segment on NSX-T and configure DNS by adding the DNS service IP. The VMs or Clients attached to this segment will use the DNS service IP as the endpoint. Use the edit DHCP config, to configure the same. We are using DHCP for this example.

<img width="866" alt="image" src="https://user-images.githubusercontent.com/12230297/162179709-1133797d-0b15-42cb-bfc3-f662dad13b36.png">

<img width="868" alt="image" src="https://user-images.githubusercontent.com/12230297/162179766-782ff9c4-d2a6-48ad-99a8-7686a5488221.png">


5. Validate that the settings have taken effect on the Ubuntu machine, used for this example

<img width="694" alt="image" src="https://user-images.githubusercontent.com/12230297/162179821-34a9a558-7eca-45eb-a62d-01d1b2e35dee.png">


## Configure NSX-T NAT Rules

6. Next, configure NSX-T NAT rule to allow SDDC VMs to access external networks or public networks. Here, we are doing SNAT for the Segment network 192.168.20.0/24 to NSX-T HA VIP IP (Please chec the HA VIP in your deployed SDDC)

<img width="864" alt="image" src="https://user-images.githubusercontent.com/12230297/162179898-b78b59df-aec8-46c3-888a-0e24f46c74a5.png">


7. Similarly, as the DNS Service IP is altogether a different IP from the overlay segment range, in order for the forwarded requests to reach 8.8.8.8, a separate NAT rule must be written. Here, we are writing a SNAT rule specifically for 192.168.30.254/32 IP.

<img width="866" alt="image" src="https://user-images.githubusercontent.com/12230297/162179975-17312f8e-e2f2-4ab7-b2c1-678308fb4e91.png">


## Edit VCN Configuration

8.	Now, that the configuration is complete from NSX-T end, for the DNS query response to reach back to the SDDC VMs, a return route is required on the VCN NSX Edge Uplink1 route tables for the NSX-T overlay segments and the DNS service IP. Add the below route tables.

<img width="808" alt="image" src="https://user-images.githubusercontent.com/12230297/162250054-ee857adc-5181-4705-8d3a-0e360c8434a7.png">



If everything is good, then once you try to ping google.com or anything else on internet it should be able to resolve from the VM running on NSX-T overlay.


## Acknowledgements

List the names and title of authors and contributors. This section is optional; delete if not needed.

- **Authors** - Animesh Dixit (Principal Cloud Architect), name (title)
- **Contributors** - name (title), name (title)

## Learn More

Explore other labs on [docs.oracle.com/learn](https://docs.oracle.com/learn) or access more free learning content on the [Oracle Learning YouTube channel](https://www.youtube.com/user/OracleLearning). Additionally, visit [education.oracle.com/learning-explorer](https://education.oracle.com/learning-explorer) to become an Oracle Learning Explorer.

For product documentation, visit [Oracle Help Center](https://docs.oracle.com).

