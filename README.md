# Initial-Configuration-of-a-Cisco-Switch-and-Port-Security-Features
![Network Topology](https://imgur.com/4K1jHSC.jpg)

## SUMMARY
As an initial setup, a router and a switch are configured with IP address information. Then, security aspects of the switch is implemented by limiting user access and ports availabilty. Finally, port security is configured on a switch's interface to mitigate threats such as spoofing attacks, application-layer attacks, Denial of Service and port scans. The simulation was completed in Boson NetSim CCNA 200-301. 

### IP Addresses
| Device                   | Interface    |  IP    | Subnet | Default Gateway
| ------------------------ | -----------  | -----  | ------ | ---------------
| Router4                  | FastEthernet 0/0 | 198.168.1.1 | 255.255.255.0 | -
| Switch 1                 | VLAN 1 |192.168.1.2 | 255.255.255.0 | 192.168.1.1
| PC1                      | - |192.168.1.252 | 255.255.255.0 | 192.168.1.1

## Below is a step-by-step video recorded  
[![Watch the video](https://img.youtube.com/vi/baV2BQx7pDE/hqdefault.jpg)](https://youtu.be/baV2BQx7pDE)

## Step 1: Configure Initial Connectivity Settings

1. Issue the following commands to configure the Router4 with a host name and IP address information to the FastEthernet 0/0 interface.\
   
	***Router(config)#hostname Router4***\
        ***Router4(config)#interface fastethernet 0/0***\
      	***Router4(config-if)#ip address 192.168.1.1 255.255.255.0***\
   	***Router4(config-if)#no shutdown***

3. Configure Switch1 with a host name and assign the appropriate IP address and subnet mask to the management VLAN: \

	***Switch(config)#hostname Switch1***\
	***Switch1(config)#interface vlan 1***\
	***Switch1(config-if)#ip address 192.168.1.2 255.255.255.0***



