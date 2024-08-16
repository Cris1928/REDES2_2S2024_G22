# PRACTICA 1

|Nombre|Carnet|
|:----|:----|
|Cristian Daniel Gómez Escobar |202107190|
|Jorge Sebastian Zamora Polanco |202002591|
|Roberto Carlos Gómez Donis |202000544|
|Gustavo Alejandro Girón Arriola |201900898|

## SWITCH0

```bash
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
```

## SWITCH1  

```bash
SW1_G22# vtp domain practica1.usac.local  
SW1_G22# vtp password redes2grupo22  
SW1_G22# vtp mode client  
copy running-config startup-config  
SW1_G22# interface range Fa0/1 – 3  
SW1_G22# switchport mode trunk  
SW1_G22# do write  
SW1_G22# exit  
copy running-config startup-config
```  

## SWITCH2  

```bash
SW2_G22# vtp domain practica1.usac.local  
SW2_G22# vtp password redes2grupo22  
SW2_G22# vtp mode client  
copy running-config startup-config  
SW2_G22# interface range Fa0/1 – 3  
SW2_G22# switchport mode trunk  
SW2_G22# do write  
SW2_G22# exit  
copy running-config startup-config
```  

## SWITCH3  

```bash
SW3_G22# vtp domain practica1.usac.local  
SW3_G22# vtp password redes2grupo22  
SW3_G22# vtp mode client  
copy running-config startup-config  
SW3_G22# interface range Fa0/1 – 4  
SW3_G22# switchport mode trunk  
SW3_G22# do write  
SW3_G22# exit  
copy running-config startup-config
```  

## SWITCH4  

```bash
SW4_G22# vtp domain practica1.usac.local  
SW4_G22# vtp password redes2grupo22  
SW4_G22# vtp mode client  
copy running-config startup-config  
SW4_G22# interface range Fa0/1 – 9  
SW4_G22# switchport mode trunk  
SW4_G22# do write  
SW4_G22# exit  
copy running-config startup-config
```  

## SWITCH5  

```bash
SW5_G22# vtp domain practica1.usac.local  
SW5_G22# vtp password redes2grupo22  
SW5_G22# vtp mode client  
copy running-config startup-config  
SW5_G22# interface range Fa0/1 – 4  
SW5_G22# switchport mode trunk  
SW5_G22# do write  
SW5_G22# exit  
copy running-config startup-config
```  

## SWITCH6  

```bash
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
```  

## SWITCH7  

```bash
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
```  

## SWITCH8

```bash
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
```

## SWITCH9

```bash
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
```

## SWITCH10

```bash
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
```

## Configuracion de STP

### Comandos

```bash
SW8_G22#Configure terminal
SW8_G22(config)#spanning-tree mode rapid-pvst
```

|Escenario|Protocolo Spanning-Tree|Red Primaria|Red Básicos|Red Diversificado|
|:----|:----|:----|:----|:----|
|1|PVST|00:28.15|00:55:42|00:55.48|
|2|Rapid PVST|0|00:01.93|00:23.56|

## Seguridad de interfaces de red

```bash
SW8_G22#Configure terminal
SW8_G22(config)#interface Fa0/2
SW8_G22(config)#switchport port-security
SW8_G22(config)#switchport port-security mac-address <numero_de_MACs>
```