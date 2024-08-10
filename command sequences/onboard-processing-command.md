```mermaid
participant MCC
    participant RF
    participant OBC
    participant ADCS
    participant PAY
    participant Other

    MCC->>RF: Command Downlink
    activate RF
    RF->>RF: Decode & Verify
    RF->>OBC: Command
    deactivate RF

    activate OBC
    OBC->>OBC: Interpret & Validate
    OBC->>OBC: Schedule & Prioritize

    alt Attitude Control Required
        OBC->>ADCS: Attitude Command
        activate ADCS
        ADCS->>ADCS: Execute Maneuver
        ADCS->>OBC: Maneuver Complete
        deactivate ADCS
    end

    alt Payload Operation Required
        OBC->>PAY: Payload Command
        activate PAY
        PAY->>PAY: Configure & Acquire Data
        PAY->>OBC: Data Ready
        deactivate PAY
    end
    
    alt Other Subsystem Interactions
        OBC->>Other: Subsystem Command
        activate Other
        Other->>Other: Execute Command
        Other->>OBC: Command Complete
        deactivate Other
    end


```
