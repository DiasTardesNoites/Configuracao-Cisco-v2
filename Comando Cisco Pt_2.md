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
# COMANDOS ACL
**Atrelar ACL a Interface**
```
>enable
#configure terminal
(config)# interface serial 0/0/0
(config-if)# ip access-group 11 out
```
**Remover ACL da interface**
```
>enable
#configure terminal
(config)# interface serial 0/0/0
(config-if)# no ip access-group 11 out
```
**Criar ACL Padrão Numerica (Filtragem de Protocolos TCP e UDP)**
```
>enable
#configure terminal
(config)# access-list 99 permit tcp 0.0.0.0 0.0.0.0 range 1024 65535 host 0.0.0.0 eq www
```
**Criar ACL Extendida Numerica (Filtragem de Protocolos TCP e UDP)**
```
>enable
#configure terminal
(config)# access-list 101 permit tcp 0.0.0.0 0.0.0.0 range 1024 65535 host 0.0.0.0 eq www
```
**Criar ACL Padrão Nomeada**
```
>enable
#configure terminal
(config)# ip access-list standard GrêmioSérieB
(config-std-nacl)# 10 permit tcp 0.0.0.0 0.0.0.0 host 0.0.0.0 eq 80
(config-std-nacl)# 20 deny tcp any any

```
**Criar ACL Extendida Nomeada**
```
>enable
#configure terminal
(config)# ip access-list extended MesaGabigol_APP
(config-std-nacl)# 10 permit ip 0.0.0.0 0.0.0.0 host 0.0.0.0
(config-std-nacl)# 20 permit icmp 0.0.0.0 0.0.0.0 host 0.0.0.0
(config-std-nacl)# 30 deny ip any any
```
**Proteção Login com ACL**
```
>enable
#config terminal
(config)#line vty 0 4
(config-line)#login local
(config-line)#transport input ssh
(config-line)#access-class 21 in
exit
(config)#access-list 21 permit 0.0.0.0 0.0.0.0
(config)#access-list 21 deny any
```
**Criar ACL numerada e criar um Comentario**
```
>enable
#configure terminal
(config)#access-list 1 remark Rede_LAN_S1
(config)#access-list 1 permit 0.0.0.0 0.0.0.0
(config)#access-list 1 deny any
(config)#do show access-list
```
**Verificar em qual porta esta aplicada a ACL**
```
>enable
#show running-config
```
**Verificar as ACLs**
```
>enable
#show access-lists 
```
>OBS:Para que os códigos funcionem não é necessário que os nomes sejam **GrêmioSérieB** ou **MesaGabigol_APP**!
Esses foram nomes aleatórios escolhidos por puro cunho _Futebolístico_. 

# COMANDOS PAT
**Configurar ACL para permitir endereços a serem convertidos**
```
>enable
#configure terminal
(config)#ip access-list (Nome da Access List) permit (Rede de Origem) (Wildcard de Origem) 
```
**Defina o Pool**
```
>enable
#configure terminal
(config)#ip nat pool (Nome-IPs-WAN-PAT) 0.0.0.0 0.0.0.0 netmask 0.0.0.0
```
**Criação do PAT (Vínculo da ACL ao Pool)**
```
>enable
#configure terminal
(config)#ip nat inside source list (nome-access-list) pool (nome-IP-WAN interface) Serial 0/0/0 overload
```
**Verificação do PAT**
```
>enable
#show ip nat translations 
```
**Limpar conversões/sessões atuais**
```
>enable
#clear ip nat translation 
```
**Verificação do Pool**
```
>enable
#show ip nat statistics
```
**Limpar Estatisticas**
```
>enable
#clear ip nat statistics
```














<img src="https://media3.giphy.com/media/3o7bu3XilJ5BOiSGic/giphy.gif?cid=ecf05e47gds2nlhmmv31k1o1ibypgrbo2ai2lf3m08kg35rx&rid=giphy.gif&ct=g" width="150">
