# Chkk API

Tagging a release on this repository will update the:

- [Node.js SDK repo](https://github.com/fern-chkk/chkk-node)
- _More SDKs to come..._

## What is in this repository?

This repository contains

- Chkk's OpenAPI Specification which has been updated to be compatible with Fern to generate SDKs. The updated definition lives in the [definition](./fern/api/definition/) folder
- Generators (see [generators.yml](./fern/api/generators.yml))

## What is in the API Definition?

The API Definition contains information about what endpoints, types, and errors are used in the API. To get the OpenAPI Specification to work with Fern's generators, we refactored inlined types, added an `x-request-name` to each endpoint and updated the `operationId` which is used for code generation in the SDK when generating function names for each endpoint.

To make sure that the definition is valid, you can use the Fern CLI.

```bash
npm install -g fern-api # Installs CLI
fern check # Checks if the definition is valid
```

## What are generators?

Generators read in your API Definition and output artifacts (e.g. the TypeScript SDK Generator) and are tracked in [generators.yml](./fern/api/generators.yml).

To trigger the generators run:

```bash
# output generated files locally
fern generate

# publish generated files
fern generate --group publish --version <version>
```

The publish command currently runs in a GitHub workflow (see [ci.yml](.github/workflows/ci.yml#L32))
