# DHCP-Configuration

# Objective
* To configure DHCP (Dynamic Host Configuration Protocol) in Cisco Packet Tracer.
* To automatically assign IP addresses to client PCs from a DHCP server or router.
* To reduce manual IP configuration and avoid IP address conflicts.
* To verify that all client devices receive valid network settings through DHCP.

# Requirments 
* Cisco Packet Tracer software
* 1 PT Router 
* 1 PT Switch 
* 2 or more PCs (clients)
* Copper Straight-Through Ethernet cables
* Configured IP network (network address and subnet mask)
* DHCP service enabled on the router or DHCP server

  ## Step 1: Connect the Devices
Connect all devices using Copper Straight-Through cables.
* PT-Router Fa0/0 → PT-Switch Fa0/1
* PC0 FastEthernet0 → PT-Switch Fa0/2
* PC1 FastEthernet0 → PT-Switch Fa0/3
After connecting the devices, verify that all links turn green, indicating successful physical connectivity.

<img width="1535" height="812" alt="Screenshot 2026-07-30 180925" src="https://github.com/user-attachments/assets/a58d3687-5e63-4710-a178-82c4ef47239c" />

 ## Step 2: Open the PT-Router
* Click on the PT-Router in the Cisco Packet Tracer workspace.
* Open the **CLI (Command Line Interface)** tab.
* Press **Enter** to access the router command prompt.
* The router is now ready for DHCP configuration commands.
  
<img width="1531" height="810" alt="Screenshot 2026-07-30 182449" src="https://github.com/user-attachments/assets/84779e47-1a29-4753-832f-d31e33db08c0" />
<img width="1536" height="820" alt="Screenshot 2026-07-30 182522" src="https://github.com/user-attachments/assets/73813952-3df1-4acb-a4ec-c1f533e4d9f1" />

## Step 3: Enter Configuration Mode
Open the router CLI and enter privileged mode, then enter global configuration mode.

Commands:
* Router> en
* Router# config t
* Router(config)#

 ## Example:
* Router> en
* Router# config t
* Enter configuration commands, one per line. End with CNTL/Z.
* Router(config)#
* After entering global configuration mode, the router is ready for DHCP configuration.

 <img width="940" height="139" alt="image" src="https://github.com/user-attachments/assets/e59ec5b0-0555-4b76-84d5-72a033537813" />

 ## Step 4: Configure the Router Interface
Configure the FastEthernet0/0 interface and assign an IP address.

Command:
* Router(config)# int fa0/0
* Router(config-if)# ip add 192.168.1.1 255.255.255.0
* Router(config-if)# no shutdown
* Router(config-if)# exit

## Example:
* Router(config)# int fa0/0
* Router(config-if)# ip address 192.168.1.1 255.255.255.0
* Router(config-if)# no shutdown

%LINK-5-CHANGED: Interface FastEthernet0/0, changed state to up

* Router(config-if)# exit
* Router(config)#
* This step assigns the IP address 192.168.1.1/24 to the router interface and enables the interface.

<img width="921" height="221" alt="image" src="https://github.com/user-attachments/assets/9f9d5ecd-80df-4a25-9844-58a2234360ba" />

## Step 5: Activate the Router Interface
After assigning the IP address, enable the FastEthernet0/0 interface using the no shutdown command.

Command:
* Router(config-if)# no shutdown
## Example:
* Router(config-if)# no shutdown

%LINK-5-CHANGED: Interface FastEthernet0/0, changed state to up
%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/0, changed state to up
* The FastEthernet0/0 interface becomes active (up), and the connection between the PT-Router and PT-Switch is successfully established.

<img width="940" height="500" alt="image" src="https://github.com/user-attachments/assets/ddec91d7-8d84-4a87-98c2-dbbb5a7d56d5" />



## Step 6: Create a DHCP Pool
Create a DHCP pool named tejaspool.

Commands:
* Router(config)# ip dhcp pool tejaspool
* Router(dhcp-config)# network 192.168.1.0 255.255.255.0
* Router(dhcp-config)# default-router 192.168.1.1
* Router(dhcp-config)# exit

## Example:
* Router(config)# ip dhcp pool tejaspool
* Router(dhcp-config)# network 192.168.1.0 255.255.255.0
* Router(dhcp-config)# default-router 192.168.1.1
* Router(dhcp-config)# exit
* Router(config)#
* This DHCP pool will automatically assign IP addresses to client PCs.

<img width="940" height="174" alt="image" src="https://github.com/user-attachments/assets/5677b53a-0146-4aaf-a392-47fee43d80f7" />

## Step 7: Configure PC0 Using DHCP

After configuring DHCP on the router, configure PC0 to obtain an IP address automatically.
1.	Click on PC0.
2.	Open the Desktop tab.
3.	Click IP Configuration.
4.	Select DHCP.

## Example:
DHCP request successful.

* IPv4 Address:      192.168.1.2
* Subnet Mask:       255.255.255.0
* Default Gateway:   192.168.1.1
* DNS Server:        0.0.0.0
* The DHCP request is successful, and PC0 automatically receives the IP address 192.168.1.2 from the router DHCP pool.

<img width="940" height="499" alt="image" src="https://github.com/user-attachments/assets/3dad89b6-a763-49dc-847d-910e23eb7e99" />
<img width="940" height="497" alt="image" src="https://github.com/user-attachments/assets/ae230ef5-4ada-472d-af3c-fae547d889b7" />

## Step 8: Configure PC1 Using DHCP

After configuring DHCP on the router, configure PC1 to obtain an IP address automatically.
1.	Click on PC1.
2.	Open the Desktop tab.
3.	Click IP Configuration.
4.	Select DHCP.

## Example:
DHCP request successful.

* IPv4 Address:      192.168.1.3
* Subnet Mask:       255.255.255.0
* Default Gateway:   192.168.1.1
* DNS Server:        0.0.0.0
* The DHCP request is successful, and PC1 automatically receives the IP address 192.168.1.3 from the router DHCP pool.

<img width="940" height="500" alt="image" src="https://github.com/user-attachments/assets/ce84f168-063a-42a6-80e3-eefa3fccb7ca" />
<img width="940" height="499" alt="image" src="https://github.com/user-attachments/assets/54acdeec-643a-450d-9ebb-d581959e9b0d" />

## Step 9: Verify Network Connectivity of the New PC (PC2)

After adding a new PC2 to the network, check whether it is receiving an IP address from the DHCP server.
1.	Click on PC2.
2.	Open Desktop → IP Configuration.
3.	Select DHCP.

## Example:
DHCP request successful.

* IPv4 Address:      192.168.1.4
* Subnet Mask:       255.255.255.0
* Default Gateway:   192.168.1.1
* DNS Server:        0.0.0.0
* The message DHCP request successful confirms that the new PC2 is properly connected to the network and the DHCP configuration is working correctly.

<img width="940" height="498" alt="image" src="https://github.com/user-attachments/assets/b17dc533-d736-4e97-a275-286363098098" />
<img width="940" height="497" alt="image" src="https://github.com/user-attachments/assets/520895bf-0a6a-4f1d-a328-9bf29035f936" />
<img width="940" height="497" alt="image" src="https://github.com/user-attachments/assets/8de39184-cc90-4045-9d28-167a7292bc68" />

## Result
The DHCP configuration was successfully implemented in Cisco Packet Tracer using a PT-Router, PT-Switch, and PC-PT devices. All connected PCs (PC0, PC1, and PC2) automatically received IP addresses from the router DHCP pool. The network connectivity was successfully verified.

## Conclusion
The DHCP server was successfully configured on the PT-Router in Cisco Packet Tracer. All client devices obtained IP addresses automatically, confirming that the DHCP configuration and network connectivity were working correctly. This project demonstrated how DHCP simplifies network configuration by automatically assigning IP addresses to client devices.

## Regards
Tejas Dodiya 
Cyber Security Student 
