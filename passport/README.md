---
title: Passport
permalink: /passport/
---

| Github   | [https://github.com/dadi/passport](https://github.com/dadi/passport) |
| NPM      | [npm install @dadi/passport](https://www.npmjs.com/package/@dadi/passport) |

## Overview

DADI Passport is a library for generating access tokens to authenticate with DADI platform components.

Various components within the DADI stack implement 2-legged oAuth2, requiring a bearer token to authorise requests. This bearer token is obtained as a response sent to a specific endpoint with a clientId/secret pair, along with a TTL defined by the provider.

This library can be used by third-party applications that wish to integrate with DADI, as it abstracts the oAuth protocol by storing and requesting bearer tokens as needed, and returning always a promise with a valid bearer token.

## Contents

### Overview

* [Token wallets](./tokenWallets.md)
* [Development](./development.md)
* [License](./license.md)
* [GPL](./gpl.md)

### Node.js

* [Requirements](./node/requirements.md)
* [Installation](./node/installation.md)
* [Usage examples](./node/usageExamples.md)
* [Testing](./node/testing.md)

### PHP

* [Requirements](./php/requirements.md)
* [Installation](./php/installation.md)
* [Usage examples](./php/usageExamples.md)
* [Testing](./php/testing.md)

## Core contributors

* Eduardo Bouças