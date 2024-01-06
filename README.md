# Initial-Configuration-of-a-Cisco-Switch-and-Port-Security-Features
![Network Topology](https://imgur.com/4K1jHSC.jpg)

## SUMMARY
As an initial setup, a router and a switch are configured with IP address information. Then, security aspects of the switch is implemented by limiting user access and ports availabilty. Finally, port security is configured on a switch's interface to mitigate threats such as spoofing attacks, application-layer attacks, Denial of Service and port scans. 

### IP Addresses
| Device                   | Interface    |  IP    | Subnet | Default Gateway
| ------------------------ | -----------  | -----  | ------
| Router4                  | FastEthernet 0/0 | 198.168.1.1 | 255.255.255.0 | -
| Switch 1                 | VLAN 1 |192.168.1.2 | 255.255.255.0 | 192.168.1.1
| PC1                  | - |192.168.1.252 | 255.255.255.0 | 192.168.1.1

## Below is a step-by-step video recorded  
[![Watch the video]( )

## Step 1: Configure DHCP 
1. First, let's see the IP configuration of each PC and configure them to obtain IP addresses by using DHCP.\
	***C:>ipconfig | C:>ipconfig /ip dhcp***
   
2. See if DHCP server has been configured on Router1\
	 ***Router1#show ip dhcp pool***
   
3. Best practice is to prevent the DHCP server from leasing IP addresses that you do not want to have conflicts later.\
	***Router1(config)#ip dhcp excluded-address 10.10.1.1***\
	***Router1(config)#ip dhcp excluded-address 10.10.1.11  10.10.1.12***
