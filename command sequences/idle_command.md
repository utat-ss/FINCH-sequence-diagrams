
# Idle Command Sequence
```mermaid
sequenceDiagram
    actor Operator
    participant MCC/GS
    box FINCH
        participant RF
        participant OBC 
        participant ADCS
        participant Power
    end


    OBC->>ADCS: Adjust orientation to sun pointing
    ADCS-->>OBC: Done
    ADCS->>OBC: Report attitude telemetry
    Power->>OBC: Report battery telemetry


    Operator->>MCC/GS: Ping FINCH
    MCC/GS->>RF: Transmit ping

    alt contact
        RF->>OBC: Transmit ping
        OBC->>OBC: Enter "Downlinking" sequence with parameter "Telemetry"

    else error
        OBC->>OBC: Log error
        OBC->>OBC: Enter "Safety" sequence

    end



