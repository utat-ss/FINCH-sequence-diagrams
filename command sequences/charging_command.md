
# Chrging Command Sequence
```mermaid
sequenceDiagram
    Actor Operator
    participant MCC
    box FINCH
        participant RF
        participant OBC as Onboard Computer (OBC)
        participant SolarPanels
        participant BatteryPack as BP
        participant ADCS
        participant PAY
    end

    Operator->>MCC: Send charging command
    MCC->>RF: Transmit command to CubeSat
    RF->>OBC: Relay command to OBC
    OBC->>SolarPanels: Activate solar panels
    SolarPanels->>BP: Start power generation
    BP->>OBC: Monitor charging process
    OBC->>ADCS: Adjust orientation for optimal charging
    BP->>OBC: Report charging status
    OBC->>RF: Transmit status to MCC
    RF->>MCC: Relay status to MCC
    MCC->>Operator: Confirm charging initiated

