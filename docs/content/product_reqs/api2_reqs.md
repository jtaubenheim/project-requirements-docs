---
title: API Version 2 REST / GraphQL / API Gateway
tags: [api2]
permalink: api2_reqs.html
---

## REST

It is **recommended** that the next API version that Scale makes available also comes with API specifications. This document is an attempt to capture and resolve ambiguity in v1 of the API, and make stronger guarantees in v2.

## API Gateway

One possibility for moving forward is an API gateway. In an ideal world, one of these API services would allow components to expose user facing and QE testable code without being tied to a different component's release schedule.


[KrakenD](https://www.krakend.io/)

[Tyk.io](https://tyk.io/)

## Tenents of API v2

Scale will strive to define every reasonable behavior of an API.  Any behavior not specifically defined will be considered undefined. No tests will be written to enforce behaviors that are undefined. Breakages due to a dependency on an undefined behavior will be considered a bug in the client.

A defined behavior will be recorded in this document and have automated tests written to guarantee behavior.

Undefined behaviors may be added to an existing API. These may be requested by API clients or added by Scale.

## Undefined Behavior - Needs to be Defined

- What changes can be made live, what changes require vms to be offline?
- When a GET API call is made and there are 0 results, should the result be an empty array or an exception?
- Are the top level states of the node/cluster relevant to what APIs are available?
- What standard parameters and behaviors should exist for [Read Filters](https://github.lab.local/dev/scaled/issues/552)
- Should scaled serve a [REST API directly](https://github.com/RGPaul/rest-server-cpp)?
- Should we use a [rest API gateway](https://github.com/Kong/kong https://tyk.io/)?
- Should we maintain our own [Python](https://blog.ovhcloud.com/openapi-with-python-a-state-of-the-art-and-our-latest-contribution/)?


## V2 Rollout

Generally when we launch an API version, that version should be frozen. Bug fixes and enhancements requested for version X should be created, shipped and tested in X+1. One workable solution for this would be to have endpoint X pass through to X-1 on day 1, then iterate from there.
