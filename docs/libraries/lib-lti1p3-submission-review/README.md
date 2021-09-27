# TAO - LTI 1.3 Submission Review Library

[![Latest Version](https://img.shields.io/github/tag/oat-sa/lib-lti1p3-submission-review.svg?style=flat&label=release)](https://github.com/oat-sa/lib-lti1p3-submission-review/tags)
[![License GPL2](http://img.shields.io/badge/licence-GPL%202.0-blue.svg)](http://www.gnu.org/licenses/gpl-2.0.html)
[![Build Status](https://github.com/oat-sa/lib-lti1p3-submission-review/actions/workflows/build.yaml/badge.svg?branch=main)](https://github.com/oat-sa/lib-lti1p3-submission-review/actions)
[![Tests Coverage Status](https://coveralls.io/repos/github/oat-sa/lib-lti1p3-submission-review/badge.svg?branch=main)](https://coveralls.io/github/oat-sa/lib-lti1p3-submission-review?branch=main)
[![Psalm Level Status](https://shepherd.dev/github/oat-sa/lib-lti1p3-submission-review/level.svg)](https://shepherd.dev/github/oat-sa/lib-lti1p3-submission-review)
[![Packagist Downloads](http://img.shields.io/packagist/dt/oat-sa/lib-lti1p3-submission-review.svg)](https://packagist.org/packages/oat-sa/lib-lti1p3-submission-review)

> PHP library for [LTI 1.3 Submission Review Service](https://www.imsglobal.org/spec/lti-sr/v1p0) implementations as [platforms and / or as tools](http://www.imsglobal.org/spec/lti/v1p3/#platforms-and-tools), based on [LTI 1.3 Core library](https://github.com/oat-sa/lib-lti1p3-core).

# Table of contents

- [TAO LTI 1.3 PHP framework](#tao-lti-13-php-framework)
- [IMS](#ims)
- [Installation](#installation)
- [Documentation](#documentation)
- [Tests](#tests)

## TAO LTI 1.3 PHP framework

This library is part of the [TAO LTI 1.3 PHP framework](https://oat-sa.github.io/doc-lti1p3/).

## IMS

You can find below [IMS](https://www.imsglobal.org/) related information.

### Related specifications

- [IMS LTI Submission Review Service](https://www.imsglobal.org/spec/lti-sr/v1p0)
- [IMS LTI 1.3 Core](http://www.imsglobal.org/spec/lti/v1p3)
- [IMS Security](https://www.imsglobal.org/spec/security/v1p0)

## Installation

```console
$ composer require oat-sa/lib-lti1p3-submission-review
```

## Documentation

You can find below the library documentation, presented by topics.

### Quick start

- how to [configure the underlying LTI 1.3 Core library](../lib-lti1p3-core/doc/quickstart/configuration.md)

### Messages

- how to [implement the submission review message workflow (as platform and / or tool)](doc/message/submission-review-workflow.md)

## Tests

To run tests:

```console
$ vendor/bin/phpunit
```
**Note**: see [phpunit.xml.dist](phpunit.xml.dist) for available test suites.
