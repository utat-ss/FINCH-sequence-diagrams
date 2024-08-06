
# Chrging Command Sequence
```mermaid
sequenceDiagram
    actor Operator
    participant MCC
    box FINCH
        participant RF
        participant OBC as Onboard Computer (OBC)
        participant SolarPanels
        participant PowerController
        participant BatteryPack
        participant ADCSController
    end

    Operator->>MCC: Send charging command
    MCC->>RF: Transmit command to CubeSat
    RF->>OBC: Relay command to OBC
    OBC->>PowerController: Activate solar panels
    PowerController->>SolarPanels: Start generating power
    SolarPanels->>BatteryPack: Store generated power
    BatteryPack->>OBC: Report charging status
    OBC->>ADCSController: Adjust orientation for optimal charging
    ADCSController->>OBC: Confirm orientation adjusted
    OBC->>RF: Transmit status to MCC
    RF->>MCC: Relay status to MCC
    MCC->>Operator: Confirm charging initiated


