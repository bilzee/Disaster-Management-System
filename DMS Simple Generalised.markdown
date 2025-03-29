```mermaid
erDiagram
    Incident {
        string IncidentID "PK"
        string IncidentSeverity
        datetime IncidentDate
        string IncidentName
        string RapidAssessmentID "FK"
    }

    RapidAssessment {
        string RapidAssessmentID "PK"
        datetime RapidAssessmentDate
        string IncidentID "FK"
        string AffectedEntityID "FK"
    }

    AffectedEntity {
        string AffectedEntityID "PK"
        string AffectedEntityName
        decimal Longitude
        decimal Latitude
        string RapidAssessment "FK"
        string RapidResponse "FK"
    }

    RapidResponse {
        string RapidResponseID "PK"
        datetime RapidResponseDate
        string AffectedEntityID "FK"
        string RapidAssessmentID "FK"
    }

    Incident ||--|{ RapidAssessment : "One-to-Many"
    RapidAssessment ||--|| AffectedEntity : "One-to-One"
    AffectedEntity ||--|{ RapidResponse : "One-to-Many"
    RapidAssessment ||--|{ RapidResponse : "One-to-Many"
```
