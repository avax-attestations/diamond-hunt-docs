# Welcome to Diamond Hunt Docs

AAS Social credit system

## About

Diamond hunt is a on chain social credit system. The credits are awarded with a
Diamond ERC20 token to users who recieve attestations based on interacting with
avalanche projects.

The projects has two github repositories:

* [passport-contracts](https://github.com/avax-attestations/passport-contracts) contains the solidity contracts and a client library for interacting with them and creating schemas
* [passport-frontend](https://github.com/avax-attestations/passport-frontend/) contains both the frontend and API for signing attestations

## How it works

Instead of the usual attestation flow where an EOA attests something for a
recipient address the diamond hunt application uses a proxy contract to make the
attestations. This allows end users to submit transactions (and pay for gas).
The diamond hunt proxy only accepts attestations with a corresponding EIP712
signature from a trusted EOA address. The signed attestations are created by a
web app with the private key of the trusted signing address. Upon succesful
attestation the proxy mints an amount of diamonds to the attestation recipient.

## Whats next

You can read about the [Architecture](architecture.md) to gain a deeper insight
into how the system works. The [Attestations](attestations.md) page has a guide
for expanding the system by adding new attestations types. The
[Deployment](deployment.md) page contains information about the CI/CD process
for deploying updates. The [Contracts](contracts.md) page contains addresses for
all deployed contracts and ID's of schemas.
