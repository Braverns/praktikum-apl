erDiagram
    vessels ||--o{ trips : carries
    ports ||--o{ routes : starts
    ports ||--o{ routes : ends
    ports ||--o{ shipments : origin
    ports ||--o{ shipments : destination
    routes ||--o{ trips : assigned
    trips ||--o{ tickets : issues
    trips ||--o{ shipments : transports
    trips ||--o{ trip_crews : staffed_by
    passengers ||--o{ tickets : buys
    tickets ||--|| payment_ticket : pays
    cargo ||--o{ shipments : contains
    shipments ||--|| payment_shipment : pays
    crews ||--o{ trip_crews : assigned

    vessels {
        int vessel_id PK
        string vessel_name
        string vessel_type
        float cargo_capacity_ton
    }
    ports {
        int port_id PK
        string port_name
        string city
    }
    trips {
        int trip_id PK
        datetime departure_time
        string status
    }
