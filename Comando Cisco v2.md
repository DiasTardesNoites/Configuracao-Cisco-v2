# COMANDOS RIPv2
**Ativar Protocolo RIPv2**
```
>enable
#configure terminal
(config)#router rip
(config-router)#version 2
```
**Desativar e eliminar o RIP**
```
>enable
#configure terminal
(config)#no router rip
```
**Anunciar redes no RIP**
```
>enable
#configure terminal
(config)#router rip
(config-router)#version 2
R2(config-router)#no auto-summary
R2(config-router)#network 0.0.0.0
R2(config-router)#network 0.0.0.0
```
**Exibir configurações do protocolo IPv4**
```
>enable
#show ip protocols
```
**Exibir rotas do RIP**
```
>enable
#show ip route
```
**Especificar interface sem Roteador**
```
>enable
#configure terminal
(config)#router rip
(config-router)#version 2
(config-router)#passive-interface g0/0
```

# COMANDOS OSPF

* **_Configuração De Single Area_**

**Criar OSPF com ID de processo 10**
```
>enable
#configure terminal
(config)#router ospf 10
```
**Especificar ID do Roteador**
```
>enable
#configure terminal
(config)#router ospf 10
(config-router)#router-id 0.0.0.0
end
#show ip protocols
```
**Especificar Redes que o Roteador participa**
```
>enable
#configure terminal
(config)#router ospf 10
(config-router)#network 0.0.0.0 0.0.0.0 area 0
(config-router)#network 0.0.0.0 0.0.0.0 area 0
(config-router)#network 0.0.0.0 0.0.0.0 area 0
```
**Especificar interface sem Roteador**
```
>enable
#configure terminal
(config)#router ospf 10
(config-router)#passive-interface g0/0
end
```
**Realizar Limpeza**
```
>enable
#clear ip ospf process
```

* **_Verificar Custos_**

**Verificar banco de dados do OSPF**
```
>enable
#show ip ospf database
```
**Verificar Interfaces do OSPF**
```
>enable
#show ip ospf interface
```
**Verificar vizinhos OSPF**
```
>enable
#show ip ospf neighbor
```
