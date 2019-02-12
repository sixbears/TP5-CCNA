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
route à ajouter : net2  
fichiers hosts à remplir : client1.tp5.b1, client2.tp5.b1  

- client1.tp5.b1  
directement connecté à net2
route à ajouter : net1
fichiers hosts à remplir : server1.tp5.b1, client2.tp5.b1  

- client2.tp5.b1  
directement connecté à net2
route à ajouter : net1
fichiers hosts à remplir : server1.tp5.b1, client1.tp5.b1  

- router1.tp5.b1  
directement connecté à net2
route à ajouter : net1

