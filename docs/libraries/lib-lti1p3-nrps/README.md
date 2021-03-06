# TAO - LTI 1.3 NRPS Library

[![Latest Version](https://img.shields.io/github/tag/oat-sa/lib-lti1p3-nrps.svg?style=flat&label=release)](https://github.com/oat-sa/lib-lti1p3-nrps/tags)
[![License GPL2](http://img.shields.io/badge/licence-GPL%202.0-blue.svg)](http://www.gnu.org/licenses/gpl-2.0.html)
[![Build Status](https://github.com/oat-sa/lib-lti1p3-nrps/actions/workflows/build.yaml/badge.svg?branch=master)](https://github.com/oat-sa/lib-lti1p3-nrps/actions)
[![Test Coverage Status](https://coveralls.io/repos/github/oat-sa/lib-lti1p3-nrps/badge.svg?branch=master)](https://coveralls.io/github/oat-sa/lib-lti1p3-nrps?branch=master)
[![Psalm Level Status](https://shepherd.dev/github/oat-sa/lib-lti1p3-nrps/level.svg)](https://shepherd.dev/github/oat-sa/lib-lti1p3-nrps)
[![Packagist Downloads](http://img.shields.io/packagist/dt/oat-sa/lib-lti1p3-nrps.svg)](https://packagist.org/packages/oat-sa/lib-lti1p3-nrps)
[![IMS Certified](https://img.shields.io/badge/IMS-certified-brightgreen)](https://site.imsglobal.org/certifications/open-assessment-technologies-sa/tao-lti-13-devkit)

> [IMS certified](https://site.imsglobal.org/certifications/open-assessment-technologies-sa/tao-lti-13-devkit) PHP library for [LTI 1.3 Names and Role Provisioning Services](https://www.imsglobal.org/spec/lti-nrps/v2p0) implementations as [platforms and / or as tools](http://www.imsglobal.org/spec/lti/v1p3/#platforms-and-tools), based on [LTI 1.3 Core library](https://github.com/oat-sa/lib-lti1p3-core).

## IMS

You can find below [IMS](https://www.imsglobal.org/) related information.

### Related certifications

- [LTI 1.3 advantage complete](https://site.imsglobal.org/certifications/open-assessment-technologies-sa/tao-lti-13-devkit)

### Related specifications

- [IMS LTI 1.3 Names and Role Provisioning Services](https://www.imsglobal.org/spec/lti-nrps/v2p0)
- [IMS LTI 1.3 Core](http://www.imsglobal.org/spec/lti/v1p3)
- [IMS Security](https://www.imsglobal.org/spec/security/v1p0)

## Installation

```console
$ composer require oat-sa/lib-lti1p3-nrps
```

## Documentation

You can find below the library documentation, presented by topics.

### Configuration

- how to [configure the underlying LTI 1.3 Core library](../lib-lti1p3-core/doc/quickstart/configuration.md)

### Platform

- how to [use the NRPS library as a platform](doc/platform.md)

### Tool

- how to [use the NRPS library as a tool](doc/tool.md)

## Tests

To run tests:

```console
$ vendor/bin/phpunit
```
**Note**: see [phpunit.xml.dist](https://github.com/oat-sa/lib-lti1p3-nrps/blob/master/phpunit.xml.dist) for available test suites.