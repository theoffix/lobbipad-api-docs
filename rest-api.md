# Company REST API

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

### Get today's visits

```
GET /api/v1/visits/today
```

The API will return a JSON array of your company's visits of the current day.

### Checkout all the visitors

```
GET /api/v1/visits/search?checkoutall=true
```

The API will checkout all the visitors who has checked in. 

### Hosts Mass Sync

```
POST /api/v1/sync-hosts
```

This endpoint allows you to sync your hosts from a remote system to Lobbipad using an easy CSV format.

#### Input
Our API supports both:
- sending the actual file and as `form-data` using `file` as the property for the actual file
- sending the CSV as raw text body input

An example of the input:

```csv
lastName,email,firstName,telephone
Doe,jane.doe@lobbipad.com,Jane,+32497799277
Doe,john.doe@lobbipad.com,John,+32497799288
```

The input is flexible, as long as the first line is there to show the order you selected, you can interchange the order of the columns to your liking.

#### Feedback

```
POST /api/v1/sync-hosts?waitForResult=true
```

By default you will get a fast response. If you want actual feedback on all items it's possible to opt-in to this feedback. This will take a bit longer though. Opt-in by using the `waitForResult` flag as shown above.

---

If you need any features which are missing in this API or find any issues, please email us at support@lobbipad.com or file an issue on this repository. If you are in doubt if the issue can be security related, please disclose it in private (support@lobbipad.com) first.