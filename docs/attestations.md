# Adding new attestations

This is a quick guide for adding new attestation types to diamond hunt.

## AAS

Follow the usual route for registering a schema with the schema registry.

## Diamond Hunt Proxy

Deploy a rewarder for you attestation (see [example-rewarders]()).
Decide on a *string* name for your attestation.
Enable the schema in the proxy with the name and rewarder.
```
proxy.addAttestationType(name, schemaId, rewarderAddress)
```

## Diamond Hunt Frontend

The frontend is probably the trickiest to get right and ensure the system remains sound. There are a few parts that must be done to enable a new attestation type.

### Config

Add schema ID and schema encoder to _lib/config.ts_
Upload an image for the frontend with the same name as given to the schema when enabling in the proxy.

### Frontend

Add an `AttestationCard` to _pages/index.ts_ for the new attestation.

Add validation functions for the attestation, for example these could be checking if the user already has the attestation or meets certain criteria (such as an external API call). It is important these functions are used both on the client and in the API when signing the attestation.

Add a function to sign the attestation, examples can be found in _lib/signing/*.ts_. It is important when an attestation is signed that no new attestation is signed for the same address withing the `deadline` provided when signing the API. In the passport-frontend application a redis cache is used to cache the signed attestations with a TTL matching the deadline value.

## See also

See the _Makefile_ in the [passport-contracts](https://github.com/avax-attestations/passport-contracts/blob/main/Makefile) repo for examples of using a javascript CLI to create and enable schemas.
