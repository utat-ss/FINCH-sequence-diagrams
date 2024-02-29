# Modes of Operation

```mermaid
stateDiagram-v2
    [*] --> PPODState: Mission Commences
    PPODState --> SpacecraftEjection: Spacecraft integrated in\nP-POD on launch vehicle before deployment
    SpacecraftEjection --> PassiveState: Spacecraft recently ejected\nfrom vehicle
    PassiveState --> PreparationForImaging: Spacecraft is idle,\nprocesses that are not time-sensitive\nare carried out
    PreparationForImaging --> Imaging: orient spacecraft\nappropriately, get ready
    Imaging --> PreparationForImaging: Capture data
    PassiveState --> EndOfMission: spacecraft enters low\npower state, mission ends
    PassiveState --> PrepForTransmission: Spacecraft is idle,\nprocesses that are not time-sensitive\nare carried out
    PrepForTransmission --> DataLink: orient spacecraft\nappropriately
    DataLink --> TTAndCLink: high speed, transmits images
    TTAndCLink --> DataLink: Lower speed, for\nspacecraft status

    SpacecraftEjection --> CriticalFault: Critical Fault Occurs
    CriticalFault --> RecoveryState: Run error diagnostics,\nreturn spacecraft to normal
    RecoveryState --> PassiveState: Run error diagnostics,\nreturn spacecraft to normal




```
