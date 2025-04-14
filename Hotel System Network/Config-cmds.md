## FL-1 ROUTER

### Initial setup
`enable` <br>
`configure terminal` <br>
`hostname` FL-1_Router <br>
`no ip domain-lookup` <br>
`enable secret` Floor!-Router

### Configuring SSH keys for remote login
`ip domain-name` hotel-design.com <br>
`crypto key generate rsa` <br>
1024 <br>
`username` Fl1-Admin `secret` Adm!n-7ES7

### Configuring and securing the lines
`line console` 0 <br>
`password` HO73L-D35!GN <br>
`login`
<br>

`line vty` 0 15 <br>
`password` D35!GN-HO73L <br>
`transport input` ssh <br>
`login local` <br>
`exit`
<br>

`ip ssh version` 2 <br>
`service password-encryption` <br>
`banner motd` #Unauthorised Access is Prohibited and Prosecutable#

### Configuring the serial interfaces (Interfaces connecting the routers)
`Interface` s0/0/0 <br>
`description` Link to Floor-2 <br>
`ip address` 10.10.10.1 255.255.255.252 <br>
`no shutdown`
<br>

`interface` s0/0/1 <br>
`description` Link to Floor-3 <br>
`ip address` 10.10.10.5 255.255.255.252 <br>
`no shutdown` <br>
`exit`

### Configuring the VLAN interfaces on the router
`interface` g0/0.80 <br>
`description` The Reception VLAN 80 Gateway Interface <br>
`encapsulation dot1Q` 80 <br>
`ip address` 192.168.8.1 255.255.255.0
<br>

`interface` g0/0.70 <br>
`description` The Store VLAN 70 Gateway Interface <br>
`encapsulation dot1Q` 70 <br>
`ip address` 192.168.7.1 255.255.255.0
<br>

`interface` g0/0.60 <br>
`description` The Logistics VLAN 60 Gateway Interface <br>
`encapsulation dot1Q` 60 <br>
`ip address` 192.168.6.1 255.255.255.0
<br>

`interface` g0/0 <br>
`no shutdown` <br>
`exit`

### Configuring OSPF to advertise its routes
`router ospf` 1 <br>
`network` 10.10.10.0 0.0.0.3 `area` 0 <br>
`network` 10.10.10.4 0.0.0.3 `area` 0 <br>
`network` 192.168.8.0 0.0.0.255 `area` 0 <br>
`network` 192.168.7.0 0.0.0.255 `area` 0 <br>
`network` 192.168.6.0 0.0.0.255 `area` 0 <br>
`exit`

### Configuring DHCP pools for the VLANs on the router
`ip dhcp excluded-address` 192.168.8.1 <br>
`ip dhcp excluded-address` 192.168.7.1 <br>
`ip dhcp excluded-address` 192.168.6.1
<br>

`ip dhcp pool` VL80-Reception <br>
`network` 192.168.8.0 255.255.255.0 <br>
`default-router` 192.168.8.1
<br>

`ip dhcp pool` VL70-Store <br>
`network` 192.168.7.0 255.255.255.0 <br>
`default-router` 192.168.7.1
<br>

`ip dhcp pool` VL60-Logistics <br>
`network` 192.168.6.0 255.255.255.0 <br>
`default-router` 192.168.6.1

### To save your work
`copy running-config startup-config`

### To verify your interface configurations
`show ip interface brief` <br>
`show running-config`

### To verify your OSPF configurations
`show ip ospf` <br>
`show ip route ospf
`
### To verify your DHCP configurations
`show ip dhcp pool`<br>
`show ip dhcp binding`
<br><br><br><br><br><br><br><br><br><br>





## FL-2 ROUTER

### Initial setup
`enable` <br>
`configure terminal` <br>
`hostname` FL-2_Router <br>
`no ip domain-lookup`
`enable secret` Floor#-Router

### Configuring SSH keys for remote login
`ip domain-name` hotel-design.com <br>
`crypto key generate rsa`<br>
1024 <br>
`username` Fl2-Admin `secret` Adm!n-T35T

### configuring and securing the lines
`line console` 0 <br>
`password` HO73L-D35!GN <br>
`login` <br>
`line vty` 0 15 <br>
`password` D35!GN-HO73L <br>
`transport` input ssh <br>
`login local` <br>
`exit`
<br>

`ip ssh version` 2 <br>
`service password-encryption`
`banner motd` #Unauthorised Access is Prohibited and Prosecutable#

### Configuring the serial interfaces (Interfaces connecting the routers)
`interface` s0/0/0 <br>
`description` Link to Floor-1 <br>
`ip address` 10.10.10.2 255.255.255.252 <br>
`no shutdown`
<br>

`interface` s0/0/1 <br>
`description` Link to Floor-3 <br>
`ip address` 10.10.10.9 255.255.255.252 <br>
`no shutdown` <br>
`exit`

### Configuring the VLAN interfaces on the router
`interface` g0/0.50 <br>
`description` The Finance VLAN 50 Gateway Interface <br>
`encapsulation` dot1Q 50 <br>
`ip address` 192.168.5.1 255.255.255.0
<br>

`interface` g0/0.40 <br>
`description` The HR VLAN 40 Gateway Interface <br>
`encapsulation dot1Q` 40 <br>
`ip address` 192.168.4.1 255.255.255.0
<br>

`interface` g0/0.30 <br>
`description` The Sales VLAN 30 Gateway Interface <br>
`encapsulation dot1Q` 30 <br>
`ip address` 192.168.3.1 255.255.255.0
<br>

`interface` g0/0 <br>
`no shutdown` <br>
`exit`

### Configuring OSPF to advertise its routes
`router ospf` 1 <br>
`network` 10.10.10.0 0.0.0.3 `area` 0 <br>
`network` 10.10.10.8 0.0.0.3 `area` 0 <br>
`network` 192.168.3.0 0.0.0.255 `area` 0 <br>
`network` 192.168.4.0 0.0.0.255 `area` 0 <br>
`network` 192.168.5.0 0.0.0.255 `area` 0 <br>
`exit`

### Configuring DHCP pools for the VLANs on the router
`ip dhcp excluded-address` 192.168.5.1 <br>
`ip dhcp excluded-address` 192.168.4.1 <br>
`ip dhcp excluded-address` 192.168.3.1
<br>

`ip dhcp pool` VL50-Finance <br>
`network` 192.168.5.0 255.255.255.0 <br>
`default-router` 192.168.5.1
<br>

`ip dhcp pool` VL40-HR <br>
`network` 192.168.4.0 255.255.255.0 <br>
`default-router` 192.168.4.1
<br>

`ip dhcp pool` VL30-Sales <br>
`network` 192.168.3.0 255.255.255.0 <br>
`default-router` 192.168.3.1

### To save your work
`copy running-config startup-config`

### To verify your interface configurations
`show ip interface brief` <br>
`show running-config`

### To verify your OSPF configurations
`show ip ospf` <br>
`show ip route ospf`

### To verify your DHCP configurations
`show ip dhcp pool` <br>
`show ip dhcp binding`
<br><br><br><br><br><br><br><br><br><br>




## FL-3 ROUTER

### Initial setup
`enable` <br>
`configure terminal` <br>
`hostname` FL-3_Router <br>
`no ip domain-lookup` <br>
`enable secret` Floor$-Router

### Configuring SSH keys for remote login
`ip domain-name` hotel-design.com <br>
`crypto key generate rsa` <br>
1024 <br>
`username` Fl3-Admin `secret` Adm!n-7E5T

### Configuring and securing the lines
`line console` 0 <br>
`password` HO73L-D35!GN <br>
`login`
<br>

`line vty` 0 15 <br>
`password` D35!GN-HO73L <br>
`transport input` ssh <br>
`login local` <br>
`exit`
<br>

`ip ssh version` 2 <br>
`service password-encryption` <br>
`banner motd` #Unauthorised Access is Prohibited and Prosecutable#

### Configuring the serial interfaces (Interfaces connecting the routers)
`interface` s0/1/0 <br>
`description` Link to Floor-1 <br>
`ip address` 10.10.10.6 255.255.255.252 <br>
`no shutdown`
<br>

`interface` s0/1/1 <br>
`description` Link to Floor-3 <br>
`ip address` 10.10.10.10 255.255.255.252 <br>
`no shutdown` <br>
`exit`

### Configuring the VLAN interfaces on the router
`interface` g0/0.20 <br>
`description` The Admin VLAN 20 Gateway Interface <br>
`encapsulation dot1Q` 20 <br>
`ip address` 192.168.2.1 255.255.255.0
<br>

`interface` g0/0.10 <br>
`description` The IT VLAN 10 Gateway Interface <br>
`encapsulation dot1Q` 10 <br>
`ip address` 192.168.1.1 255.255.255.0
<br>

`interface` g0/0 <br>
`no shutdown` <br>
`exit`

### Configuring OSPF to advertise its routes
`router ospf` 1 <br>
`network` 10.10.10.4 0.0.0.3 `area` 0 <br>
`network` 10.10.10.8 0.0.0.3 `area` 0 <br>
`network` 192.168.1.0 0.0.0.255 `area` 0 <br>
`network` 192.168.2.0 0.0.0.255 `area` 0 <br>
`exit`

### Configuring DHCP pools for the VLANs on the router
`ip dhcp excluded-address` 192.168.2.1 <br>
`ip dhcp excluded-address` 192.168.1.1
<br>

`ip dhcp pool` VL20-Admin <br>
`network` 192.168.2.0 255.255.255.0 <br>
`default-router` 192.168.2.1
<br>

`ip dhcp pool` VL10-IT <br>
`network` 192.168.1.0 255.255.255.0 <br>
`default-router` 192.168.1.1

### To save your work
`copy running-config startup-config`

### To verify your interface configurations
`show ip interface brief` <br>
`show running-config`

### To verify your OSPF configurations
`show ip ospf` <br>
`show ip route ospf`

### To verify your DHCP configurations
`show ip dhcp pool` <br>
`show ip dhcp binding`
<br><br><br><br><br><br><br><br><br><br>





## FL-1 SWITCH

### Initial setup
`enable` <br>
`configure terminal` <br>
`hostname` FL-1_SW <br>
`no ip domain-lookup` <br>
`enable secret` Floor!-Switch

### Configuring and securing the lines
`line console` 0 <br>
`password` HO73L-N37W0RK <br>
`login`
<br>

`line vty` 0 15 <br>
`password` N37W0RK-HO73L <br>
`login` <br>
`exit`
<br>

`service password-encryption` <br>
`banner motd` #Unauthorised Access is Prohibited and Prosecutable#

### Setting up the VLANs
`vlan` 80 <br>
`name` Reception <br>
`vlan` 70 <br>
`name` Store <br>
`vlan` 60 <br>
`name` Logistics <br>
`vlan` 101 <br>
`name` Native

### Configuring the VLAN access ports
`interface range` fa0/1, fa0/2, fa0/24 <br>
`switchport mode access` <br>
`switchport access vlan` 80
<br>

`interface range` fa0/3, fa0/23 <br>
`switchport mode access` <br>
`switchport access vlan` 70
<br>

`interface range` fa0/4, fa0/22 <br>
`switchport mode access` <br>
`switchport access vlan` 60
<br>

### Configuring trunking
`interface` g0/1 <br>
`switchport mode trunk` <br>
`switchport trunk native vlan` 101 <br>
`switchport trunk allowed vlan` 80,70,60,101

### To save your work
`copy running-config startup-config`

### To verify your VLAN configurations
`show vlan brief` <br>
`show interfaces vlan` <br>
`show interfaces switchport` <br>
`show running-config`
<br><br><br><br><br><br><br><br><br><br>




## FL-2 SWITCH

### Initial setup
`enable` <br>
`configure terminal` <br>
`hostname` FL-2_SW <br>
`no ip domain-lookup` <br>
`enable secret` Floor#-Switch

### configuring and securing the lines
`line console` 0 <br>
`password` HO73L-N37W0RK <br>
`login`
<br>

`line vty` 0 15 <br>
`password` N37W0RK-HO73L <br>
`login` <br>
`exit`
<br>

`service password-encryption` <br>
`banner motd` #Unauthorised Access is Prohibited and Prosecutable#

### Setting up the VLANs
`vlan` 50 <br>
`name` Finance <br>
`vlan` 40 <br>
`name` HR <br>
`vlan` 30 <br>
`name` Sales <br>
`vlan` 101 <br>
`name` Native

### Configuring the VLAN access ports
`interface range` fa0/2, fa0/24 <br>
`switchport mode access` <br>
`switchport access vlan` 50
<br>

`interface range` fa0/1, fa0/3, fa0/23 <br>
`switchport mode access` <br>
`switchport access vlan` 40
<br>

`interface range` fa0/4, fa0/22 <br>
`switchport mode access` <br>
`switchport access vlan` 30

### Configuring trunking
`interface` g0/1 <br>
`switchport mode trunk` <br>
`switchport trunk native vlan` 101 <br>
`switchport trunk allowed vlan` 50,40,30,101

### To verify your VLAN configurations
`show vlan brief` <br>
`show interfaces vlan` <br>
`show interfaces switchport` <br>
`show running-config`





## FL-3 SWITCH

### Initial setup
`enable` <br>
`configure terminal` <br>
`hostname` FL-3_SW <br>
`no ip domain-lookup` <br>
`enable secret` Floor$-Switch

### Configuring and securing the lines
`line console` 0 <br>
`password` HO73L-N37W0RK <br>
`login`
<br>

`line vty` 0 15 <br>
`password` N37W0RK-HO73L <br>
`login` <br>
`exit`
<br>

`service password-encryption` <br>
`banner motd` #Unauthorised Access is Prohibited and Prosecutable#

### Setting up the VLANs
`vlan` 20 <br>
`name` Admin <br>
`vlan` 10 <br>
`name` IT <br>
`vlan` 101 <br>
`name` Native <br>
`exit`

### Configuring the VLAN access ports
`interface range` fa0/2, fa0/24 <br>
`switchport mode access` <br>
`switchport access vlan` 20
<br>

`interface range` fa0/1, fa0/3, fa0/23 <br>
`switchport mode access` <br>
`switchport access` vlan 10

### Configuring trunking
`interface` g0/1 <br>
`switchport mode trunk` <br>
`switchport trunk native vlan` 101 <br>
`switchport trunk allowed` vlan 10,20,101 <br>
`exit`

### Configuring port-security for Test-PC
`interface` fa0/1 <br>
`switchport mode access` <br>
`switchport port security` <br>
`switchport port security mac address` sticky <br>
`switchport port security violation` shutdown <br>
`exit`

### To verify your VLAN configurations
`show vlan brief` <br>
`show interfaces vlan` <br>
`show interfaces switchport` <br>
`show running-config` <br>
