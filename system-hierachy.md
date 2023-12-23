# FINCH System Hierachy Diagram
See [System Architecture](https://www.notion.so/utat-ss/aa7abed08ca749f685d8266b6ede20ce?v=2676ae2481e843a49b551e2e7c0308ed&pvs=4) database for source truth. This diagram should someday be generated from the database using TreeViz.
```mermaid
graph LR
    ADCS
    ADCS_Controller[ADCS Controller]
    Antennas
    Data_Bus[Data Bus]
    Data_Storage[Data Storage]
    Power
    FINCH[FINCH Spacecraft]
    GNSS_Antenna[GNSS Antenna]
    Mechanical
    OBC
    Optics
    Panels
    Pay_Mech[Payload Mechanical]
    Payload
    Power_Bus[Power Bus]
    Rails
    RF
    Star_Tracker[Star Tracker]
    Sun_Sensors[Sun Sensors]
    Thermal
    Transceiver
    Temperature_Sensors[Temperature Sensors]
    Thermal_Strap[Thermal Strap]
    Payload_Firmware[Payload Firmware]
    Power_Controller[Power Controller]
    Battery_Pack[Battery Pack]
    Solar_Panels[Solar Panels]

    FINCH --> ADCS
    FINCH --> Power
    FINCH --> Mechanical
    FINCH --> Firmware
    FINCH --> Payload
    FINCH --> RF
    FINCH --> Thermal

    Payload --> Optics
    Payload --> Payload_Firmware
    Payload --> Pay_Mech

    ADCS --> Star_Tracker
    ADCS --> Sun_Sensors
    ADCS --> GNSS_Antenna
    ADCS --> ADCS_Controller

    Power --> Power_Controller
    Power --> Battery_Pack
    Power --> Power_Bus
    Power --> Solar_Panels
    
    Mechanical --> Panels
    Mechanical --> Rails

    Firmware --> OBC
    Firmware --> Data_Storage
    Firmware --> Data_Bus

    RF --> Transceiver
    RF --> Antennas

    Thermal --> Temperature_Sensors
    Thermal --> Radiator
    Thermal --> Thermal_Strap

```