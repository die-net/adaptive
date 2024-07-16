Adaptive [![Build Status](https://github.com/die-net/adaptive/actions/workflows/go-test.yml/badge.svg)](https://github.com/die-net/adaptive/actions/workflows/go-test.yml) [![Coverage Status](https://coveralls.io/repos/github/die-net/adaptive/badge.svg?branch=main)](https://coveralls.io/github/die-net/adaptive?branch=main) [![Go Report Card](https://goreportcard.com/badge/github.com/die-net/adaptive)](https://goreportcard.com/report/github.com/die-net/adaptive)
========

The adaptive package is implementation of Client-Side Throttling described in the 
[Handling Overload](https://sre.google/sre-book/handling-overload/) chapter of
Google's [Site Reliability Engineering](https://sre.google/books/) book. 

Rather than traditional circuit breakers which are either closed or open (on
or off) and thus allow all traffic or none client side throttling attempts
to predict what the service can currently handle.  When there have been
recent failures, it attempts to limit requests to some multiple of the
recent successes, such as 2x the number of successful requests in the last
30 seconds.  This better handles overload situations, continuing to allow
some load, and otherwise behaves similarly to a circuit breaker when a
service is completely down.

This is a fork of an
[internal package](https://github.com/grpc/grpc-go/tree/v1.64.0/balancer/rls/internal/adaptive/)
from Google's [grpc-go](https://pkg.go.dev/github.com/grpc/grpc-go),
modified to expose its functionality as public interfaces and not rely on
another internal package.  It retains 100% test coverage.

License
-------

Copyright 2020 gRPC authors.

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at: http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
