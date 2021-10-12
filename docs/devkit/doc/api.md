# HTTP API documentation

## HTTP API security

Since this development kit can be registered with real LMS production instances, the HTTP API endpoints are **protected by an API key**.

This API key is configurable on the [.env](https://github.com/oat-sa/devkit-lti1p3/blob/master/.env) file, in the `APP_API_KEY` environment variable.

Every HTTP API endpoint request must provide this key as a token bearer via the request header `Authorization: Bearer <token>`.

## HTTP API endpoints

The development kit HTTP endpoints are described below (and also available on [the development kit repository](https://github.com/oat-sa/devkit-lti1p3/blob/master/doc/openapi/devkit.yaml)).

!!swagger-http https://raw.githubusercontent.com/oat-sa/devkit-lti1p3/master/doc/openapi/devkit.yaml!!