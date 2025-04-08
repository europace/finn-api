# Finn API
As advisor, I can provide Finn as digital assistant to my customers for a fast and easy financing process.


![advisor](https://img.shields.io/badge/-advisor-lightblue)
![mortgageLoan](https://img.shields.io/badge/-mortgageLoan-lightblue)

[![Authentication](https://img.shields.io/badge/Auth-OAuth2-green)](https://github.com/europace/authorization-api)

[![GitHub release](https://img.shields.io/github/v/release/europace/finn-api)](https://github.com/europace/finn-api/releases)

## Documentation
[![YAML](https://img.shields.io/badge/OAS-YAML-lightgrey)](https://github.com/europace/finn-api/blob/master/finn-openapi.yaml)
[![JSON](https://img.shields.io/badge/OAS-JSON-lightgrey)](https://github.com/europace/finn-api/blob/master/finn-openapi.json)

Feedback and questions about the model are welcome as a [GitHub Issue](https://github.com/europace/finn-api/issues/new).

## Usecases
As an advisor using a CRM tool, you can extend your processes by inviting your customers to Finn in your first contact e-mails.

### Authentication
Please use [![Authentication](https://img.shields.io/badge/Auth-OAuth2-green)](https://docs.api.europace.de/common/authentifizierung/authorization-api/) to get access to the APIs. 

## Create invitation
Creates an invitation for specified case. Returned link (`href`) can be used in emails of advisor to invite customer to Finn. 

Requirements:
- Existing case in BaufiSmart containing at least one applicant with email address, first and last name.
- The Partner-ID your API client is authorized with has to be the advisor (Kundenbetreuer) or editor (Bearbeiter) of the case. (You can change advisor or editor via [Vorgaenge-API](https://docs.api.europace.de/baufinanzierung/vorgaenge/vorgang-auslesen-api/)) 

Example request:
``` http
POST /accounts/v1/cases/{caseId}/invitations
Host: finn.api.europace.de
Content-Type: application/json 
Authorization: Bearer {{access-token}}

{
    "userEmail": "some-user@mail.de"
}
```

Example response:
``` http
201 Created
Content-Type: application/json
{
     "href": "https://meinfinn.de/h6shkjks67dbbjakia0ag",
     "userEmail": "some-user@mail.de",
     "advisorId": "Ab123",
     "caseId": "AB123456",
     "caseOrigin": "baufismart",
     "expiresAt": 1700833943,
     "createdAt": "2023-11-28T10:50:28.532Z",
     "updatedAt": "2023-11-28T10:50:28.532Z"
}
```

## Terms of use
The APIs are provided under the following [Terms of Use](https://docs.api.europace.de/nutzungsbedingungen).

## Support
If you have any questions or problems, you can contact support@meinfinn.de.
