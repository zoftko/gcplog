# gcplog
Boilerplate to set up `slog` in a way that is compatible with GCP. If you use `slog` with its default settings,
GCP will fail to extract the severity and structured values out of the log. This snippet changes formatting
so that GCP can parse log messages correctly.

## Usage
Simply call `gcplog.Setup()`. Please note this will change the logger in `slog` for a new one. It will also
enable debug logs if the environment variable `DEBUG` is set.

```go
package main

import (
	"github.com/zoftko/gcplog"
	"log/slog"
)

func main() {
	gcplog.Setup()
	slog.Info("GCP will no longer detect this with a default severity", "random-key", "Will be parsed as well")
}
```
