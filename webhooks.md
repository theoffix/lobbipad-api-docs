# Lobbipad webhook API (beta)

This repository contains documentation for the Lobbipad webhook API. If you need any features which are missing in this API or find any issues, please email us at support@lobbipad.com or file an issue on this repository. If you are in doubt if the issue can be security related, please disclose it in private (support@lobbipad.com) first.

You can add your endpoints in the [company api settings](/settings/api/webhooks). Endpoints are `https://` only. You can add multiple endpoint URL's.

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

## Responding succesfully
To respond successful, you need to respond with a `2xx` status code. If this is not the case we will retry the delivery. If your app wasn't able to respond with a status in the `2xx` range within 3 minutes, we will stop trying to deliver the payload.
