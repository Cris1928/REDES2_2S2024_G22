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
| 12.0.0.0  | --- | M2 -> T3
| 13.0.0.0  | --- | T9  -> T3
| 11.0.0.0  | --- | BIBLIOTECA -> T3 

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
Para las computadoras en la VLAN 24, se siguio este procedimiento en los puertos correspondiente  
```
Switch(config)# interface fastEthernet 0/3
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 24
Switch(config-if)# exit
```
