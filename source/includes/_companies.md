# Companies

## Retrieve the company stats for given company id
Returns with an 401 if the user does not belong to the company or isn't an
admin of the company.

```http
GET /company/{company_id} HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
Authorization: Bearer 795665b4-53da-468c-a0d7-ab2d82e58406
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "data": [
     {
       "id": "f7559f2a-8f1c-461e-8a9b-7efea5564edb",
       "type": "companies",
       "attributes": {
         "name": "CompanyMood",
         "anonymous_tracking": false,
         "certificate_active": true,
         "certificate_type": "green",
         "certificate_id": "3d34dbca-ed95-4341-ac59-b4577311784b",
         "created_at": "2015-03-13T11:46:40.196Z",
         "frequency_period": "months",
         "frequency_amount": 3,
         "mood_creation_notification_on": 4,
         "mood_creation_notification_on_hours": 9,
         "mood_creation_notification_on_weeks": 4,
         "mood_creation_reminder_on": 5,
         "mood_creation_reminder_on_hours": 17,
         "mood_creation_reminder_on_weeks": 2,
         "allow_anonymous_suggestions": true,
         "current_tracking_period_start": "2015-03-01",
         "current_tracking_period_end": "2015-03-31",
         "logo_url": "https://cdn.company-mood.com/companies/logos/f8fddbb8ad00bede48a5df91248ca067537a2b7a/main.png"
       }
     }
  ]
}
```

### Response Attributes

Parameter                           | Description
------------------------------------|------------
id                                  | id of the company
name                                | name of the company
anonymous_tracking                  | Does the company track anonymous?
certificate_active                  | Is the companies certificate active?
certificate_type                    | Certificate type ["green", "gold"]
certificate_id                      | The certificated UUID
created_at                          | Timestamp of the company creation
frequency_period                    | Tracking frequency period ["daily", "weeks", "months"]
frequency_amount                    | Tracking frequency amount [1..3]
mood_creation_notification_on       | Weekday for mood creation (notification and creation forcing)
mood_creation_notification_on_hours | Hour for the mood creation (notification and creation forcing)
mood_creation_notification_on_weeks | Week for the mood creation (notification and creation forcing)
mood_creation_reminder_on           | Weekday for mood creation reminder notification
mood_creation_reminder_on_hours     | Hour for the mood creation reminder notification
mood_creation_reminder_on_weeks     | Week for the mood creation reminder notification
allow_anonymous_suggestions         | Is it allowed to create anonymous suggestions for this company? If false, all suggestions will be created with `not_anonymous` set to true.
current_tracking_period_start       | Date when the current tracking period starts
current_tracking_period_end         | Date when the current tracking period ends
logo_url                            | The URL of the company logo. If no custom logo has been uploaded the returned value will be `null`


## Update a company

```http
PUT /companies/{company_id} HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
Authorization: Bearer 795665b4-53da-468c-a0d7-ab2d82e58406
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db

{
  "data": [
     {
       "type": "companies",
       "attributes": {
         "name": "CompanyMood",
         "certificate_active": true,
         "frequency_period": "months",
         "frequency_amount": 3,
         "mood_creation_notification_on": 4,
         "mood_creation_notification_on_hours": 9,
         "mood_creation_notification_on_weeks": 4,
         "mood_creation_reminder_on": 5,
         "mood_creation_reminder_on_hours": 17,
         "mood_creation_reminder_on_weeks": 2,
         "allow_anonymous_suggestions": false
       }
     }
  ]
}
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "data": [
     {
       "id": "f7559f2a-8f1c-461e-8a9b-7efea5564edb",
       "type": "companies",
       "attributes": {
         "name": "CompanyMood",
         "anonymous_tracking": false,
         "certificate_active": true,
         "certificate_type": "green",
         "certificate_id": "3d34dbca-ed95-4341-ac59-b4577311784b",
         "created_at": "2015-03-13T11:46:40.196Z",
         "frequency_period": "months",
         "frequency_amount": 3,
         "mood_creation_notification_on": 4,
         "mood_creation_notification_on_hours": 9,
         "mood_creation_notification_on_weeks": 4,
         "mood_creation_reminder_on": 5,
         "mood_creation_reminder_on_hours": 17,
         "mood_creation_reminder_on_weeks": 2,
         "allow_anonymous_suggestions": false,
         "current_tracking_period_start": "2015-03-01",
         "current_tracking_period_end": "2015-03-31",
         "logo_url": "https://cdn.company-mood.com/companies/logos/f8fddbb8ad00bede48a5df91248ca067537a2b7a/main.png"
       }
     }
  ]
}
```

### PUT Attributes

Parameter                           | Description
------------------------------------|------------
name                                | name of the company
certificate_active                  | Is the companies certificate active?
frequency_period                    | Tracking frequency period ["daily" | "weeks" | "months"]
frequency_amount                    | Tracking frequency amount [1..3]
mood_creation_notification_on       | Weekday for mood creation (notification and creation forcing)
mood_creation_notification_on_hours | Hour for the mood creation (notification and creation forcing)
mood_creation_notification_on_weeks | Week for the mood creation (notification and creation forcing)
mood_creation_reminder_on           | Weekday for mood creation reminder notification
mood_creation_reminder_on_hours     | Hour for the mood creation reminder notification
mood_creation_reminder_on_weeks     | Week for the mood creation reminder notification
allow_anonymous_suggestions         | Is it allowed to create anonymous suggestions for this company? If false, all suggestions will be created with `not_anonymous` set to true.

### Response Attributes

Parameter                           | Description
------------------------------------|------------
id                                  | id of the company
name                                | name of the company
anonymous_tracking                  | Does the company track anonymous?
certificate_active                  | Is the companies certificate active?
certificate_type                    | Certificate type ["green" | "gold"]
certificate_id                      | The certificated UUID
created_at                          | Timestamp of the company creation
frequency_period                    | Tracking frequency period ["daily" | "weeks" | "months"]
frequency_amount                    | Tracking frequency amount [1..3]
mood_creation_notification_on       | Weekday for mood creation (notification and creation forcing)
mood_creation_notification_on_hours | Hour for the mood creation (notification and creation forcing)
mood_creation_notification_on_weeks | Week for the mood creation (notification and creation forcing)
mood_creation_reminder_on           | Weekday for mood creation reminder notification
mood_creation_reminder_on_hours     | Hour for the mood creation reminder notification
mood_creation_reminder_on_weeks     | Week for the mood creation reminder notification
allow_anonymous_suggestions         | Is it allowed to create anonymous suggestions for this company? If false, all suggestions will be created with `not_anonymous` set to true.
current_tracking_period_start       | Date when the current tracking period starts
current_tracking_period_end         | Date when the current tracking period ends
logo_url                            | The URL of the company logo. If no custom logo has been uploaded the returned value will be `null`
