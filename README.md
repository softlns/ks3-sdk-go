# ks3-sdk-go

[![License][license-image]][license-url]
[![Go Report Card][report-image]][report-url]
[![Build Status][travis-image]][travis-url]
[![GoDoc][godoc-image]][godoc-url]

This is an  unofficial Go SDK for Kingsoft Cloud KS3 services

## Installation

```bash
go get -u github.com/softlns/ks3-sdk-go

```

## Configuring Credentials

Before using the SDK, ensure that you've configured credentials. One
way you can set it in your program, which might look like:

```go
ks3.New("<accessKey>", "<secretKey>", "<regionName>", ...)
```

Alternatively, you can set the following environment variables:

```
KS3_ACCESS_KEY_ID=MY-ACCESS-KEY
KS3_SECRET_ACCESS_KEY=MY-SECRET-KEY
```

## Using the Go SDK

To use a service in the SDK, create a service variable by calling the `New()`
function. Once you have a service client, you can call API operations which each
return response data and a possible error.

To list a set of buckets from KS3, you could run:

```go
package main

import (
	"fmt"
	"log"

	"github.com/softlns/ks3-sdk-go/ks3"
)

func main() {
	// Your KS3 Access Key.
	accessKey := "<accessKey>"
	// Your KS3 Secret Key.
	secretKey := "<secretKey>"
	// The name of the KS3 region in which you would like to store objects (for example `ks3-cn-beijing`).
	regionName := "<regionName>"
	// Indicates whether to use HTTPS instead of HTTP. A boolean value. The default is true.
	secure := true
	// An internal endpoint or the public endpoint for KS3 access. The default is false.
	internal := false
	// You can change the default endpoint by changing this value.
	regionEndpoint := ""

	client, err := ks3.New(accessKey, secretKey, regionName, secure, internal, regionEndpoint)
	resp, err := client.GetService()

	if err != nil {
		log.Fatal(err)
	}

	log.Print(fmt.Sprintf("%T %+v", resp.Buckets[0], resp.Buckets[0]))
}
```
You can find more information and operations in our
[API documentation][godoc-url].

## Authors

See the [AUTHORS](AUTHORS).

## License

This project is distributed under [Apache License, Version 2.0](LICENSE).



[license-url]: https://www.apache.org/licenses/LICENSE-2.0.html
[license-image]: https://img.shields.io/badge/license-Apache%202-4EB1BA.svg

[report-url]: https://goreportcard.com/report/github.com/softlns/ks3-sdk-go
[report-image]: https://goreportcard.com/badge/github.com/softlns/ks3-sdk-go

[travis-url]: https://travis-ci.org/softlns/ks3-sdk-go
[travis-image]: https://travis-ci.org/softlns/ks3-sdk-go.svg

[godoc-url]: http://godoc.org/github.com/softlns/ks3-sdk-go
[godoc-image]: http://godoc.org/github.com/softlns/ks3-sdk-go?status.png
