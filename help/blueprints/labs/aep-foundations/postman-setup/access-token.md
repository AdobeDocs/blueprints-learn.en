---
hold: true
title: Access token
description: Generate an OAuth server-to-server access token in Postman and understand the required headers for authenticating AEP API calls.
doc-type: article
solution: Experience Platform
exl-id: e38a1bd4-5a09-40c6-8303-c3770801c864
---

# Access token

## API security overview



To establish a secure API connection to an Adobe product Adobe provides the creation of an OAuth server-to-server credential. To do so you must first create a developer project within the Adobe Developer Console. In order to have access to the Developer Console you must have been assigned Developer Rights within the Adobe Admin Console. Once you have these rights you can create developer projects utilizing the various Adobe product related APIs. This is where the OAuth Server-to-Server credential comes into play. To generate an access token you must pass a certain set of claims to Adobe's Identity Management Service (IMS). For OAuth server-to-server credentials an example call would look like so:

```curl
curl -X POST 'https://ims-na1.adobelogin.com/ims/token/v3?client_id={CLIENT_ID}' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'client_secret={CLIENT_SECRET}&grant_type=client_credentials&scope={SCOPE}'
```

>[!NOTE]
>
>You can learn more about the e2e process for creating the developer project using OAuth Server-to-Server credentials [here](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/#generate-access-tokens). For the bootcamp we will "hand wave" this step of the process 😄



## Adobe Experience Platform + Adobe IMS

Every request to any Adobe service must include the access token in the Authorization header along with the Client Secret that was generated during the developer project creation. Additionally, the Experience Platform and its associated applications require two other header params are present on each request.

- `x-gw-ims-org-id` - this param specifies the `IMS Org` that the request belongs to and ensures the processing of the requests resolves to the appropriate SaaS environment
- `x-sandbox-name` - this param specifies which sandbox to process the request in within the Experience Platform

Now that you understand a little bit about how Adobe secures its APIs and what is required to work with them, use them now.

>[!CAUTION]
>
>Not specifying the `x-sandbox-name` param does not fail the request as you might expect. Instead it defaults the request to process into the `default` sandbox that is automatically provisioned with any Experience Platform environment

>[!NOTE]
>
>As part of this bootcamp we created a developer project and provided you a Postman Environment file with all of the necessary values to request an `access_token`. This is what you uploaded in the previous steps of the lab

## Authenticate with Postman

1. Launch Postman and navigate to the directory titled `IMS Authenticate` and open the request by clicking on it
1. Next in the upper right corner of Postman you see an environment drop-down. Select the `AEP Bootcamp` environment from the drop-down
1. Now execute the call by clicking the “Send” button

![Postman request after sending the IMS Authenticate call to generate an access token](assets/access-token-execute-ims-authenticate-request.png)

A successful response should look like this:

```none
200 OK Successful Authentication
```

Successful Response

```json
{
    "token_type": "bearer",
    "access_token": "<value>",
    "expires_in": 86399979
}
```

`token_type` - always will be of type bearer

`access_token` - proves authorization and required in the authorization header of all API calls

`expires_in` - milliseconds until the access token expires (24hrs expiration period today)

>[!TIP]
>
>Congratulations! You've successfully authenticated and your access\_token is now saved to your environment file



## Common errors

### Invalid token

This occurs when the `private_key` in your environment file is malformed or no longer valid. If you see this ensure you have copied the entire key, including the line breaks

Example:

```none
-----BEGIN PRIVATE KEY----- 
some uber long varchar set is here
-----END PRIVATE KEY----- 
```

```none
400 invalid_token
```

>[!NOTE]
>
>Only applicable when using JWT based auth

### Invalid IMS\_ORG

This error occurs when you forget to set your postman environment from the drop-down

![IMS_ORG not found in active environment error when no Postman environment is selected](assets/access-token-forgot-to-select-postman-environment.png)

>[!NOTE]
>
>Don't forget to set your postman environment when executing API calls
>
>![Selecting the AEP Bootcamp environment from the Postman environment drop-down](assets/access-token-set-postman-environment.png)
