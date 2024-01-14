## Switch Configuratie Headquarters

Hierbij de configuratie voor de coreswitch van headquarters:

```
Current configuration : 4720 bytes
!
version 16.3.2
service timestamps log datetime msec
service timestamps debug datetime msec
no service password-encryption
!
hostname SwitchHQ
!
!
enable secret 5 $1$mERr$hx5rVt7rPNoS4wqbXKX7m0
!
!
!
!
!
aaa new-model
!
aaa authentication login default local 
aaa authentication enable default enable 
!
!
!
!
!
!
!
no ip cef
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
no ip domain-lookup
ip domain-name ucll.local
!
!
spanning-tree mode rapid-pvst
!
!
!
!
!
!
interface GigabitEthernet1/0/1
 ip dhcp snooping trust
 switchport trunk native vlan 99
 switchport mode trunk
!
interface GigabitEthernet1/0/2
 switchport access vlan 10
 switchport mode access
 switchport nonegotiate
 switchport port-security
 switchport port-security mac-address sticky 
 switchport port-security violation restrict 
 switchport port-security mac-address sticky 0050.0F0C.73CA
!
interface GigabitEthernet1/0/3
 switchport access vlan 20
 switchport mode access
 switchport nonegotiate
 switchport port-security
 switchport port-security mac-address sticky 
 switchport port-security violation restrict 
!
interface GigabitEthernet1/0/4
 switchport access vlan 30
 switchport mode access
 switchport nonegotiate
 switchport port-security
 switchport port-security mac-address sticky 
 switchport port-security violation restrict 
!
interface GigabitEthernet1/0/5
 switchport access vlan 40
 switchport mode access
 switchport nonegotiate
 switchport port-security
 switchport port-security mac-address sticky 
 switchport port-security violation restrict 
 switchport port-security mac-address sticky 0050.0F0C.73CA
!
interface GigabitEthernet1/0/6
 switchport access vlan 50
 switchport mode access
 switchport nonegotiate
 switchport port-security
 switchport port-security mac-address sticky 
 switchport port-security violation restrict 
!
interface GigabitEthernet1/0/7
 switchport access vlan 60
 switchport mode access
 switchport nonegotiate
 switchport port-security
 switchport port-security mac-address sticky 
 switchport port-security violation restrict 
 switchport port-security mac-address sticky 0007.EC8D.D977
!
interface GigabitEthernet1/0/8
 switchport access vlan 70
 switchport mode access
 switchport nonegotiate
 switchport port-security
 switchport port-security mac-address sticky 
 switchport port-security violation restrict 
!
interface GigabitEthernet1/0/9
 switchport access vlan 80
 switchport mode access
 switchport nonegotiate
 switchport port-security
 switchport port-security mac-address sticky 
 switchport port-security violation restrict 
!
interface GigabitEthernet1/0/10
 switchport access vlan 90
 switchport mode access
 switchport nonegotiate
 switchport port-security
 switchport port-security mac-address sticky 
 switchport port-security violation restrict 
!
interface GigabitEthernet1/0/11
 switchport access vlan 100
 switchport mode access
 switchport nonegotiate
 switchport port-security
 switchport port-security mac-address sticky 
 switchport port-security violation restrict 
!
interface GigabitEthernet1/0/12
 switchport access vlan 110
 switchport mode access
 switchport nonegotiate
 switchport port-security
 switchport port-security mac-address sticky 
 switchport port-security violation restrict 
!
interface GigabitEthernet1/0/13
 switchport access vlan 120
 switchport mode access
 switchport nonegotiate
 switchport port-security
 switchport port-security mac-address sticky 
 switchport port-security violation restrict 
!
interface GigabitEthernet1/0/14
 switchport access vlan 130
 switchport mode access
 switchport nonegotiate
 switchport port-security
 switchport port-security mac-address sticky 
 switchport port-security violation restrict 
!
interface GigabitEthernet1/0/15
 shutdown
!
interface GigabitEthernet1/0/16
 shutdown
!
interface GigabitEthernet1/0/17
 shutdown
!
interface GigabitEthernet1/0/18
 shutdown
!
interface GigabitEthernet1/0/19
 shutdown
!
interface GigabitEthernet1/0/20
 shutdown
!
interface GigabitEthernet1/0/21
 shutdown
!
interface GigabitEthernet1/0/22
 shutdown
!
interface GigabitEthernet1/0/23
 shutdown
!
interface GigabitEthernet1/0/24
 shutdown
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
 mac-address 000b.becd.b501
 ip address 192.168.40.253 255.255.255.0
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
 transport input ssh
line vty 5 15
 transport input ssh
!
!
!
!
end
```