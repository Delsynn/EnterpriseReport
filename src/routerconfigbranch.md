## Router Configuratie Branch Office

Hierbij de configuratie voor de router van het branch office:

```
Current configuration : 2753 bytes
!
version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname RouterBranch
!
login on-success log
!
!
enable secret 5 $1$w5Ir$502DVRxTCk7lspVXxPK7M0
!
ip dhcp relay information trust-all
!
!
ip dhcp excluded-address 192.168.140.1 192.168.140.10
ip dhcp excluded-address 192.168.140.255
ip dhcp excluded-address 192.168.150.1 192.168.150.10
ip dhcp excluded-address 192.168.150.255
!
ip dhcp pool RD
 network 192.168.140.0 255.255.255.0
 default-router 192.168.140.1
 dns-server 8.8.8.8
ip dhcp pool BEZOEKERS
 network 192.168.150.0 255.255.255.0
 default-router 192.168.150.1
 dns-server 8.8.8.8
!
!
!
ip cef
no ipv6 cef
!
!
!
username admin secret 5 $1$SvZ5$3KCgARMYaHCkPeQxuPbL11
!
!
license udi pid CISCO2901/K9 sn FTX15243NQL-
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
 no ip address
 duplex auto
 speed auto
 shutdown
!
interface GigabitEthernet0/1
 no ip address
 ip nat inside
 duplex auto
 speed auto
!
interface GigabitEthernet0/1.140
 encapsulation dot1Q 140
 ip address 192.168.140.1 255.255.255.0
 ip nat inside
!
interface GigabitEthernet0/1.150
 encapsulation dot1Q 150
 ip address 192.168.150.1 255.255.255.0
 ip nat inside
!
interface GigabitEthernet0/1.160
 encapsulation dot1Q 160
 ip address 192.168.160.1 255.255.255.0
 ip nat inside
!
interface GigabitEthernet0/1.170
 encapsulation dot1Q 170
 ip address 192.168.170.1 255.255.255.0
 ip nat inside
!
interface GigabitEthernet0/1.180
 encapsulation dot1Q 180
 ip address 192.168.180.1 255.255.255.0
 ip nat inside
!
interface GigabitEthernet0/1.190
 encapsulation dot1Q 190
 ip address 192.168.190.1 255.255.255.0
 ip nat inside
!
interface GigabitEthernet0/1.200
 encapsulation dot1Q 200
 ip address 192.168.200.1 255.255.255.0
 ip nat inside
!
interface Serial0/0/0
 ip address 10.0.1.2 255.255.255.252
 ip nat inside
 clock rate 2000000
!
interface Serial0/0/1
 ip address 10.0.3.1 255.255.255.252
 ip nat inside
!
interface Vlan1
 no ip address
 shutdown
!
router ospf 1
 router-id 2.2.2.2
 log-adjacency-changes
 network 10.0.1.0 0.0.0.3 area 0
 network 192.168.140.0 0.0.0.255 area 0
 network 192.168.150.0 0.0.0.255 area 0
 network 192.168.160.0 0.0.0.255 area 0
 network 192.168.170.0 0.0.0.255 area 0
 network 192.168.180.0 0.0.0.255 area 0
 network 192.168.190.0 0.0.0.255 area 0
 network 192.168.200.0 0.0.0.255 area 0
 network 10.0.3.0 0.0.0.3 area 0
!
ip classless
ip route 0.0.0.0 0.0.0.0 10.0.1.1 
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
 login
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
end
```
