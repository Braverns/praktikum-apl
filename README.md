erDiagram
    vessels ||--o{ trips : "assigned to"
    ports ||--o{ routes : "as origin"
    ports ||--o{ routes : "as destination"
    ports ||--o{ shipments : "origin"
    ports ||--o{ shipments : "destination"
    routes ||--o{ trips : "defines"
    trips ||--o{ tickets : "has"
    trips ||--o{ shipments : "carries"
    trips ||--o{ trip_crews : "staffed by"
    passengers ||--o{ tickets : "purchases"
    tickets ||--|| payment_ticket : "paid by"
    cargo ||--o{ shipments : "loaded in"
    shipments ||--|| payment_shipment : "paid by"
    crews ||--o{ trip_crews : "assigned to"

    vessels {
        int vessel_id PK
        string vessel_name
        string vessel_type
        float cargo_capacity_ton
        int passenger_capacity
        string engine_type
        string owner_company
    }

    ports {
        int port_id PK
        string port_name
        string river_name
        string city
        string province
        float latitude
        float longitude
    }

    routes {
        int route_id PK
        int origin_port_id FK
        int destination_port_id FK
        float distance_km
        float estimated_hours
    }

    trips {
        int trip_id PK
        int vessel_id FK
        int route_id FK
        datetime departure_time
        datetime arrival_time
        string status
    }

    passengers {
        int passenger_id PK
        string full_name
        string id_number
        string phone
        string address
    }

    tickets {
        int ticket_id PK
        int passenger_id FK
        int trip_id FK
        string seat_number
        decimal ticket_price
        string ticket_status
    }

    cargo {
        int cargo_id PK
        string description
        float weight_kg
        float volume_m3
        string cargo_type
    }

    shipments {
        int shipment_id PK
        int cargo_id FK
        int trip_id FK
        string shipper_name
        string consignee_name
        int origin_port_id FK
        int destination_port_id FK
        decimal freight_cost
    }

    crews {
        int crew_id PK
        string crew_name
        string role
        string phone
    }
