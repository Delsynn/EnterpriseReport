## Switch Configuratie Headquarters

Hierbij de configuratie voor de coreswitch van headquarters:

```
Current configuration : 4912 bytes
!
version 16.3.2
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname CoreSwitchHQ
!
!
enable secret 5 $1$mERr$hx5rVt7rPNoS4wqbXKX7m0
!
!
!
!
!
!
ip cef
no ipv6 cef
!
!
!
username admin secret 5 $1$mERr$hx5rVt7rPNoS4wqbXKX7m0
!
!
!
!
!
!
!
!
!
ip dhcp snooping
!
ip ssh version 2
ip domain-name ucll.local
!
!
spanning-tree mode pvst
!
!
!
!
!
!
interface GigabitEthernet1/0/1
 ip dhcp snooping trust
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,100,110,120,130
 switchport mode trunk
!
interface GigabitEthernet1/0/2
 ip dhcp snooping trust
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,100,110,120,130
 switchport mode trunk
!
interface GigabitEthernet1/0/3
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,100,110,120,130
 switchport mode trunk
!
interface GigabitEthernet1/0/4
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,100,110,120,130
 switchport mode trunk
!
interface GigabitEthernet1/0/5
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,100,110,120,130
 switchport mode trunk
!
interface GigabitEthernet1/0/6
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,100,110,120,130
 switchport mode trunk
!
interface GigabitEthernet1/0/7
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,100,110,120,130
 switchport mode trunk
!
interface GigabitEthernet1/0/8
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,100,110,120,130
 switchport mode trunk
!
interface GigabitEthernet1/0/9
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,100,110,120,130
 switchport mode trunk
!
interface GigabitEthernet1/0/10
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,100,110,120,130
 switchport mode trunk
!
interface GigabitEthernet1/0/11
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,100,110,120,130
 switchport mode trunk
!
interface GigabitEthernet1/0/12
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,100,110,120,130
 switchport mode trunk
!
interface GigabitEthernet1/0/13
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,100,110,120,130
 switchport mode trunk
!
interface GigabitEthernet1/0/14
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,100,110,120,130
 switchport mode trunk
!
interface GigabitEthernet1/0/15
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,100,110,120,130
 switchport mode trunk
!
interface GigabitEthernet1/0/16
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,100,110,120,130
 switchport mode trunk
!
interface GigabitEthernet1/0/17
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,100,110,120,130
 switchport mode trunk
!
interface GigabitEthernet1/0/18
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,100,110,120,130
 switchport mode trunk
!
interface GigabitEthernet1/0/19
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,100,110,120,130
 switchport mode trunk
!
interface GigabitEthernet1/0/20
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,100,110,120,130
 switchport mode trunk
!
interface GigabitEthernet1/0/21
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,100,110,120,130
 switchport mode trunk
!
interface GigabitEthernet1/0/22
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,100,110,120,130
 switchport mode trunk
!
interface GigabitEthernet1/0/23
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,100,110,120,130
 switchport mode trunk
!
interface GigabitEthernet1/0/24
 switchport trunk native vlan 99
 switchport trunk allowed vlan 10,20,30,40,50,60,70,80,90,100,110,120,130
 switchport mode trunk
!
interface GigabitEthernet1/1/1
 shutdown
!
interface GigabitEthernet1/1/2
 shutdown
!
interface GigabitEthernet1/1/3
 shutdown
!
interface GigabitEthernet1/1/4
 shutdown
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan40
 description IT VLAN FOR SSH
 mac-address 000b.be9e.5001
 ip address 192.168.40.254 255.255.255.0
!
ip classless
!
ip flow-export version 9
!
!
!
!
!
!
!
line con 0
!
line aux 0
!
line vty 0 4
 login local
 transport input ssh
line vty 5 15
 login local
 transport input ssh
!
!
!
!
end
```