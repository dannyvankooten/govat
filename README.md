Package vat
===

[![Go Report Card](https://goreportcard.com/badge/github.com/dannyvankooten/vat)](https://goreportcard.com/report/github.com/dannyvankooten/vat)
[![GoDoc](https://godoc.org/github.com/dannyvankooten/vat?status.svg)](https://godoc.org/github.com/dannyvankooten/vat)
![License](https://img.shields.io/dub/l/vibe-d.svg)

Package for validating VAT numbers & retrieving VAT rates in Go.

## Installation

Use go get.

```
go get github.com/dannyvankooten/vat
```

Then import the package into your own code.

```
import "github.com/dannyvankooten/vat"
```

## Usage

### Validating VAT numbers

VAT numbers can be validated by format, existence or both. VAT numbers are looked up using the [VIES VAT validation API](http://ec.europa.eu/taxation_customs/vies/).

```go
package main

import "github.com/dannyvankooten/vat"

func main() {
  // validates format + existence
  validity := vat.Validate("NL123456789B01")

  // validate format
  validity := vat.ValidateFormat("NL123456789B01")

  // validate existence
  validity := vat.ValidateExistence("NL123456789B01")
}
```

### Retrieving VAT rates

VAT numbers van be validated by format, existence or both.

```go
package main

import (
  "fmt"
  "github.com/dannyvankooten/vat/rates"
)

func main() {
  c, _ := rates.Country("NL")
  r, _ := c.Rate("standard")

  fmt.Printf("Standard VAT rate for NL is %.2f", r)
  // Output: Standard VAT rate for NL is 21.00
}
```

## License

MIT licensed. See the LICENSE file for details.
