
# Chrging Command Sequence
```mermaid
sequenceDiagram
    actor Operator
    participant MCC
    box FINCH
        participant RF
        participant OBC as Onboard Computer (OBC)
        participant ADCS
        participant Power
    end

    Operator->>MCC: Send charging command
    MCC->>RF: Transmit command to CubeSat
    RF->>OBC: Relay command to OBC
    alt No error
        OBC->>ADCS: Adjust orientation to sun pointing
        ADCS->>OBC: Confirm orientation adjusted
        Note right of ADCS: Orientation adjusted towards sun vector
        OBC->>Power: Activate power system
        Power->>OBC: Report charging status
        OBC->>OBC: Trigger downlink
        OBC->>RF: Telemetry data
        RF->>MCC: Data downlink
        MCC->>Operator: Confirm charging initiated
    else Charging status error
        OBC->>OBC: Log error
        OBC->>RF: Transmit error status to MCC
        RF->>MCC: Relay error status to MCC
        MCC->>Operator: Report error
    end



