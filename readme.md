# Lobbipad API docs

This repository contains documentation for the Lobbipad company REST API (below) and [webhook API](webhooks.md).

If you need any features which are missing in this API or find any issues, please email us at support@lobbipad.com or file an issue on this repository. If you are in doubt if the issue can be security related, please disclose it in private (support@lobbipad.com) first.

# REST API

## Authentication
You can generate a token in the web dashboard of your account. Log into your account and visit the [API settings page](https://lobbipad.com/settings/api).
This will act as a substitute for a username and password pair. You can revoke this token at all times in your API settings in your account.

__For example__
Replace `$TOKEN` by your actual token or export it as an environment variable.

```bash
curl -X GET -H "Authorization: Bearer $TOKEN" "https://lobbipad.com/api/v1/visits/today"
```
## API Methods
All API methods are exposed under https://lobbipad.com/api/v1/. The API is not available via unencrypted HTTP.

# Get today's visits

```
GET /api/v1/visits/today
```

The API will return a JSON array of your company's visits of the current day.
