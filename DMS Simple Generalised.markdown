```mermaid
erDiagram
    Incident {
        string IncidentID "PK"
        string IncidentSeverity
        datetime IncidentDate
        string IncidentName
        string AffectedEntityID "FK"
    }

    AffectedEntity {
        string AffectedEntityID "PK"
        string AffectedEntityName
        decimal Longitude
        decimal Latitude
        string IncidentID "FK"
        string RapidAssessment "FK"
        string RapidResponse "FK"
    }

    RapidAssessment {
        string RapidAssessmentID "PK"
        datetime RapidAssessmentDate
        string AffectedEntityID "FK"
    }

    RapidResponse {
        string RapidResponseID "PK"
        datetime RapidResponseDate
        string AffectedEntityID "FK"
        string RapidAssessmentID "FK"
    }


    Incident }|--|{ AffectedEntity : "*:*"
    AffectedEntity ||--|{ RapidAssessment : "1:*"
    AffectedEntity ||--|{ RapidResponse : "1:*"
    RapidAssessment ||--|{ RapidResponse : "1:*"

```
