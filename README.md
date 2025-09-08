# AML
Financial services risk analysis 




flowchart TD
    %% Entry Point
    A[Clean DataFrame with Metadata] --> B[User Choice Logic Layer]
    
    %% User Configuration Layer
    B --> C[Method Selection & Configuration]
    C --> D[Parameter Setup]
    D --> E[Quality Requirements Setup]
    E --> F[Output Preferences Setup]
    
    %% Method Selection Decision
    F --> G{Select Chunking Method}
    
    %% Fixed Chunking Branch
    G --> H[Fixed Chunking Method]
    H --> H1[Set Chunk Size Parameters]
    H1 --> H2[Apply Overlap Settings]
    H2 --> H3[Handle Word Boundaries]
    H3 --> H4[Generate Fixed Chunks]
    H4 --> M1[Fixed Method Output]
    
    %% Recursive Chunking Branch
    G --> I[Recursive Chunking Method]
    I --> I1[Define Hierarchy Rules]
    I1 --> I2[Split by Paragraphs]
    I2 --> I3[Split by Sentences]
    I3 --> I4[Split by Words if Needed]
    I4 --> I5[Generate Recursive Chunks]
    I5 --> M2[Recursive Method Output]
    
    %% Semantic Chunking Branch
    G --> J[Semantic Chunking Method]
    J --> J1[Generate Text Embeddings]
    J1 --> J2[Calculate Semantic Similarity]
    J2 --> J3[Apply Similarity Threshold]
    J3 --> J4[Group Related Content]
    J4 --> J5[Generate Semantic Chunks]
    J5 --> M3[Semantic Method Output]
    
    %% Document Chunking Branch
    G --> K[Document Chunking Method]
    K --> K1[Analyze Document Structure]
    K1 --> K2[Identify Headers and Sections]
    K2 --> K3[Respect Natural Boundaries]
    K3 --> K4[Preserve Section Metadata]
    K4 --> K5[Generate Document Chunks]
    K5 --> M4[Document Method Output]
    
    %% Agentic Chunking Branch
    G --> L[Agentic Chunking Method]
    L --> L1[Initialize LLM Analysis]
    L1 --> L2[Analyze Content Context]
    L2 --> L3[Determine Optimal Split Points]
    L3 --> L4[Apply Intelligent Chunking]
    L4 --> L5[Self-Evaluate Results]
    L5 --> M5[Agentic Method Output]
    
    %% Merge All Method Outputs
    M1 --> N[Chunk Quality Assessment Layer]
    M2 --> N
    M3 --> N
    M4 --> N
    M5 --> N
    
    %% Quality Assessment Process
    N --> O[Size Validation Check]
    O --> P[Content Completeness Check]
    P --> Q[Overlap Verification Check]
    Q --> R[Semantic Coherence Check]
    R --> S{Quality Gate Decision}
    
    %% Quality Failure Branch
    S --> T[Quality Issues Handler]
    T --> U[Generate Error Report]
    U --> V[User Notification System]
    V --> W{User Action Decision}
    W --> X[Adjust Parameters]
    W --> Y[Change Method Selection]
    W --> Z[Manual Review Mode]
    X --> G
    Y --> G
    Z --> AA[Manual Chunk Editor]
    AA --> BB[User Approved Chunks]
    
    %% Quality Success Branch
    S --> CC[Chunk Standardization Layer]
    BB --> CC
    
    %% Standardization Process
    CC --> DD[Create Chunk Objects]
    DD --> EE[Attach Source Metadata]
    EE --> FF[Assign Unique Identifiers]
    FF --> GG[Apply Sequential Ordering]
    GG --> HH[Remove Duplicate Chunks]
    HH --> II[Validate Coverage Completeness]
    II --> JJ[Final Chunk Collection]
    
    %% Embedding Generation Layer
    JJ --> KK[Embedding Processing Layer]
    KK --> LL[Select Embedding Model]
    LL --> MM[Configure Batch Processing]
    MM --> NN[Generate Vector Embeddings]
    NN --> OO[Quality Check Embeddings]
    OO --> PP{Embedding Quality Gate}
    
    %% Embedding Success/Failure
    PP --> QQ[Embedding Error Handler]
    QQ --> RR[Retry Embedding Process]
    RR --> LL
    PP --> SS[Final Embedded Chunks Ready]
    
    %% Styling - Headers (Main Components)
    classDef headers fill:#e3f2fd,stroke:#90caf9,stroke-width:3px
    
    %% Styling - Sub Processes
    classDef subProcess fill:#f3e5f5,stroke:#ce93d8,stroke-width:2px
    
    %% Styling - Decision Points
    classDef decisions fill:#fff3e0,stroke:#ffb74d,stroke-width:3px
    
    %% Styling - Error Handling
    classDef errorHandling fill:#ffebee,stroke:#ef9a9a,stroke-width:2px
    
    %% Styling - Success States
    classDef success fill:#e8f5e8,stroke:#a5d6a7,stroke-width:3px
    
    %% Apply Styles to Headers
    class A,B,N,CC,KK headers
    
    %% Apply Styles to Sub Processes
    class C,D,E,F,H,I,J,K,L,H1,H2,H3,H4,I1,I2,I3,I4,I5,J1,J2,J3,J4,J5,K1,K2,K3,K4,K5,L1,L2,L3,L4,L5,M1,M2,M3,M4,M5,O,P,Q,R,DD,EE,FF,GG,HH,II,JJ,LL,MM,NN,OO subProcess
    
    %% Apply Styles to Decisions
    class G,S,W,PP decisions
    
    %% Apply Styles to Error Handling
    class T,U,V,X,Y,Z,AA,BB,QQ,RR errorHandling
    
    %% Apply Styles to Success
    class SS success
