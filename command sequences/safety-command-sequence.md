# Safety Command Sequence 
```mermaid
sequenceDiagram
    Actor Operator
    participant MCC/GS
    participant RF
    participant ADCS
    participant PAY
    participant POWER
    participant THERMAL
    participant MECH

    OBC->>PAY: Turn off
    PAY-->>OBC: Done
    OBC->>ADCS: Turn off
    PAY-->>OBC: Done

    OBC->>OBC: Set into "Safety" state

    alt Contact
        OBC->>RF: Transmit error info
        OBC->>RF: Transmit telemetry
        RF->>MCC/GS: Downlink data

    
```
