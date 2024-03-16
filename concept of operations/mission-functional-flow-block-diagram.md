# FINCH Mission Modes of Operations Flow Diagram
```mermaid
sequenceDiagram
    participant LEOP
    participant Command
    participant Charging
    participant Processing
    participant Downlinking
    participant Imaging
    participant Safety


    LEOP->>Command: Launch, deploy and detumble

    Command->>Charging: when low battery
    Charging--)Safety: error/fault
    Charging->>Command: when batteries are sufficiently charged
  

    Command->>Imaging: as scheduled by ground
    Imaging--)Safety: error/fault
    Imaging->>Command: done with imaging


    Command->>Processing: after imaging terminates
    Processing--)Safety: error/fault
    Processing->>Command: done with processing
    
    
    Command->>Downlinking: when received command from ground station
    Downlinking--)Safety: error/fault
    Downlinking->>Command: done with downlinking

```
