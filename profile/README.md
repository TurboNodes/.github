# Turbo

Turbo is a distributed residential proxy network.

This open-source infrastructure is designed for self-hosted, easy deployment via Docker Compose.
It is free for commercial use.


## Products

End-to-end encrypted HTTPS/SOCKS5 proxy network.


## System
```mermaid
flowchart TD
    User(Customer)
    ClientNode(Zero-Trust Client Node)
    subgraph Self-hosted [Self-hosted backend]
        ProxyServer[Proxy Server]
        Redis[(Redis Database & Streams)]
        AI[Traffic Analysis] 
    end
    TargetWebsite[Target Website]

    User --> |Sends HTTP/S or SOCKS5 Requests| ProxyServer
    
    ProxyServer <--> |TLS-encrypted QUIC Messaging| ClientNode
    ProxyServer --> |Uses for Auth & Credits| Redis
    
    AI --> |Evaluates server connections| Redis

    ClientNode --> |Processes Requests To| TargetWebsite
    
```


