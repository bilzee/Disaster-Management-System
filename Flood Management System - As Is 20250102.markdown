```mermaid

erDiagram
    Incident_impact {
        date Date
        string Incident_ID
        string Incident_severity
        string LGA
        int Number_affected
        int Number_displaced
        int Number_fatal
        int Number_injured
        string State
    }

    Camp {
        date Assessment_Date
        string Assessment_ID
        string Camp_ID
        string Camp_Name
        string Camp_Status
        float Lat
        float Lon
        string LGA
        int Pop_Children
        string State
    }

    Health {
        date Assessment_Date
        string Assessment_ID
        string Camp_ID
        string Camp_Name
        string Camp_Status
        int Cholera_cases
        int Diphtheria_cases
        int EssentialDrugs_Available
    }

    WASH {
        int People_Reached_Emergency
        int People_Reached_Hygiene
        int People_Reached_sustain
        int People_Reached_water
        date Assessment_Date
        string Camp_ID
        string Camp_Name
        string Camp_Status
        float Lat
        string LGA
        float Lon
        string State
    }

    Infrastructure {
        string Assessment_ID
        string Asset_Name
        string Asset_Type
        string Current_status
        string Damage_Level
        float Est_Repair_Cost
        string Infrastructure_ID
        float Lat
        string LGA
        float Lon
        string Ownership_Type
        string State
    }

    Incident_impact ||--|{ Camp : "One-to-Many"
    Incident_impact ||--|{ Infrastructure : "One-to-Many"
    Incident_impact ||--|{ WASH : "One-to-Many"
    Incident_impact ||--|{ Health : "One-to-Many"
    Camp }|--|| Health : "Many-to-One"
    Camp }|--|| WASH : "Many-to-One"
    Health ||--|{ WASH : "One-to-Many"

```
