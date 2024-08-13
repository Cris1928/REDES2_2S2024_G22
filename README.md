# REDES2_2S2024_G22


SWITCH0

SW0_G22# vtp domain practica1.usac.local
SW0_G22# vtp password redes2grupo22
SW0_G22# vtp mode server
SW0_G22# exit
copy running-config startup-config
SW0_G22# interface range Fa0/1 – 2
SW0_G22# switchport mode trunk
SW0_G22# exit
copy running-config startup-config
SW0_G22# show vlan brief
SW0_G22# vlan 14
SW0_G22# name Primaria
SW0_G22# vlan 24
SW0_G22# name Basicos
SW0_G22# vlan 34
SW0_G22# name Diversificado
SW0_G22# show vlan brief
copy running-config startup-config

------------------------------------------------------
SWITCH1

SW1_G22# vtp domain practica1.usac.local
SW1_G22# vtp password redes2grupo22
SW1_G22# vtp mode client
copy running-config startup-config
SW1_G22# interface range Fa0/1 – 3
SW1_G22# switchport mode trunk
SW1_G22# do write
SW1_G22# exit
copy running-config startup-config


------------------------------------------------------
SWITCH2

SW2_G22# vtp domain practica1.usac.local
SW2_G22# vtp password redes2grupo22
SW2_G22# vtp mode client
copy running-config startup-config
SW2_G22# interface range Fa0/1 – 3
SW2_G22# switchport mode trunk
SW2_G22# do write
SW2_G22# exit
copy running-config startup-config


------------------------------------------------------
SWITCH3

SW3_G22# vtp domain practica1.usac.local
SW3_G22# vtp password redes2grupo22
SW3_G22# vtp mode client
copy running-config startup-config
SW3_G22# interface range Fa0/1 – 4
SW3_G22# switchport mode trunk
SW3_G22# do write
SW3_G22# exit
copy running-config startup-config

------------------------------------------------------
SWITCH4

SW4_G22# vtp domain practica1.usac.local
SW4_G22# vtp password redes2grupo22
SW4_G22# vtp mode client
copy running-config startup-config
SW4_G22# interface range Fa0/1 – 9
SW4_G22# switchport mode trunk
SW4_G22# do write
SW4_G22# exit
copy running-config startup-config


------------------------------------------------------
SWITCH5

SW5_G22# vtp domain practica1.usac.local
SW5_G22# vtp password redes2grupo22
SW5_G22# vtp mode client
copy running-config startup-config
SW5_G22# interface range Fa0/1 – 4
SW5_G22# switchport mode trunk
SW5_G22# do write
SW5_G22# exit
copy running-config startup-config


------------------------------------------------------
SWITCH6

SW6_G22# vtp domain practica1.usac.local
SW6_G22# vtp password redes2grupo22
SW6_G22# vtp mode client
copy running-config startup-config
SW6_G22# interface range Fa0/1 – 2
SW6_G22# switchport mode trunk
SW6_G22# interface Fa0/3
SW6_G22# switchport mode access
SW6_G22# switchport acces vlan 14
SW6_G22# switchport mode trunk
SW6_G22# do write
SW6_G22# exit
copy running-config startup-config


------------------------------------------------------
SWITCH7

SW7_G22# vtp domain practica1.usac.local
SW7_G22# vtp password redes2grupo22
SW7_G22# vtp mode client
copy running-config startup-config
SW7_G22# interface range Fa0/1 – 2
SW7_G22# switchport mode trunk
SW7_G22# interface Fa0/3
SW7_G22# switchport mode access
SW7_G22# switchport acces vlan 14
SW7_G22# switchport mode trunk
SW7_G22# do write
SW7_G22# exit
copy running-config startup-config

------------------------------------------------------
SWITCH8

SW8_G22# vtp domain practica1.usac.local
SW8_G22# vtp password redes2grupo22
SW8_G22# vtp mode client
copy running-config startup-config
SW8_G22# interface Fa0/1
SW8_G22# switchport mode trunk
SW8_G22# interface Fa0/2
SW8_G22# switchport mode access
SW8_G22# switchport acces vlan 24
SW8_G22# switchport mode trunk
SW8_G22# do write
SW8_G22# exit
copy running-config startup-config

------------------------------------------------------
SWITCH9

SW9_G22# vtp domain practica1.usac.local
SW9_G22# vtp password redes2grupo22
SW9_G22# vtp mode client
copy running-config startup-config
SW9_G22# interface range Fa0/1-2
SW9_G22# switchport mode trunk
SW9_G22# interface Fa0/3
SW9_G22# switchport mode access
SW9_G22# switchport acces vlan 34
SW9_G22# switchport mode trunk
SW9_G22# do write
SW9_G22# exit
copy running-config startup-config


------------------------------------------------------
SWITCH10

SW10_G22# vtp domain practica1.usac.local
SW10_G22# vtp password redes2grupo22
SW10_G22# vtp mode client
copy running-config startup-config
SW10_G22# interface range Fa0/1-2
SW10_G22# switchport mode trunk
SW10_G22# interface Fa0/3
SW10_G22# switchport mode access
SW10_G22# switchport acces vlan 34
SW10_G22# switchport mode trunk
SW10_G22# do write
SW10_G22# exit
copy running-config startup-config
