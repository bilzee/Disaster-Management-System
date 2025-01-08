```mermaid 
erDiagram
    Incident {
        string IncidentID
        string IncidentTypeID
        string IncidentSeverity
        datetime IncidentDate
        string IncidentName
        string AffectedEntityID
    }

    Lookup_IncidentType {
        string IncidentTypeID "FloodIncident, FireIncident, LandslideIncident, CycloneIncident, OtherIncident"
        string IncidentTypeName
    }

    AffectedEntity {
        string AffectedEntityID
        string AffectedEntityTypeID
        string AffectedEntityName
        decimal Longitude
        decimal Latitude
        string IncidentID
        string RapidAssessment
        string RapidResponse
    }

    Lookup_AffectedEntityType {
        string AffectedEntityTypeID "Camp, Infrastructure, Land, Other"
        string AffectedEntityTypeName
    }

    Camp {
        string CampID
        string CampName
        string CampStatus
        int PopChildren
        int PopMen
        int PopWomen
        string AffectedEntityID
    }

    Infrastructure {
        string InfrastructureID
        string InfrastructureName
        string InfrastructureStatus
        string AffectedEntityID
    }

    Land {
        string LandID
        string LandName
        string LandStatus
        string AffectedEntityID
    }

    RapidAssessment {
        string RapidAssessmentID
        string RapidAssessmentTypeID
        datetime RapidAssessmentDate
        string AffectedEntityID
    }

    Lookup_RapidAssessmentType {
        string RapidAssessmentTypeID "HealthAssessment, EducationAssessment, SecurityAssessment, InfrastructureAssessment, LandAssessment"
        string RapidAssessmentTypeName
    }

    HealthAssessment {
        string HealthAssessmentID
        json HealthAssessmentDataPoints
        string RapidAssessmentID
    }

    EducationAssessment {
        string EducationAssessmentID
        json EducationAssessmentDataPoints
        string RapidAssessmentID
    }

    SecurityAssessment {
        string SecurityAssessmentID
        json SecurityAssessmentDataPoints
        string RapidAssessmentID
    }

    InfrastructureAssessment {
        string InfrastructureAssessmentID
        json InfrastructureAssessmentDataPoints
        string RapidAssessmentID
    }

    LandAssessment {
        string LandAssessmentID
        json LandAssessmentDataPoints
        string RapidAssessmentID
    }

    OtherAssessment {
        string OtherAssessmentID
        json OtherAssessmentDataPoints
        string RapidAssessmentID
    }

    RapidResponse {
        string RapidResponseID
        string RapidAssessmentTypeID
        datetime RapidResponseDate
        string AffectedEntityID
        string RapidAssessmentID
    }

    Lookup_RapidResponseType {
        string RapidAssessmentTypeID "HealthResponse, EducationResponse, SecurityResponse, InfrastructureResponse, LandResponse"
        string RapidAssessmentTypeName
    }

    HealthResponse {
        string HealthResponseID
        json HealthResponseDataPoints
        string RapidResponseID
    }

    EducationResponse {
        string EducationResponseID
        json EducationResponseDataPoints
        string RapidResponseID
    }

    SecurityResponse {
        string SecurityResponseID
        json SecurityResponseDataPoints
        string RapidResponseID
    }

    InfrastructureResponse {
        string InfrastructureResponseID
        json InfrastructureResponseDataPoints
        string RapidResponseID
    }

    LandResponse {
        string LandResponseID
        json LandResponseDataPoints
        string RapidResponseID
    }

    OtherResponse {
        string OtherResponseID
        json OtherResponseDataPoints
        string RapidResponseID
    }

    Incident }|--|| Lookup_IncidentType : "*:1"
    Incident }|--|{ AffectedEntity : "*:*"
    AffectedEntity }|--|| Lookup_AffectedEntityType : "*:1"
    AffectedEntity }|--|| Camp : "*:1"
    AffectedEntity }|--|| Infrastructure : "*:1"
    AffectedEntity }|--|| Land : "*:1"
    AffectedEntity ||--|{ RapidAssessment : "1:*"
    RapidAssessment }|--|| Lookup_RapidAssessmentType : "*:1"
    RapidAssessment }|--|| HealthAssessment : "*:1"
    RapidAssessment }|--|| EducationAssessment : "*:1"
    RapidAssessment }|--|| SecurityAssessment : "*:1"
    RapidAssessment }|--|| InfrastructureAssessment : "*:1"
    RapidAssessment }|--|| LandAssessment : "*:1"
    RapidAssessment }|--|| OtherAssessment : "*:1"
    AffectedEntity ||--|{ RapidResponse : "1:*"
    RapidResponse }|--|| Lookup_RapidResponseType : "*:1"
    RapidResponse }|--|| HealthResponse : "*:1"
    RapidResponse }|--|| EducationResponse : "*:1"
    RapidResponse }|--|| SecurityResponse : "*:1"
    RapidResponse }|--|| InfrastructureResponse : "*:1"
    RapidResponse }|--|| LandResponse : "*:1"
    RapidResponse }|--|| OtherResponse : "*:1"
    RapidAssessment ||--|{ RapidResponse : "1:*"

```
