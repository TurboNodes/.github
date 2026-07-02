# Turbo

Turbo is a distributed residential proxy network.

This open-source infrastructure is designed for self-hosted, easy deployment via Docker Compose.
It is free for commercial use.


## Products

End-to-end encrypted HTTPS/SOCKS5 proxy network.


## System
```mermaid
%%{init: {
  "flowchart": {
    "rankSpacing": 20
  },
  "themeVariables": {
    "fontSize": "12px"
  }
}}%%
flowchart TD
    User(Customer)
    ClientNode(Zero-Trust Client Node)
    subgraph Self-hosted [Self-hosted backend]
        ProxyServer[Proxy Server]
        Redis[(Redis Database & Streams)]
        AI[Traffic Analysis] 
    end
    TargetWebsite[Target Website]
    S3@{ shape: datastore, label: "Amazon S3" }

    User --> |Sends HTTP/S or SOCKS5 Requests| ProxyServer
    
    ProxyServer <--> |TLS-encrypted QUIC Messaging| ClientNode
    ProxyServer --> |Uses for Auth & Credits| Redis
    
    AI --> |Evaluates server connections| Redis
    AI --> |Stores metrics| S3

    ClientNode --> |Processes Requests To| TargetWebsite
    
```


