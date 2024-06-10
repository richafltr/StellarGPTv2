```mermaid
graph TD
    subgraph User
        StellarGPT[StellarGPT Interface]
    end

    subgraph StellarGPT Server
        S1[Stellar API Endpoints]
        S2[Soroban API Endpoints]
        S3[Signing Endpoints]
        S4[Database]
    end

    subgraph Stellar
        StellarHorizon[Stellar Horizon]
        StellarExpert[Stellar Expert]
        SorobanRPC[Soroban RPC]
    end

    subgraph Client
        Browser[User Browser]
    end

    ChatGPT --> |query| S1
    ChatGPT --> |query| S2
    S1 --> |get & post| S4
    S2 --> |get & post| S4
    S3 --> |sign & post| Freighter[Freighter Wallet]
    Browser --> |get| S4
    S4 --> |data| Browser
    S4 --> |write tx data| S1
    S4 --> |write tx data| S2
    StellarHorizon --> |get| S4
    StellarExpert --> |get| S4
    SorobanRPC --> |get| S4

    %% Visualization Flow
    subgraph Visualization
        ChatGPT --> |generate diagrams| VisComp[Interactive Visualization Components]
        VisComp --> |interactive data| Browser
    end

    %% Refreshing Flow
    Browser --> |fetch data| S4
    S4 --> |refresh data| VisComp
