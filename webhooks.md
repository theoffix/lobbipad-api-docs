# Webhook API (beta)

This repository contains documentation for the Lobbipad Webhook API. If you need any features which are missing in this API or find any issues, please email us at support@lobbipad.com or file an issue on this repository. If you are in doubt if the issue can be security related, please disclose it in private (support@lobbipad.com) first.

You can add your endpoints in the [webhook api settings](https://lobbipad.com/settings/api/webhooks). Endpoints are `https://` only. You can add multiple endpoint URL's.

## Types

We currently only support the following types of events:

- `visits.created`: called when a new visit is created
- `ping`: used for testing / verifying your setup

## Receiving a webhook event

Webhook data is sent as JSON in the POST request body. The body will contain the type and the body. See the example below.

```
{
  "type": "visits.created",
  "data": {
    "foo": "bar",
    "beep": "boop",
    "visitor": {...}
  }
}

// alternatively
{
  "type": "ping",
  "data": {
    "message": "Pinging webhooks for Foobar Inc.",
    "date": "Fri, 01 Jul 2016 11:44:22 GMT"
  }
}
```

You can easily debug the sent responses by temporarily using a service like [hookb.in](https://hookb.in).

## Responding successfully

To respond successful, you need to respond with a `2xx` status code. If this is not the case we will retry the delivery. If your app wasn't able to respond with a status in the `2xx` range within 3 minutes, we will stop trying to deliver the payload.

## Basic authentication
As this is just plain HTTP, you can use [basic authentication](https://en.wikipedia.org/wiki/Basic_access_authentication) to use a shared secret on your endpoint URL.
