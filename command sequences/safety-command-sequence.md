# Safety Command Sequence 
```mermaid
sequenceDiagram
    Actor Operator
    participant MCC/GS
    participant RF
    participant OBC
    participant ADCS
    participant PAY

    OBC->>PAY: Turn off
    PAY-->>OBC: Done
    OBC->>ADCS: Set into "Safety" mode
    ADCS-->>OBC: Done

    OBC->>OBC: Set into "Safety" state

    Operator->>MCC/GS: Set command parameters
    MCC/GS->>RF: Transmit command parameters

    alt Contact
        alt Exit Command Received
            OBC->>OBC: Enter "Idle" Sequence
        else Exit Command NOT received
            OBC->>RF: Transmit error info
        end 
        OBC->>RF: Transmit telemetry
        RF->>MCC/GS: Downlink data
    end
    
```
