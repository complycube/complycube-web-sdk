# ComplyCube Example Website

This repository provides a basic html website that uses the ComplyCube SDK. It guides you through the ComplyCube identity verification process, which includes collecting client ID documents, proof of address documents, and biometric selfies.

## To run the website

### Generating an SDK token

Before using the ComplyCube SDK, you will need to generate an SDK token. This involves [creating a client](https://docs.complycube.com/documentation/guides/web-sdk-quick-guide/integration-guide#create-a-client) and [generating a token](https://docs.complycube.com/documentation/guides/web-sdk-quick-guide/integration-guide#generate-an-sdk-token). Follow the documentation in the links or the simple steps below.

1. A client represents the individual for whom you need to perform various KYC checks.  A client is required to generate an SDK token. This must be done in your backend server:

   ```bash
   curl -X POST https://api.complycube.com/v1/clients \
     -H 'Authorization: <YOUR_API_KEY>' \
     -H 'Content-Type: application/json' \
     -d '{
          "type": "person",
          "email": "john.doe@example.com",
          "personDetails":{
               "firstName": "John",
               "lastName" :"Doe"
          }
        }'
   ```

   Example response:
   ```bash
   {
      "id": "5eb04fcd0f3e360008035eb1",
      "type": "person",
      "email": "john.doe@example.com",
      "personDetails": {
          "firstName": "John",
          "lastName": "Doe",
      },
      "createdAt": "2020-01-04T17:24:29.146Z",
      "updatedAt": "2020-01-04T17:24:29.146Z"
   }  
   ```

3. SDK Tokens enable clients to securely send personal data from your web application's frontend to ComplyCube:

   ```bash
   curl -X POST https://api.complycube.com/v1/tokens \
     -H 'Authorization: <YOUR_API_KEY>' \
     -H 'Content-Type: application/json' \
     -d '{
          "clientId": "CLIENT_ID",
          "referrer": "https://www.example.com/*"
        }'
   ```

   Example response:
   ```bash
   {
      "token": "<CLIENT_TOKEN>"
   }  
   ```
   
### Serving the website

Once you have generated your SDK token, open `complycube-web-sdk/index.html` in your code editor of choice. Go to line 42 and change `<SDK_TOKEN>` to the token you have just generated.

You can use any method to serve up the `index.html` file. We recommend using the [Live Server VS Code extension](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) to anyone using VS Code.

## Integrating our SDK

For detailed instructions on integrating our SDK, please refer to our [integration guide](https://docs.complycube.com/documentation/guides/web-sdk-quick-guide/integration-guide).

For an overview of our core platform and its multiple features, please refer to our [user guide](https://docs.complycube.com) or browse the [API reference](https://docs.complycube.com/api-reference) for fine-grained documentation of all our services.


## About ComplyCube

[ComplyCube](https://www.complycube.com/en), an award-winning SaaS & API platform, offers innovative Identity Verification (IDV), Anti-Money Laundering (AML), and Know Your Customer (KYC) compliance solutions. Its extensive customer base spans several industries, such as financial services, transport, healthcare, e-commerce, cryptocurrency, FinTech, and telecoms, making ComplyCube a leading figure in the IDV space.
<br>
<br>
This ISO-certified platform is notable for its quick omnichannel integration and a wide range of services. It provides Low/No-Code solutions, robust API, Mobile SDKs, Client Libraries, and smooth CRM integrations.
