# Turbo
> **Fastest** and **cheapest** ~~decentralized~~ distributed residential proxy network.

This open-source infrastructure is designed for self-hosted, easy deployment via Docker Compose.
It is free for commercial use.


## Product

End-to-end encrypted HTTPS/SOCKS5 proxy network.


## System
```mermaid
flowchart LR
    User(Customer)
    ClientNode(Zero-Trust Client Node)
    subgraph Self-hosted [Self-hosted Docker backend]
        ProxyServer[Proxy Server]
        Redis[(Redis K/V store)]
        ClickHouse[(ClickHouse)]
    end
    TargetWebsite[Target Website]
    
    User --> |Sends HTTP/S or SOCKS5 Requests| ProxyServer
    
    ProxyServer <--> |TLS-encrypted QUIC Messaging| ClientNode

    ProxyServer --> |Stores metrics| ClickHouse
    ProxyServer --> |Uses for Auth & Credits| Redis

    ClientNode --> |Processes Requests To| TargetWebsite
```


