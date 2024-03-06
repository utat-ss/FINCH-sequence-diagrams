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

    Command->>Charging: orient solar panels to maximize sun coverage
    Charging--)Safety: error/fault
    Charging->>Command: when batteries are sufficiently charged
  

    Command->>Imaging: perform imaging tasks
    Imaging--)Safety: error/fault
    Imaging->>Command: done with imaging


    Command->>Processing: process images
    Processing--)Safety: error/fault
    Processing->>Command: done with processing
    
    
    Command->>Downlinking: downlink data to ground station
    Downlinking--)Safety: error/fault
    Downlinking->>Command: done with downlinking

```
