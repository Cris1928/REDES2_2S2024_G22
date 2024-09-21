![image](https://github.com/user-attachments/assets/11995ed9-1bb7-47ea-9fb1-2750c3fd824b)


# MANUAL TECNICO | PRACTICA 2
## Topología implementada
![image](https://github.com/user-attachments/assets/04239df2-d98e-429d-b083-67accd2421ff)
## Configuración de Ip

Existen 8 redes dentro de la topología con una ip determinada con la siguientes direcciones en la tabla:

| Red          | Vlan    | Edificio | 
| ------------ | ------------ | ----------------- |
| 192.168.14.0 /24  | RECURSOS  | M2 
| 192.168.24.0 /24  | VISITANTES | M2
| 192.168.34.0 /24  | RECURSOS | T3   
| 192.168.44.0 /24  | SOPORTE |T3 |
| 192.168.54.0 /24  | RECURSOS  | T9 
| 192.168.64.0 /24  | VISITANTES | T9 
| 192.168.74.0 /24  | RECURSOS  | BIBLIOTECA 
| 192.168.84.0 /24  | VISITANTES | BIBLIOTECA 
| 192.168.50.2 | --- | M2 -> T3
| 192.168.60.1  | --- | T9  -> T3
| 192.168.70.1  | --- | BIBLIOTECA -> T3 

## M2 - RECURSOS  
![image](https://github.com/user-attachments/assets/5948eb67-fcb3-46ec-8caf-a500917e2ce0)
## M2 - VISITANTES
![image](https://github.com/user-attachments/assets/98570647-b7f1-4a46-a69e-2d22ce552edb)
## BIBLIOTECA CENTRAL - RECURSOS  
![image](https://github.com/user-attachments/assets/751fb68b-78a0-4066-a953-31cb0e33c14d)
## BIBLIOTECA CENTRAL - VISITANTES  
![image](https://github.com/user-attachments/assets/cfc3689f-5050-43bf-92b1-5a2c386a181e)
## T9 - VISITANTES  
![image](https://github.com/user-attachments/assets/670946c6-8aba-4771-a1a8-65fe3d83087c)
## T9 - RECURSOS  
![image](https://github.com/user-attachments/assets/984f8764-a4d1-43b0-a0dd-05d77aa85b4d)
## T3 - SOPORTE  
![image](https://github.com/user-attachments/assets/446bdae5-c219-40aa-b760-2527cb45809d)
## T3 - RECURSOS
![image](https://github.com/user-attachments/assets/5c33498c-6fa4-4591-8ab1-1815f3b28187)
## VLAN
en cada switch involucrado. Creamos las VLANs 34, 14, y 24. Para hacerlo, se siguieron los siguientes pasos en cada switch  
```
Switch(config)# vlan 34
Switch(config-vlan)# name Recursos
Switch(config-vlan)# exit

Switch(config)# vlan 14
Switch(config-vlan)# name Soporte
Switch(config-vlan)# exit

Switch(config)# vlan 24
Switch(config-vlan)# name Visitantes
Switch(config-vlan)# exit
```
## Asignar puertos a las VLANs
En cada switch donde están conectadas las computadoras rodeadas de verde, se asignaron los puertos a la VLAN 34.  
```
Switch(config)# interface fastEthernet 0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 34
Switch(config-if)# exit

```
Para las computadoras en la VLAN 14 (Soporte), conectadas en los puertos correspondientes de cada switch  
```
Switch(config)# interface fastEthernet 0/2
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 14
Switch(config-if)# exit
```

## Configurar Trunks entre switches  
Para que las VLANs se comuniquen entre los switches, se configuraro enlaces troncales entre ellos. Los enlaces troncales permiten que múltiples VLANs pasen a través de un puerto.

En el caso de FastEthernet 0/5, FastEthernet 0/4, y similares son los que conectan un switch con otro. En este caso, usa el siguiente comando para configurar un trunk en ambos extremos:
```
Switch(config)# interface fastEthernet 0/5
Switch(config-if)# no switchport trunk encapsulation dot1q
Switch(config-if)# switchport trunk allowed vlan 14,24,34
Switch(config-if)# exit
```
Esto para cada cable que conecta un switch con otro  
##  Configurar un switch con enrutamiento inter-VLAN
para que las VLANs se comuniquen entre sí (enrutamiento inter-VLAN), se configuro uno de los switches de capa 3 dfel edificio T3 para realizar el enrutamiento entre las VLANs.  
```
Switch(config)# interface vlan 34
Switch(config-if)# ip address 192.168.34.1 255.255.255.0
Switch(config-if)# no shutdown
Switch(config-if)# exit

Switch(config)# interface vlan 14
Switch(config-if)# ip address 192.168.14.1 255.255.255.0
Switch(config-if)# no shutdown
Switch(config-if)# exit

Switch(config)# interface vlan 24
Switch(config-if)# ip address 192.168.24.1 255.255.255.0
Switch(config-if)# no shutdown
Switch(config-if)# exit
```

## LACP

Se realizó la configuración del PortChannel, donde es una técnica que se utiliza para combinar múltiples enlaces físicos en un solo enlace lógico de alta velocidad. Esto mejora la capacidad y la redundancia de la conexión entre dos dispositivos, como un switch y un servidor o entre dos switches, con los siguientes comandos se realizo este proceso en el switch central (T3) y los demas switches de capa 3.  
Para los switchs de capa 3
```
interface range fastEthernet 0/1-x
channel-protocol lacp
channel-group 1 mode active
```
para el  switch central (T3).  
```
interface range fastEthernet 0/1-4
channel-protocol lacp
channel-group 12 mode active

interface range fastEthernet 0/5-8
channel-protocol lacp
channel-group 2 mode active

interface range fastEthernet 0/9-12
channel-protocol lacp
channel-group 3 mode active
```
## OSPF

El OSPF es un protocolo de enrutamiento dinámico que se utiliza para enrutar paquetes dentro de una red de computadoras, por lo que se procede a configurar el mismo sobre los  switches capa 3 de la topología, como se muestra a continuación:  
```
router ospf 22
 router-id 1.1.1.1
 log-adjacency-changes
 network 192.168.50.0 0.0.0.255 area 22
 network 192.168.60.0 0.0.0.255 area 22
 network 192.168.70.0 0.0.0.255 area 22
 network 192.168.34.0 0.0.0.255 area 22
 network 192.168.44.0 0.0.0.255 area 22


router ospf 22
 router-id 1.1.1.1
 log-adjacency-changes
 network 192.168.70.0 0.0.0.255 area 22
 network 192.168.74.0 0.0.0.255 area 22
 network 192.168.84.0 0.0.0.255 area 22
```


## EIGRP

El EIGRP es un protocolo de enrutamiento de estado de enlace, que se utiliza para enrutar paquetes dentro de una red de computadoras, por lo que se procede a configurar el mismo sobre los switches de la topología, como se muestra a continuación:


## ACLs
Estas seran utilizadas para que bloqueen o permitan tráfico de manera específica.  
De la siguiente forma se han configurado los acls del switchs.  
### T3
```
ip access-list extended SOPORTE
 permit icmp any any echo
 permit icmp any any echo-reply
exit

ip access-list extended RECURSOS
 permit icmp any 192.168.44.0 0.0.0.255 echo-reply
 deny icmp any 192.168.44.0 0.0.0.255 echo
 permit icmp any any echo-reply
 permit icmp any any echo
exit

interface Vlan14
 ip access-group SOPORTE out
exit
interface Vlan34
 ip access-group RECURSOS in
exit
```
### BIBLIOTECA
```
ip access-list extended VISITANTES
 permit icmp any 192.168.44.0 0.0.0.255 echo-reply
ip access-list extended RECURSOS
 permit icmp any 192.168.44.0 0.0.0.255 echo-reply
 deny icmp any 192.168.44.0 0.0.0.255 echo
 permit icmp any any echo-reply
 permit icmp any any echo
```
### M2
```
ip access-list extended VISITANTES
 permit icmp any 192.168.44.0 0.0.0.255 echo-reply
ip access-list extended RECURSOS
 permit icmp any 192.168.44.0 0.0.0.255 echo-reply
 deny icmp any 192.168.44.0 0.0.0.255 echo
 permit icmp any any echo-reply
 permit icmp any any echo
```
### T9
```
ip access-list extended VISITANTES
 permit icmp any 192.168.44.0 0.0.0.255 echo-reply
ip access-list extended RECURSOS
 permit icmp any 192.168.44.0 0.0.0.255 echo-reply
 deny icmp any 192.168.44.0 0.0.0.255 echo
 permit icmp any any echo-reply
 permit icmp any any echo
```
## PRUEBA DE FUNCIONALIDAD
### SOPORTE – T3
Todas las demás VLANs de la red. 
![image](https://github.com/user-attachments/assets/df512696-e2a3-451d-861c-461b6dc4c647)

### RECURSOS – T3, M2, T9
Todas las VLANs de RECURSOS de los demás edificios
![image](https://github.com/user-attachments/assets/8a79a851-80f8-4e03-86cb-c3fea233327c)
### VISITANTES – T3, M2, T9  
No debe tener comunicación con las demás VLANs de la red
![image](https://github.com/user-attachments/assets/878b3ba8-7852-4d1e-8d52-a3f5beb8ebc8)


