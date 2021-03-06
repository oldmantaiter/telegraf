# HTTP Input Plugin

The HTTP input plugin collects metrics from one or more HTTP(S) endpoints.  The endpoint should have metrics formatted in one of the supported [input data formats](../../../docs/DATA_FORMATS_INPUT.md).  Each data format has its own unique set of configuration options which can be added to the input configuration.


### Configuration:

```toml
# Read formatted metrics from one or more HTTP endpoints
[[inputs.http]]
  ## One or more URLs from which to read formatted metrics
  urls = [
    "http://localhost/metrics"
  ]

  ## HTTP method
  # method = "GET"

  ## Optional HTTP headers
  # headers = {"X-Special-Header" = "Special-Value"}

  ## Optional HTTP Basic Auth Credentials
  # username = "username"
  # password = "pa$$word"

  ## Optional SSL Config
  # ssl_ca = "/etc/telegraf/ca.pem"
  # ssl_cert = "/etc/telegraf/cert.pem"
  # ssl_key = "/etc/telegraf/key.pem"
  ## Use SSL but skip chain & host verification
  # insecure_skip_verify = false

  ## Amount of time allowed to complete the HTTP request
  # timeout = "5s"

  ## Data format to consume.
  ## Each data format has its own unique set of configuration options, read
  ## more about them here:
  ## https://github.com/influxdata/telegraf/blob/master/docs/DATA_FORMATS_INPUT.md
  # data_format = "influx"

```

### Metrics:

The metrics collected by this input plugin will depend on the configured `data_format` and the payload returned by the HTTP endpoint(s).

The default values below are added if the input format does not specify a value:

- http
  - tags:
    - url
