# networking-IT_lab
my learning habits

Mission 008 – Port Security & Sticky MAC

First, understand what we're doing
Imagine you have a network switch with several ports.
- Port Fa0/1 – Computer A
- Port Fa0/2 – Computer B
- Port Fa0/3 – Computer C
You want Fa0/3 to accept only the authorized device.

What is a MAC address?

A MAC address is a unique hardware identifier assigned to a network interface.

Example:

00:1A:2B:3C:4D:5E

Sticky MAC means the switch automatically learns the MAC address of the device connected to that port and saves it in its running configuration.

If another device is connected later, the switch can detect the unauthorized MAC address and take action.

- Switch name: Switch1
- Interface: FastEthernet 0/3
- Enable port security
- Enable sticky MAC learning
Open the Switch1 CLI.
Step 1 – Enter privileged EXEC mode
Type:
enable


Your prompt should change from:
Switch1>


to:
Switch1#


What happened? You entered privileged EXEC mode, where you can access administrative commands.
Step 2 – Enter global configuration mode
Type:
configure terminal


Your prompt should become:
Switch1(config)#


What happened? You're now allowed to modify the switch configuration.
Step 3 – Select the correct port
Type:
interface fastethernet 0/3


Your prompt should become:
Switch1(config-if)#


What happened? You're configuring only interface FastEthernet 0/3.
Step 4 – Enable Port Security
Type:
switchport port-security


This enables port security on that interface.
Step 5 – Enable Sticky MAC
Type:
switchport port-security mac-address sticky


Mission commands completed
Your configuration should look like this:

Your real-world IT knowledge
One important detail: Sticky MAC addresses are initially stored in the running configuration. To retain them after a switch restart, you must save the configuration using:
copy running-config startup-config


Also, if another device connects and violates the security policy, the port can be shut down depending on its violation mode. 
Feature History for MAC [Support]+1

system protocol

port speed and duplex configuration (tuning)

enable
conf t
int fa 0//7
duplex full
speed 100

end

VIRTUAL LOCAL AREA NETWORK SEGMENTATION

enable
conf t
vlan 10
name ACCOUNTING
end

enable

Step 2 – Enter configuration mode
configure terminal

Step 3 – Select port Fa0/5
interface fastethernet 0/5

Step 4 – Set the port as an access port
switchport mode access

Why? Because this port connects to an end-user device, such as an accounting workstation.

Step 5 – Assign VLAN 10
switchport access vlan 10

enable
configure terminal
interface fastethernet 0/5
switchport mode access
switchport access vlan 10
end
show vlan brief

end


