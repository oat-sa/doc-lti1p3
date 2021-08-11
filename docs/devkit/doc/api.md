# HTTP API documentation

## Security

Since this development kit can be registered with real LMS production instances, the API HTTP endpoints are **protected by an API key**.

This API key is configurable on the [.env](https://github.com/oat-sa/devkit-lti1p3/blob/master/.env) file, in the `APP_API_KEY` environment variable.

Every API HTTP endpoint request must provide this key as a token bearer via the request header `Authorization: Bearer <token>`.

## HTTP endpoints

You can find below the available API HTTP endpoints offered by the development kit.

!!swagger-http https://raw.githubusercontent.com/oat-sa/devkit-lti1p3/master/doc/openapi/devkit.yaml!!