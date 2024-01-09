# Initial-Configuration-of-a-Cisco-Switch-and-Port-Security-Features
![Network Topology](https://imgur.com/4K1jHSC.jpg)

## SUMMARY
As an initial setup, a router and a switch are configured with IP address information. Then, security aspects of the switch are implemented by limiting user access and ports availabilty. Finally, port security is configured on a switch's interface to mitigate threats such as spoofing attacks, application-layer attacks, Denial of Service and port scans. The simulation was completed in Boson NetSim CCNA 200-301. 

### IP Addresses
| Device                   | Interface    |  IP    | Subnet | Default Gateway
| ------------------------ | -----------  | -----  | ------ | ---------------
| Router4                  | FastEthernet 0/0 | 198.168.1.1 | 255.255.255.0 | -
| Switch 1                 | VLAN 1 |192.168.1.2 | 255.255.255.0 | 192.168.1.1
| PC1                      | - |192.168.1.252 | 255.255.255.0 | 192.168.1.1

## Below is a step-by-step video recorded  
[![Watch the video](https://img.youtube.com/vi/baV2BQx7pDE/hqdefault.jpg)](https://youtu.be/baV2BQx7pDE)

## Step 1: Configure Initial Connectivity Settings

1. Configure the Router4 with a host name and IP address information to the FastEthernet 0/0 interface.\
   	***Router(config)#hostname Router4***\
        ***Router4(config)#interface fastethernet 0/0***\
      	***Router4(config-if)#ip address 192.168.1.1 255.255.255.0***\
   	***Router4(config-if)#no shutdown***

2. Configure Switch 1 with a host name and assign the appropriate IP address and subnet mask to the management VLAN. \
	***Switch(config)#hostname Switch1***\
	***Switch1(config)#interface vlan 1***\
	***Switch1(config-if)#ip address 192.168.1.2 255.255.255.0***

3. Configure the IP address assigned to the FastEthernet 0/0 interface on Router4 as the default gateway for Switch1. \
	***Switch1(config)#ip default-gateway 192.168.1.1***\

4. Configure the appropriate IP address, subnet mask and default gateway on PC1. \
	***C:>ipconfig /ip 192.168.1.252 255.255.255.0***\
	***C:>ipconfig /dg 192.168.1.1***\
Also, ping Router4 to test connectivity\
	***C:>ping 192.168.1.1***

## Step 2: Enhance Security on Switch1

1. Add a user named admin with a password of cisco. Configure cisco as the enable, enable secret, vty line, and console port passwords. Plus, configure the switch to store all current and future passwords in an encrypted form:\
	***Switch1(config)#username boson password cisco***\
	***Switch1(config)#enable password cisco***\
	***Switch1(config)#enable secret level 5 cisco***\
	***Switch1(config)#line vty 0 15***\
	***Switch1(config-line)#password cisco***\
	***Switch1(config-line)#login local***\
	***Switch1(config-line)#line console 0***\
	***Switch1(config-line)#password cisco***\
	***Switch1(config-line)#login local***\
   	***Switch1(config-line)#exit***\
	***Switch1(config)#service password-encryption***\

2.  Configure all unused ports as access ports and disable them:\
	***Switch1(config)#interface range fastethernet 0/3 - 12***\
	***Switch1(config-if-range)#switchport mode access***\
	***Switch1(config-if-range)#shutdown***\ 

## Step 3: Configure Port Security on Switch1

1. MAC address of PC1, connected to the FastEthernet 0/2 interface, can be found by using the show mac-address-table command. Then, configure port security on the FastEthernet 0/2 interface by first disabling the interface and setting it to access mode. \
	***Switch1#show mac-address-table***\
 	***Switch1(config)#interface fastethernet 0/2***\
	***Switch1(config-if)#shutdown***\
   	***Switch1(config-if)#switchport mode access***

2. Although the maximum number of MAC addresses allowed is 1 by default, we'll limit the maximum number of devices that can connect the FastEthernet 0/2 interface to 1 and use the MAC address of PC1 as the device that will be allowed connect to the interface:\
	***Switch1(config-if)#switchport port-security***\  
	***Switch1(config-if)#switchport port-security maximum 1***\
	***Switch1(config-if)#switchport port-security mac-address 000C.7988.2251***

3. Off the three modes in port-security (Protect, Restrict and Shutdown), the shutdown mode is enabled by default when port-security is enabled. If another device attempts to connect to the network via the FastEthernet 0/2 interface, the port will be shut down. At last, re-enable the interface by issuing no shutdown command: \
	***Switch1(config-if)#switchport port-security violation shutdown***\
  	***Switch1(config-if)#no shutdown***


	







