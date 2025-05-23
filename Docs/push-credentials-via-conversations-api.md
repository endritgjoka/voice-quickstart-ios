## Create Push Credentials via the Conversations Credential Resource API

Voice SDK users can manage their Push Credentials in the developer console (**Console > Account > Keys & Credentials > Credentials**). Currently the Push Credential management page only supports the default region (US1). To create or update Push Credentials for other regional (i.e. Australia) usage, developers can use the Conversations public API to manage their Push Credentials. Follow the instructions of the [Credential Resource API](https://www.twilio.com/docs/conversations/api/credential-resource) and replace the endpoint with the regional endpoint, for example https://conversations.dublin.ie1.twilio.com for the Ireland region.

You will also need:
- Apple VoIP Service certificate: follow the [instructions](https://github.com/twilio/voice-quickstart-ios#6-create-a-push-credential-with-your-voip-service-certificate) to get the certificate and key.
- Twilio account credentials: find your API auth token for the specific region in the developer console. Go to **Console > Account > Keys & Credentials > API keys & tokens** and select the region in the dropdown menu.

Example of creating an `IE1` Push Credential for APN:

```
curl -X POST https://conversations.dublin.ie1.twilio.com/v1/Credentials \
--data-urlencode "Type=apn" \
--data-urlencode "Certificate=$(cat $PATH_OF_CERT_PEM)" \
--data-urlencode "PrivateKey=$(cat $PATH_OF_KEY_PEM)" \
--data-urlencode "Sandbox=true" \
-u $TWILIO_ACCOUNT_SID:$TWILIO_AUTH_TOKEN
```

To update a Push Credential (CR****) in `IE1`:

```
curl -X POST https://conversations.dublin.ie1.twilio.com/v1/Credentials/CR**** \
--data-urlencode "Type=apn" \
--data-urlencode "Certificate=$(cat $PATH_OF_CERT_PEM)" \
--data-urlencode "PrivateKey=$(cat $PATH_OF_KEY_PEM)" \
--data-urlencode "Sandbox=true" \
-u $TWILIO_ACCOUNT_SID:$TWILIO_AUTH_TOKEN
```

# Note that currently the Conversations Credential Resource API is not available for the Australia region. Please reach out to the [Twilio Help Center](https://help.twilio.com/) if you need help managing your Push Credentials for the Australia region.
