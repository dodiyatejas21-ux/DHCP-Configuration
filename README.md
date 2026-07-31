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
# Image reference from word file with diagram reference No1
<img width="1535" height="812" alt="Screenshot 2026-07-30 180925" src="https://github.com/user-attachments/assets/a58d3687-5e63-4710-a178-82c4ef47239c" />

 ## Step 2: Open the PT-Router
* Click on the PT-Router in the Cisco Packet Tracer workspace.
* Open the **CLI (Command Line Interface)** tab.
* Press **Enter** to access the router command prompt.
* The router is now ready for DHCP configuration commands.
# Image referece from word file with diagram reference No2&3
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

## Step 5: Create a DHCP Pool
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


