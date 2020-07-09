<img src="https://d32exi8v9av3ux.cloudfront.net/static/images/luno-email-336.png">

# Luno API [![GoDoc](https://godoc.org/github.com/luno/luno-go?status.png)](https://godoc.org/github.com/luno/luno-go) [![Build Status](https://travis-ci.org/luno/luno-go.svg?branch=master)](https://travis-ci.org/luno/luno-go)

This Go package provides a wrapper for the [Luno API](https://www.luno.com/api).

### Documentation

Please visit [godoc.org](https://godoc.org/github.com/luno/luno-go) for the full
package documentation.

### Authentication

Please visit the [Settings](https://www.luno.com/wallet/settings/api_keys) page
to generate an API key.

### Installation

```
go get github.com/luno/luno-go
```

### Example usage

A full working example of this library in action.

```go
package main

import luno "github.com/luno/luno-go"
import (
  "log"
  "context"
  "time"
)

lunoClient := luno.NewClient()
lunoClient.SetAuth("<API_KEY_ID>", "<API_KEY_SECRET>")

req := luno.GetOrderBookRequest{Pair: "XBTZAR"}
ctx, cancel := context.WithDeadline(context.Background(), time.Now().Add(10 * time.Second))
defer cancel()

res, err := lunoClient.GetOrderBook(ctx, &req)
if err != nil {
  log.Fatal(err)
}
log.Println(res)
```

Remember to substitute `<API_KEY_ID>` and `<API_KEY_SECRET>` for your own Id and Secret.

It is also recommended to set these as environment variables rather than include them in plaintext. You can do this on `BASH` with:

```
$ set LUNO_API_ID="<API_KEY_ID>"
$ set LUNO_API_SECRET="<API_KEY_SECRET>"
```

And then access them in Go like so:

```go

import "os"

var API_KEY_ID string = os.Getenv("LUNO_KEY_ID")
var API_KEY_SECRET string = os.Getenv("LUNO_KEY_SECRET")

```


### License

[MIT](https://github.com/luno/luno-go/blob/master/LICENSE.md)
