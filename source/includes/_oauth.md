# Oauth

## Sign in via google oauth

```http
POST /oauth/google_oauth2 HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db

{
  "data": {
    "type": "oauth",
    "attributes": {
      "id_token": "INSERT ID TOKEN HERE"
    }
  }
}
```

```http
HTTP/1.1 201 CREATED
Content-Type: application/json

{
  "data": {
    "id": "1d7f7eea-b088-46dd-b29c-51ccfa4085e7",
    "type": "users",
    "attributes": {
      "firstname": "John",
      "lastname": "Doe",
      "email": "j.doe1@example.com",
      "locale": "de",
      "image_url": "https://gravatar.com/avatar/829afce351884fcde132544bf9686221",
      "role": "admin",
      "auth_token": "5c3dad26-31a4-4f6d-a799-b3cd9053dc83",
      "company_id": "8f40670c-9927-4712-979f-81a2fa4c7253"
    }
  }
}
```

You can create a new oauth session and get the `auth_token` and other important informations
about the just logged in user by sending a `id_token` to this endpoint.

The returned role can be "admin", "employee" or "department_manager".

### POST Attributes

Paramteter | Description
-----------|------------
id_token   | Request this token from google auth api (see <https://developers.google.com/identity/sign-in/web/sign-in>)

### Response Attributes

Paramteter | Description
-----------|------------
firstname  | Firstname of the sessions user
lastname   | Lastname of the sessions user
email      | Email of the sessions user
locale     | Locale of the sessions user
image_url  | Url to the profile image of the sessions user
role       | Role of the sessions user (`admin`, `department_manager` or `employee`)
auth_token | Auth token for users session, use this for further authorization on endpoints
company_id | ID of the company, the user belongs to. Empty if the user does't belong to a company, yet.