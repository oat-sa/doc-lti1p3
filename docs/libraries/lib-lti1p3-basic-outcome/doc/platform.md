# Basic Outcome Platform - Basic Outcome Service Server

> How to use the [BasicOutcomeServiceServerRequestHandler](https://github.com/oat-sa/lib-lti1p3-basic-outcome/blob/master/src//Service/Server/Handler/BasicOutcomeServiceServerRequestHandler.php) (with the core [LtiServiceServer](https://github.com/oat-sa/lib-lti1p3-core/blob/master/src/Service/Server/LtiServiceServer.php)) to serve authenticated Basic Outcome service endpoints as a platform.

## Features

This library provides a [BasicOutcomeServiceServerRequestHandler](https://github.com/oat-sa/lib-lti1p3-basic-outcome/blob/master/src//Service/Server/Handler/BasicOutcomeServiceServerRequestHandler.php) ready to be use with the core [LtiServiceServer](https://github.com/oat-sa/lib-lti1p3-core/blob/master/src/Service/Server/LtiServiceServer.php) to handle basic outcome operations.

- it accepts a [PSR7 ServerRequestInterface](https://www.php-fig.org/psr/psr-7/#321-psrhttpmessageserverrequestinterface) containing the basic outcome request,
- leverages the [required IMS LTI 1.3 service authentication](https://www.imsglobal.org/spec/security/v1p0/#securing_web_services),
- and returns a [PSR7 ResponseInterface](https://www.php-fig.org/psr/psr-7/#33-psrhttpmessageresponseinterface) containing the basic outcome response

## Usage

First, you need to provide a [BasicOutcomeServiceServerProcessorInterface](https://github.com/oat-sa/lib-lti1p3-basic-outcome/blob/master/src//Service/Server/Processor/BasicOutcomeServiceServerProcessorInterface.php) implementation, in charge to process the basic outcome operations.

```php
<?php

use OAT\Library\Lti1p3BasicOutcome\Service\Server\Processor\BasicOutcomeServiceServerProcessorInterface;
use OAT\Library\Lti1p3BasicOutcome\Service\Server\Processor\Result\BasicOutcomeServiceServerProcessorResult;
use OAT\Library\Lti1p3Core\Registration\RegistrationInterface;

/** @var BasicOutcomeServiceServerProcessorInterface $processor */
$processor = new class() implements BasicOutcomeServiceServerProcessorInterface 
{
    public function processReadResult(
        RegistrationInterface $registration,
        string $sourcedId
    ) : BasicOutcomeServiceServerProcessorResult {
        // @todo: Logic for readResult basic outcome operations
    }

    public function processReplaceResult(
        RegistrationInterface $registration,
        string $sourcedId,
        float $score,
        string $language = 'en'
    ) : BasicOutcomeServiceServerProcessorResult {
        // @todo: Logic for replaceResult basic outcome operations
    }

    public function processDeleteResult(
        RegistrationInterface $registration,
        string $sourcedId
    ) : BasicOutcomeServiceServerProcessorResult {
        // @todo: Logic for deleteResult basic outcome operations
    }
};
```

Then:

- you can construct the [BasicOutcomeServiceServerRequestHandler](https://github.com/oat-sa/lib-lti1p3-basic-outcome/blob/master/src//Service/Server/Handler/BasicOutcomeServiceServerRequestHandler.php) (constructed with your [BasicOutcomeServiceServerProcessorInterface](https://github.com/oat-sa/lib-lti1p3-basic-outcome/blob/master/src//Service/Server/Processor/BasicOutcomeServiceServerProcessorInterface.php) implementation)
- to finally expose it to requests using the core [LtiServiceServer](https://github.com/oat-sa/lib-lti1p3-core/blob/master/src/Service/Server/LtiServiceServer.php) (constructed with the [RequestAccessTokenValidator](https://github.com/oat-sa/lib-lti1p3-core/blob/master/src/Security/OAuth2/Validator/RequestAccessTokenValidator.php), from core library)

```php
<?php

use OAT\Library\Lti1p3BasicOutcome\Service\Server\Handler\BasicOutcomeServiceServerRequestHandler;
use OAT\Library\Lti1p3BasicOutcome\Service\Server\Processor\BasicOutcomeServiceServerProcessorInterface;
use OAT\Library\Lti1p3Core\Registration\RegistrationRepositoryInterface;
use OAT\Library\Lti1p3Core\Security\OAuth2\Validator\RequestAccessTokenValidator;
use OAT\Library\Lti1p3Core\Service\Server\LtiServiceServer;
use Psr\Http\Message\ServerRequestInterface;

/** @var ServerRequestInterface $request */
$request = ...

/** @var RegistrationRepositoryInterface $repository */
$repository = ...

/** @var BasicOutcomeServiceServerProcessorInterface $processor */
$processor = ...

$validator = new RequestAccessTokenValidator($repository);

$handler = new BasicOutcomeServiceServerRequestHandler($processor);

$server = new LtiServiceServer($validator, $handler);

// Generates a response containing the basic outcome operation result
$response = $server->handle($request);
```
