```mermaid
flowchart LR
    subgraph Local
    Ordinateur[Ordinateur] -.-|SSH : IP publique| Box{Box}
    end
    Box -.-|SSH| Internet[Fournisseur <br /> internet]
    Internet -.-|SSH <br /> ETH1 : | VMAdmin[VM Admin Linux <br /> Firewall <br /> 1 port <br /> 2 cartes réseau]
    subgraph Azure - 10.0.4.0/24
    VMAdmin ---|SSH  <br /> ETH0 : 10.0.4.1| VN((Virtual Network privé))
    VN ---|SSH  <br /> ETH0 : 10.0.4.2| BDD[VM BDD Linux]
    VN ---|SSH  <br />  ETH0 : 10.0.4.3| Appli[VM Application Linux]
    end
    Appli --- |ETH1 : | Services[Services applicatifs]
```
