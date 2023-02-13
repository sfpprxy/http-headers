# http-headers
HTTP headers as golang constants

## Install

`go get -u github.com/sfpprxy/http-headers`

## Example

```go
package middleware

import (
	"github.com/gin-gonic/gin"
	"github.com/sfpprxy/http-headers"
	"net/http"
	"time"
)

// NoCache is a middleware function that appends headers
// to prevent the client from caching the HTTP response.
func NoCache(c *gin.Context) {
	// hh is the package name alias for http-headers
	// hh.CacheControl is a constant inside hh package
	c.Header(hh.CacheControl, "no-cache, no-store, max-age=0, must-revalidate, value")
	c.Header(hh.Expires, "Thu, 01 Jan 1970 00:00:00 GMT")
	c.Header(hh.LastModified, time.Now().UTC().Format(http.TimeFormat))
	c.Next()
}
```
