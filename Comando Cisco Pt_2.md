# COMANDOS NAT
**Ativar NAT nas interfaces Internas e Externas**
```
>enable
#configure terminal
(config)#interface g0/0
(config-if)#ip nat inside
exit
(config)#interface g0/1
(config-if)#ip nat outside
exit
```
**Regra de NAT Estatico por IP**
```
>enable
#configure terminal
(config)#ip nat inside source static 0.0.0.0 0.0.0.0
```
**Regra de NAT Estatico por Porta**
```
>enable
#configure terminal
(config)#ip nat inside source static tcp 0.0.0.0 "0" 0.0.0.0 "0"
```
**Verificar IPs**
```
>enable
#show ip interface brief
```
**Verificar Outside e Inside**
```
>enable
#show run
```
**Verificar Rotas**
```
>enable
#show ip route
```
**Verificar Rotas**
```
>enable
#show ip nat statistics
```
**Após a inserção do NAT**
```
>enable
#show ip nat translations
```

<img src="https://media3.giphy.com/media/3o7bu3XilJ5BOiSGic/giphy.gif?cid=ecf05e47gds2nlhmmv31k1o1ibypgrbo2ai2lf3m08kg35rx&rid=giphy.gif&ct=g" width="150">
