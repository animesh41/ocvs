Here, the Goal is to let VMware SDDC workloads running on the NSX-T Overlay networks to access the Public DNS servers out of the OCVS SDDC environment.

For the below configuration and example, we will use the well-known Google DNS Server ip :8.8.8.8.

We will be configuring DNS forwarding on NSX-T to allow SDDC VMs to forward their DNS queries to Google DNS servers.

High Level steps:

•	Public DNS Server IP: 8.8.8.8
•	Configure a Public DNS Zone with the Public DNS Server IP.
•	Configure a DNS Service IP on NSX-T and attach it to the respective Tier-1 GW.  This is the IP to which Client VMs running on SDDC attached to NSX-T overlay networks will send the DNS queries.
•	Configure SNAT rules on NSX-T
•	Update VCN route table 

![image](https://user-images.githubusercontent.com/12230297/161758470-2401ff0d-333e-4982-ae00-d8d7a527d527.png)

Step by Step Configuration:

1.	Login to the vCenter and setup a test VM. In this example, we are using Ubuntu 20.04 and is attached to an Overlay NSX-T network. 

 ![image](https://user-images.githubusercontent.com/12230297/161758594-dd267f3b-ef11-4df6-9526-cb9a99e95b08.png)


2.	Under DNS Zones, create a new DNS Zone as Public and set the Public DNS server , in this case 8.8.8.8.

 



3.. Under DNS Services, add the DNS Service IP (192.168.30.254) and attach to Tier1 Gateway. Use the DNS zone created in previous step as the Default DNS zone.

 


4.	Next, create a new Overlay Segment on NSX-T and configure DNS by adding the DNS service IP. The VMs or Clients attached to this segment will use the DNS service IP as the endpoint. Use the edit DHCP config. 

 

 


5.	Validate that the settings have taken effect on the Ubuntu machine. If the machine is already powered on, a reboot may be required.

 



6.	Next, configure NSX-T NAT rule to allow SDDC VMs to access external networks or public networks. Here, we are doing SNAT for the Segment network 192.168.20.0/24 to NSX-T HA VIP IP.

 

7.	Similarly, as the DNS Service IP is altogether a different IP for it to forward requests to 8.8.8.8, a separate NAT rule must be written. Here, we are writing a SNAT rule for 192.168.30.254/32 IP 

 
8.	Now, that the configuration is complete from NSX-T end, for the DNS query response to reach back to the SDDC VMs, a return route is required on the VCN NSX Edge Uplink1 route tables for the segments and the DNS service IP. 

 

9.	If everything is good, then once you try to ping google.com or anything else on internet it should be able to resolve from the VM running on NSX-T overlay.

 

Hope this helps.!!
![image](https://user-images.githubusercontent.com/12230297/161758534-56f2d35a-c63a-4266-becd-cd5ca0a38c5d.png)
