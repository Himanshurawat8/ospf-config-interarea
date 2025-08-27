# ospf-config-interarea
R0

Fa0/0 (to PC0): 10.0.0.1/24

Fa0/1 (to R1): 30.0.0.1/24

R1

Fa0/0 (to R0): 30.0.0.2/24

Fa0/1 (to R2): 40.0.0.1/24

R2

Fa0/0 (to R1): 40.0.0.2/24

Fa0/1 (to R3): 50.0.0.1/24

R3

Fa0/1 (to R2): 50.0.0.2/24

Fa0/0 (to PC1): 20.0.0.1/24


enable
configure terminal
hostname R0

interface FastEthernet0/0
 ip address 10.0.0.1 255.255.255.0
 no shutdown
!
interface FastEthernet0/1
 ip address 30.0.0.1 255.255.255.0
 no shutdown
!
router ospf 1
 router-id 1.1.1.1
 network 10.0.0.0 0.0.0.255 area 2
 network 30.0.0.0 0.0.0.255 area 2
 passive-interface FastEthernet0/0
exit
copy running-config startup-config

enable
configure terminal
hostname R0

interface FastEthernet0/0
 ip address 10.0.0.1 255.255.255.0
 no shutdown
!
interface FastEthernet0/1
 ip address 30.0.0.1 255.255.255.0
 no shutdown
!
router ospf 1
 router-id 1.1.1.1
 network 10.0.0.0 0.0.0.255 area 2
 network 30.0.0.0 0.0.0.255 area 2
 passive-interface FastEthernet0/0
exit
copy running-config startup-config


enable
configure terminal
hostname R1

interface FastEthernet0/0
 ip address 30.0.0.2 255.255.255.0
 no shutdown
!
interface FastEthernet0/1
 ip address 40.0.0.1 255.255.255.0
 no shutdown
!
router ospf 1
 router-id 2.2.2.2
 network 30.0.0.0 0.0.0.255 area 2
 network 40.0.0.0 0.0.0.255 area 0
exit
copy running-config startup-config


enable
configure terminal
hostname R2

interface FastEthernet0/0
 ip address 40.0.0.2 255.255.255.0
 no shutdown
!
interface FastEthernet0/1
 ip address 50.0.0.1 255.255.255.0
 no shutdown
!
router ospf 1
 router-id 3.3.3.3
 network 40.0.0.0 0.0.0.255 area 0
 network 50.0.0.0 0.0.0.255 area 1
exit
copy running-config startup-config


enable
configure terminal
hostname R3

interface FastEthernet0/1
 ip address 50.0.0.2 255.255.255.0
 no shutdown
!
interface FastEthernet0/0
 ip address 20.0.0.1 255.255.255.0
 no shutdown
!
router ospf 1
 router-id 4.4.4.4
 network 50.0.0.0 0.0.0.255 area 1
 network 20.0.0.0 0.0.0.255 area 1
 passive-interface FastEthernet0/0
exit
copy running-config startup-config


3) PC configuration (Packet Tracer GUI)

PC0: IP 10.0.0.2, Mask 255.255.255.0, Gateway 10.0.0.1

PC1: IP 20.0.0.2, Mask 255.255.255.0, Gateway 20.0.0.1
\
