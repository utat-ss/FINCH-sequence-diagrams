# Downlinking Command Sequence
'''mermaid
sequenceDiagram
    Actor Operator
    participant MCC
    participant GS
    box FINCH
        participant RF
        participant OBC
        participant ADCS
        participant PAY
    end

    Operator->>MCC->>GS: Load downlink parameters
    
    alt Contact
        GS->>RF: Send downlink parameters
        RF->>OBC: Schedule downlink
        
        alt Downlink conditions met
            OBC->>ADCS: Orient to init attitude
            OBC->>RF: ???
            ADCS-->>OBC: Ready
            RF-->>OBC: Ready

            OBC->>ADCS: Trigger downlink maneuver
            OBC->>RF: Trigger downlink
            ADCS-->>OBC: Done
            OBC->>RF: End downlink
            RF->>GS: Downlink data

            alt Downlink telemetry data
                OBC->>RF: Telemetry data
                OBC->>RF: Trigger downlink
                RF->>GS: Downlink telemetry data

            alt Downlink image data
                PAY->>PAY: Verify image compression
                OBC->>PAY: Send image to RF
                PAY->>RF: Image data
                OBC->>RF: Trigger downlink
                RF->>GS: Downlink image data

        else Downlink conditions could not be met
            OBC->>OBC: Log error
        end
    end

    alt Downlink
        GS->>MCC: Transfer data to database server
        RF-->>OBC: Done 
    end