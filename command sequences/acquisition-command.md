# Imaging Command Sequence
```mermaid
sequenceDiagram
    Actor Operator
    participant MCC/GS
    box FINCH
        participant RF
        participant OBC
        participant ADCS
        participant PAY
    end

    Operator->>MCC/GS: Load acquisition params
    MCC/GS->>RF: Send acquisition params

    alt Contact
        alt Nominal Sequence Execution
            RF->>OBC: Schedule acquisition
    
            alt Acquisition conditions met
                OBC->>ADCS: Set to fine pointing mode with attitude parameters
                PAY->>PAY: Cool camera to init temp
                ADCS-->>OBC: Ready
                PAY-->>PAY: Ready
    
                OBC->>ADCS: Trigger acquisition maneuver
                OBC->>PAY: Trigger image acquisition
                ADCS-->>OBC: Done
                OBC->>PAY: End image acquisition
                PAY->>PAY: Store Image Data

                OBC->>OBC: Perform Status Check
    
            else Acquisition conditions could not be met
                OBC->>OBC: Log status
                OBC->>OBC: Enter "Idle" sequence
            end
        else Anomaly
            OBC->>OBC: Log error
            OBC->>OBC: Enter "Safety" Sequence
        end
end
    

```
