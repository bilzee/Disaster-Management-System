```mermaid
erDiagram
    Incident {
        string IncidentID "PK"
        string IncidentTypeID "LU"
        string IncidentSeverity
        datetime IncidentDate
        string IncidentName
        string AffectedEntityID "FK"
    }

    Lookup_IncidentType {
        string IncidentTypeID "FloodIncident, FireIncident, LandslideIncident, CycloneIncident, OtherIncident"
        string IncidentTypeName
    }

    AffectedEntity {
        string AffectedEntityID "PK"
        string AffectedEntityTypeID "LU"
        string AffectedEntityName
        decimal Longitude
        decimal Latitude
        string IncidentID "FK"
        string RapidAssessment "FK"
        string RapidResponse "FK"
    }

    Lookup_AffectedEntityType {
        string AffectedEntityTypeID "Camp, Infrastructure, Land, Other"
        string AffectedEntityTypeName
    }

    Camp {
        string CampID "PK"
        string CampName
        string CampStatus
        int PopChildren
        int PopMen
        int PopWomen
        string AffectedEntityID "FK"
    }

    Infrastructure {
        string InfrastructureID "PK"
        string InfrastructureName
        string InfrastructureStatus
        string AffectedEntityID "FK"
    }

    Land {
        string LandID "PK"
        string LandName
        string LandStatus
        string AffectedEntityID "FK"
    }

    RapidAssessment {
        string RapidAssessmentID "PK"
        string RapidAssessmentTypeID "LU"
        datetime RapidAssessmentDate
        string AffectedEntityID "FK"
    }

    Lookup_RapidAssessmentType {
        string RapidAssessmentTypeID "HealthAssessment, EducationAssessment, SecurityAssessment, InfrastructureAssessment, LandAssessment"
        string RapidAssessmentTypeName
    }

    HealthAssessment {
        string HealthAssessmentID "PK"
        json HealthAssessmentDataPoints
        string RapidAssessmentID "FK"
    }

    EducationAssessment {
        string EducationAssessmentID "PK"
        json EducationAssessmentDataPoints
        string RapidAssessmentID "FK"
    }

    SecurityAssessment {
        string SecurityAssessmentID "PK"
        json SecurityAssessmentDataPoints
        string RapidAssessmentID "FK"
    }

    InfrastructureAssessment {
        string InfrastructureAssessmentID "PK"
        json InfrastructureAssessmentDataPoints
        string RapidAssessmentID "FK"
    }

    LandAssessment {
        string LandAssessmentID "PK"
        json LandAssessmentDataPoints
        string RapidAssessmentID "FK"
    }

    OtherAssessment {
        string OtherAssessmentID "PK"
        json OtherAssessmentDataPoints
        string RapidAssessmentID "FK"
    }

    RapidResponse {
        string RapidResponseID "PK"
        string RapidAssessmentTypeID "LU"
        datetime RapidResponseDate
        string AffectedEntityID "FK"
        string RapidAssessmentID "FK"
    }

    Lookup_RapidResponseType {
        string RapidAssessmentTypeID "HealthResponse, EducationResponse, SecurityResponse, InfrastructureResponse, LandResponse"
        string RapidAssessmentTypeName
    }

    HealthResponse {
        string HealthResponseID "PK"
        json HealthResponseDataPoints
        string RapidResponseID "FK"
    }

    EducationResponse {
        string EducationResponseID "PK"
        json EducationResponseDataPoints
        string RapidResponseID "FK"
    }

    SecurityResponse {
        string SecurityResponseID "PK"
        json SecurityResponseDataPoints
        string RapidResponseID "FK"
    }

    InfrastructureResponse {
        string InfrastructureResponseID "PK"
        json InfrastructureResponseDataPoints
        string RapidResponseID "FK"
    }

    LandResponse {
        string LandResponseID "PK"
        json LandResponseDataPoints
        string RapidResponseID "FK"
    }

    OtherResponse {
        string OtherResponseID "PK"
        json OtherResponseDataPoints
        string RapidResponseID "FK"
    }

    Incident }|--|| Lookup_IncidentType : "Many-to-One"
    Incident ||--|{ RapidAssessment : "One-to-Many"
    RapidAssessment }|--|| AffectedEntity : "Many-to-One"
    AffectedEntity ||--|{ RapidResponse : "One-to-Many"
    RapidAssessment ||--|{ RapidResponse : "One-to-Many"

    RapidAssessment }|--|| Lookup_RapidAssessmentType : "Many-to-One"
    RapidAssessment }|--|| HealthAssessment : "Many-to-One"
    RapidAssessment }|--|| EducationAssessment : "Many-to-One"
    RapidAssessment }|--|| SecurityAssessment : "Many-to-One"
    RapidAssessment }|--|| InfrastructureAssessment : "Many-to-One"
    RapidAssessment }|--|| LandAssessment : "Many-to-One"
    RapidAssessment }|--|| OtherAssessment : "Many-to-One"

    AffectedEntity }|--|| Lookup_AffectedEntityType : "Many-to-One"
    AffectedEntity }|--|| Camp : "Many-to-One"
    AffectedEntity }|--|| Infrastructure : "Many-to-One"
    AffectedEntity }|--|| Land : "Many-to-One"

    RapidResponse }|--|| Lookup_RapidResponseType : "Many-to-One"
    RapidResponse }|--|| HealthResponse : "Many-to-One"
    RapidResponse }|--|| EducationResponse : "Many-to-One"
    RapidResponse }|--|| SecurityResponse : "Many-to-One"
    RapidResponse }|--|| InfrastructureResponse : "Many-to-One"
    RapidResponse }|--|| LandResponse : "Many-to-One"
    RapidResponse }|--|| OtherResponse : "Many-to-One"


```
