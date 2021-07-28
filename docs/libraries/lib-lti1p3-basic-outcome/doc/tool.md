# Basic Outcome Tool - Basic Outcome Service Client

> How to use the [BasicOutcomeServiceClient](https://github.com/oat-sa/lib-lti1p3-basic-outcome/blob/master/src//Service/Client/BasicOutcomeServiceClient.php) to perform authenticated basic outcome service calls as a tool.

## Features

This library provides a [BasicOutcomeServiceClient](https://github.com/oat-sa/lib-lti1p3-basic-outcome/blob/master/src//Service/Client/BasicOutcomeServiceClient.php) (based on the [LtiServiceClient](https://github.com/oat-sa/lib-lti1p3-core/blob/master/doc/service/service-client.md)) that allow the following outcome operations:

- [read result](https://www.imsglobal.org/spec/lti-bo/v1p1#readresult)
- [replace result](https://www.imsglobal.org/spec/lti-bo/v1p1#replaceresult)
- [delete result](https://www.imsglobal.org/spec/lti-bo/v1p1#deleteresult)

## Usage

### Read a result

```php
<?php

use OAT\Library\Lti1p3BasicOutcome\Service\Client\BasicOutcomeServiceCLient;
use OAT\Library\Lti1p3Core\Message\Payload\LtiMessagePayloadInterface;
use OAT\Library\Lti1p3Core\Registration\RegistrationRepositoryInterface;

// Related registration
/** @var RegistrationRepositoryInterface $registrationRepository */
$registration = $registrationRepository->find(...);

// Related LTI 1.3 message payload
/** @var LtiMessagePayloadInterface $payload */
$payload  = ...;

$client = new BasicOutcomeServiceCLient();

$response = $client->readResultForPayload(
    $registration, // [required] as the tool, it will call the platform of this registration
    $payload       // [required] for the LTI message payload containing the basic outcome claim result sourced id (got at LTI launch)
);

// you also can directly read a result for a given basic outcome claim
$response = $client->readResultForClaim(
    $registration,               // [required] as the tool, it will call the platform of this registration
    $payload->getBasicOutcome()  // [required] for the basic outcome claim result sourced id (got at LTI launch)
);

// or you also can directly read a result from given URL and result sourced id
$response = $client->readResult(
    $registration,                         // [required] as the tool, it will call the platform of this registration
    'https://example.com/basic-outcome',   // [required] to a given basic outcome service url
    'resultSourcedId'                      // [required] for a given result sourced id
);

if ($response->isSuccess()) {
    // you can access the score
    $score = $response->getScore();

    // you can access the language
    $language = $response->getLanguage();

    // you can access the description of the operation
    $description = $response->getDescription();

    // you can also access if needed basic outcome response metadata
    $identifier = $response->getIdentifier();
    $refIdentifier = $response->getReferenceRequestIdentifier();
    $refType = $response->getReferenceRequestType();
}
```

### Replace a result

```php
<?php

use OAT\Library\Lti1p3BasicOutcome\Service\Client\BasicOutcomeServiceCLient;
use OAT\Library\Lti1p3Core\Message\Payload\LtiMessagePayloadInterface;
use OAT\Library\Lti1p3Core\Registration\RegistrationRepositoryInterface;

// Related registration
/** @var RegistrationRepositoryInterface $registrationRepository */
$registration = $registrationRepository->find(...);

// Related LTI 1.3 message payload
/** @var LtiMessagePayloadInterface $payload */
$payload  = ...;

$client = new BasicOutcomeServiceCLient();

$response = $client->replaceResultForPayload(
    $registration, // [required] as the tool, it will call the platform of this registration
    $payload,      // [required] for the LTI message payload containing the basic outcome claim result sourced id (got at LTI launch)
    0.42,          // [required] for a given score
    'en'           // [optional] for a given language
);

// you also can directly replace a result for a given basic outcome claim, score and language
$response = $client->replaceResultForClaim(
    $registration,                // [required] as the tool, it will call the platform of this registration
    $payload->getBasicOutcome(),  // [required] for the basic outcome claim result sourced id (got at LTI launch)
    0.42,                         // [required] for a given score
    'en'                          // [optional] for a given language
);

// or you also can directly replace a result on given URL, result sourced id, score and language
$response = $client->replaceResult(
    $registration,                         // [required] as the tool, it will call the platform of this registration
    'https://example.com/basic-outcome',   // [required] to a given basic outcome service url
    'resultSourcedId',                     // [required] for a given result sourced id
    0.42,                                  // [required] for a given score
    'en'                                   // [optional] for a given language
);

if ($response->isSuccess()) {
    // you can access the description of the operation
    $description = $response->getDescription();

    // you can also access if needed basic outcome response metadata
    $identifier = $response->getIdentifier();
    $refIdentifier = $response->getReferenceRequestIdentifier();
    $refType = $response->getReferenceRequestType();
}
```

### Delete a result

```php
<?php

use OAT\Library\Lti1p3BasicOutcome\Service\Client\BasicOutcomeServiceCLient;
use OAT\Library\Lti1p3Core\Message\Payload\LtiMessagePayloadInterface;
use OAT\Library\Lti1p3Core\Registration\RegistrationRepositoryInterface;

// Related registration
/** @var RegistrationRepositoryInterface $registrationRepository */
$registration = $registrationRepository->find(...);

// Related LTI 1.3 message payload
/** @var LtiMessagePayloadInterface $payload */
$payload  = ...;

$client = new BasicOutcomeServiceCLient();

$response = $client->deleteResultForPayload(
    $registration, // [required] as the tool, it will call the platform of this registration
    $payload       // [required] for the LTI message payload containing the basic outcome claim result sourced id (got at LTI launch)
);

// you also can directly delete a result for a given basic outcome claim
$response = $client->deleteResultForClaim(
    $registration,                // [required] as the tool, it will call the platform of this registration
    $payload->getBasicOutcome()   // [required] for the basic outcome claim result sourced id (got at LTI launch)
);

// or you also can directly delete a result on given URL and result sourced id
$response = $client->deleteResult(
    $registration,                         // [required] as the tool, it will call the platform of this registration
    'https://example.com/basic-outcome',   // [required] to a given basic outcome service url
    'resultSourcedId'                      // [required] for a given result sourced id
);

if ($response->isSuccess()) {
    // you can access the description of the operation
    $description = $response->getDescription();

    // you can also access if needed basic outcome response metadata
    $identifier = $response->getIdentifier();
    $refIdentifier = $response->getReferenceRequestIdentifier();
    $refType = $response->getReferenceRequestType();
}
```
