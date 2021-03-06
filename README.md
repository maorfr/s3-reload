# S3 Reload

**s3-reload** is a simple binary to trigger a reload when an object in an S3 bucket is updated.
It watches the object in the defined path in an S3 bucket and notifies the target process that the object has been changed.
It currently only supports sending an HTTP request.

It is available as a Docker image at https://hub.docker.com/r/maorfr/s3-reload

Uses [maorfr/csnotify](https://github.com/maorfr/csnotify) under the hood.

Inspired by [jimmidyson/configmap-reload](https://github.com/jimmidyson/configmap-reload).

### Usage

```
Usage of ./out/s3-reload:
  -s3-path string
        S3 object path to watch for updates; may be used multiple times (example: s3://my-bucket/path/to/watch)
  -webhook-method string
        the HTTP method url to use to send the webhook (default "POST")
  -webhook-status-code int
        the HTTP status code indicating successful triggering of reload (default 200)
  -webhook-url string
        the url to send a request to when the object in the specified S3 path has been updated
```

### License

This project is [Apache Licensed](LICENSE.txt)

### Credentials

#### AWS

s3-reload uses the default AWS [credentials chain](https://docs.aws.amazon.com/sdk-for-go/v1/developer-guide/configuring-sdk.html).
In addition, the `AWS_REGION` environment variable should be set.
