## Router Configuratie Headquarters

Hierbij de configuratie voor de router van headquarters:

```
Current configuration : 4913 bytes
!
version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname RouterHQ
!
login on-success log
!
!
enable secret 5 $1$gNAX$zEFZKA2/m.d9cZ8aE/.UP0
!
ip dhcp relay information trust-all
!
!
ip dhcp excluded-address 192.168.10.1 192.168.10.10
ip dhcp excluded-address 192.168.10.255
ip dhcp excluded-address 192.168.20.1 192.168.20.10
ip dhcp excluded-address 192.168.20.255
ip dhcp excluded-address 192.168.30.1 192.168.30.10
ip dhcp excluded-address 192.168.30.255
ip dhcp excluded-address 192.168.40.1 192.168.40.10
ip dhcp excluded-address 192.168.40.255
ip dhcp excluded-address 192.168.50.1 192.168.50.10
ip dhcp excluded-address 192.168.50.255
ip dhcp excluded-address 192.168.60.1 192.168.60.10
ip dhcp excluded-address 192.168.60.255
ip dhcp excluded-address 192.168.70.1 192.168.70.10
ip dhcp excluded-address 192.168.70.255
ip dhcp excluded-address 192.168.80.1 192.168.80.10
ip dhcp excluded-address 192.168.80.255
!
ip dhcp pool SALES
 network 192.168.10.0 255.255.255.0
 default-router 192.168.10.1
 dns-server 8.8.8.8
ip dhcp pool ACCOUNTING
 network 192.168.20.0 255.255.255.0
 default-router 192.168.20.1
 dns-server 8.8.8.8
ip dhcp pool FACILITEITEN
 network 192.168.30.0 255.255.255.0
 default-router 192.168.30.1
 dns-server 8.8.8.8
ip dhcp pool IT
 network 192.168.40.0 255.255.255.0
 default-router 192.168.40.1
 dns-server 8.8.8.8
ip dhcp pool MARKETING
 network 192.168.50.0 255.255.255.0
 default-router 192.168.50.1
 dns-server 8.8.8.8
ip dhcp pool CUSTOMER_SUPPORT
 network 192.168.60.0 255.255.255.0
 default-router 192.168.60.1
 dns-server 8.8.8.8
ip dhcp pool CUSTOMER_SUCCESS
 network 192.168.70.0 255.255.255.0
 default-router 192.168.70.1
 dns-server 8.8.8.8
ip dhcp pool BEZOEKERS
 network 192.168.80.0 255.255.255.0
 default-router 192.168.80.1
 dns-server 8.8.8.8
!
!
aaa new-model
!
!
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
username admin secret 5 $1$QBGN$/WrJsjy2wDc./vUYXbKDI.
!
!
license udi pid CISCO2901/K9 sn FTX1524F4G4-
!
!
!
!
!
!
!
!
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
interface GigabitEthernet0/0
 ip address 193.190.120.57 255.255.255.224
 ip nat outside
 duplex auto
 speed auto
!
interface GigabitEthernet0/1
 no ip address
 ip nat inside
 duplex auto
 speed auto
!
interface GigabitEthernet0/1.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0
 ip nat inside
!
interface GigabitEthernet0/1.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0
 ip nat inside
!
interface GigabitEthernet0/1.30
 encapsulation dot1Q 30
 ip address 192.168.30.1 255.255.255.0
!
interface GigabitEthernet0/1.40
 encapsulation dot1Q 40
 ip address 192.168.40.1 255.255.255.0
 ip nat inside
!
interface GigabitEthernet0/1.50
 encapsulation dot1Q 50
 ip address 192.168.50.1 255.255.255.0
 ip nat inside
!
interface GigabitEthernet0/1.60
 encapsulation dot1Q 60
 ip address 192.168.60.1 255.255.255.0
 ip nat inside
!
interface GigabitEthernet0/1.70
 encapsulation dot1Q 70
 ip address 192.168.70.1 255.255.255.0
 ip nat inside
!
interface GigabitEthernet0/1.80
 encapsulation dot1Q 80
 ip address 192.168.80.1 255.255.255.0
 ip nat inside
!
interface GigabitEthernet0/1.90
 encapsulation dot1Q 90
 ip address 192.168.90.1 255.255.255.0
 ip nat inside
!
interface GigabitEthernet0/1.100
 encapsulation dot1Q 100
 ip address 192.168.100.1 255.255.255.0
 ip nat inside
!
interface GigabitEthernet0/1.110
 encapsulation dot1Q 110
 ip address 192.168.110.1 255.255.255.0
 ip nat inside
!
interface GigabitEthernet0/1.120
 encapsulation dot1Q 120
 ip address 192.168.120.1 255.255.255.0
 ip nat inside
!
interface GigabitEthernet0/1.130
 encapsulation dot1Q 130
 ip address 192.168.130.1 255.255.255.0
 ip nat inside
!
interface Serial0/0/0
 ip address 10.0.1.1 255.255.255.252
 ip nat inside
!
interface Serial0/0/1
 ip address 10.0.2.1 255.255.255.252
 ip nat inside
!
interface Vlan1
 no ip address
 shutdown
!
router ospf 1
 router-id 1.1.1.1
 log-adjacency-changes
 passive-interface GigabitEthernet0/1
 network 10.0.1.0 0.0.0.3 area 0
 network 10.0.2.0 0.0.0.3 area 0
 network 192.168.10.0 0.0.0.255 area 0
 network 192.168.20.0 0.0.0.255 area 0
 network 192.168.30.0 0.0.0.255 area 0
 network 192.168.40.0 0.0.0.255 area 0
 network 192.168.50.0 0.0.0.255 area 0
 network 192.168.60.0 0.0.0.255 area 0
 network 192.168.70.0 0.0.0.255 area 0
 network 192.168.80.0 0.0.0.255 area 0
 network 192.168.90.0 0.0.0.255 area 0
 network 192.168.100.0 0.0.0.255 area 0
 network 192.168.110.0 0.0.0.255 area 0
 network 192.168.120.0 0.0.0.255 area 0
 network 192.168.130.0 0.0.0.255 area 0
!
ip nat inside source list 1 interface GigabitEthernet0/0 overload
ip classless
ip route 0.0.0.0 0.0.0.0 193.190.120.62 
!
ip flow-export version 9
!
!
access-list 1 permit any
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
end
```
