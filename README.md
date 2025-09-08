# AML
Financial services risk analysis 


flowchart TD
    %% ========== LAYER 1 ==========
    subgraph L1[Layer 1 - Default Processing]
        direction TB
        A[Raw CSV File] --> B[Detect Encoding]
        B --> C[Identify Delimiter]
        C --> D[Validate Headers]
        D --> E[Handle Multiline Cells]
        E --> F[Remove Extra Whitespace]
        F --> G[Load into DataFrame]
        
        G --> H{Column Classification}
        
        H --> I[Text Columns]
        H --> J[Numerical Columns]
        H --> K[DateTime Columns]
        H --> L[Categorical Columns]
        
        I --> M[Convert to String]
        M --> N[Lowercase Strip]
        N --> O[Remove HTML Tags]
        O --> P[Unicode Normalization]
        P --> Q[Clean Text Data]
        
        J --> R[Preserve as Metadata]
        K --> R
        L --> R
    end

    %% ========== LAYER 2 ==========
    subgraph L2[Layer 2 - User Enabled Processing]
        direction TB
        Q --> S[User Options]
        R --> S
        
        S --> T[Preprocess Text Columns]
        T --> U[Text Normalization]
        U --> V[Stemming]
        V --> W[Lemmatization]
        W --> X[Stop Word Removal]
        X --> Y[Processed Text Data]
        
        S --> Z[Data Type Validation]
        Z --> AA[Validated Data]
        
        S --> BB[Duplicate Row Deduction]
        BB --> CC[Deduplicated Data]
        
        S --> DD[Missing Values Handling]
        DD --> EE{Missing Value Strategy}
        EE --> FF[Leave As Is]
        EE --> GG[Fill Custom Values]
        EE --> HH[Drop Rows or Columns]
        FF --> II[Handled Missing Values]
        GG --> II
        HH --> II
    end

    %% ========== QUALITY CONTROL ==========
    subgraph L3[Quality Control Layer]
        direction TB
        Y --> JJ[Quality Gates]
        AA --> JJ
        CC --> JJ
        II --> JJ
        JJ --> KK[User Review Point]
        KK --> LL{Quality Pass?}
    end

    %% ========== OUTPUT PATHS ==========
    LL -->|Pass| MM[Final Clean DataFrame with Metadata]
    MM --> NN[Proceed to Chunking Layer]
    
    LL -->|Fail| OO[Error Handling and User Notification]
    OO --> PP[User Action]
    PP --> QQ{Action Type}
    QQ -->|Retry| L2
    QQ -->|Adjust Config| RR[Update Configuration]
    RR --> L2

    %% ========== STYLING ==========
    classDef input fill:#e1f5fe,stroke:#01579b,stroke-width:2px
    classDef process fill:#c8e6c9,stroke:#2e7d32,stroke-width:2px
    classDef decision fill:#fff3e0,stroke:#ff6f00,stroke-width:2px
    classDef metadata fill:#f3e5f5,stroke:#7b1fa2,stroke-width:2px
    classDef success fill:#e8f5e9,stroke:#388e3c,stroke-width:2px
    classDef error fill:#ffebee,stroke:#c62828,stroke-width:2px
    classDef layer fill:#f5f5f5,stroke:#9e9e9e,stroke-width:2px
    
    class L1,L2,L3 layer
    class A input
    class B,C,D,E,F,G,M,N,O,P,T,U,V,W,X,Z,BB,DD process
    class H,EE,QQ decision
    class R,II metadata
    class MM,NN success
    class OO,PP,RR error
    
    linkStyle default stroke:#333,stroke-width:1.5px
