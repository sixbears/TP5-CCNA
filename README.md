## Checklist IP Routeurs

* Définition des ip statiques

Pour le réseau reliant les 2 routeurs j'ai choisi un réseau avec comme mask 255.255.255.252 (/30) car il ne va recevoir que 2 machines.
R1:10.2.3.253 --- R2:10.2.3.254

## Cheklist routes

- router1.tp5.b1  
directement connecté à net1 et net12  
route à ajouter : ```conf t / ip route 10.5.2.0 255.255.255.0 10.2.3.254```  

- router2.tp5.b1  
directement connecté à net2 et net12  
route à ajouter : ```conf t / ip route 10.5.1.0 255.255.255.0 10.2.3.253```  

- server1.tp5.b1  
directement connecté à net1  
route à ajouter :    
```sudo nano etc/sysconfig/network-scripts/route-enp0s3    10.5.2.0 via 10.5.1.254 dev enp0s3```    
fichiers hosts à remplir :   
```sudo nano /etc/hosts 10.5.2.10 client1.tp5.b1, 10.5.2.11 client2.tp5.b1```

- client1.tp5.b1  
directement connecté à net2
route à ajouter :  
```sudo nano etc/sysconfig/network-scripts/route-enp0s3    10.5.1.0 via 10.5.2.254 dev enp0s3```    
fichiers hosts à remplir :   
```sudo nano /etc/hosts 10.5.1.10 server1.tp5.b1, 10.5.2.11 client2.tp5.b1```  

- client2.tp5.b1  
directement connecté à net2
route à ajouter :     
```sudo nano etc/sysconfig/network-scripts/route-enp0s3    10.5.1.0 via 10.5.2.254 dev enp0s3```     
fichiers hosts à remplir :   
```sudo nano /etc/hosts 10.5.1.10 server1.tp5.b1 10.5.2.10 client1.tp5.b1```  


