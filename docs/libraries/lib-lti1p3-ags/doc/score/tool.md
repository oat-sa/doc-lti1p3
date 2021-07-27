# AGS Tool - Score service client

> How to use the [ScoreServiceClient](https://github.com/oat-sa/lib-lti1p3-ags/blob/master/src/Service/Score/Client/ScoreServiceClient.php) to perform authenticated AGS scores publications as a tool.

## Features

This library provides a [ScoreServiceClient](https://github.com/oat-sa/lib-lti1p3-ags/blob/master/src/Service/Score/Client/ScoreServiceClient.php) (based on the [core LtiServiceClient](https://github.com/oat-sa/lib-lti1p3-core/blob/master/doc/service/service-client.md)) that allow scores publications as a tool.

## Usage

To publish a score:

```php
<?php

use OAT\Library\Lti1p3Ags\Model\Score\Score;
use OAT\Library\Lti1p3Ags\Service\Score\Client\ScoreServiceClient;
use OAT\Library\Lti1p3Core\Registration\RegistrationRepositoryInterface;

// Related registration
/** @var RegistrationRepositoryInterface $registrationRepository */
$registration = $registrationRepository->find(...);

$scoreClient = new ScoreServiceClient();

$score = new Score(...);

$isPublished = $scoreClient->publishScore(
    $registration,                                      // [required] as the tool, it will call the platform of this registration
    $score,                                             // [required] AGS score to publish
    'https://example.com/ags/contexts/1/lineitems/1'    // [required] AGS line item url to publish the score to
);

// Check score publication success
if ($isPublished) {
    // Publication success
}
```

**Notes**:

- you can use the method `publishScoreForClaim()` to work directly with an [AGS claim](https://github.com/oat-sa/lib-lti1p3-core/blob/master/src/Message/Payload/Claim/AgsClaim.php) received at launch
- you can use the method `publishScoreForPayload()` to work directly with an [LTI message payload](https://github.com/oat-sa/lib-lti1p3-core/blob/master/src/Message/Payload/LtiMessagePayloadInterface.php) received at launch
- you can use the [ScoreFactory](../../src/Factory/Score/ScoreFactory.php) to ease your score creation
