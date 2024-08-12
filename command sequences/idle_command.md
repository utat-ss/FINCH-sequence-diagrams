
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

    alt contact
        OBC->>ADCS: Adjust orientation to sun pointing
        ADCS->>OBC: Confirm orientation adjusted
        OBC->>Power: Activate power system
        Power->>OBC: Report charging status
   OBC->>RF: Telemetry data
        OBC->>RF: Trigger downlink
        RF->>MCC/GS : Data downlink
        RF-->>OBC: Done

        MCC/GS ->>Operator: Confirm charging initiated
    else Charging status error
        OBC->>OBC: Log error
        OBC->>RF: Telemetry data
        OBC->>RF: Trigger downlink
        RF->>MCC/GS : Data downlink
        RF-->>OBC: Done
        MCC/GS ->>Operator: Report error
    end



