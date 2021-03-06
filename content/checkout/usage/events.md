---
date: 2018-09-17T15:21:22+02:00
title: Events
description: Events.
weight: 6
---

The platform has a collection of internal events that can be configured to trigger webhooks.

Webhooks should always be created with a secure `secret` key. The secret key can be used to identify valid requests to your server. The secret is sent in the Authorization header of the webhook request.

The platform expects a `200 OK` HTTP response when webhooks are called. If a 200 response is not returned, the platform will retry the webhook up to 12 times with a gradually increasing delay between each retry.

Every webhook includes a body containing a JSON object.

```json
{
    "id": 1,
    "event": "event.name",
    "company": "plue_prod",
    "data": {

    }
}
```

The attributes in the above object are described below:

Attribute | Description
--- | ---
id | The unique id of the request. This id is shared between retries of the same request.
event | The event that triggered the webhook
company | The company identifier
data | an object contained different data depending on the event

### Supported events

The following webhook events are supported:

Event | Description
--- | ---
`transaction.execute` | transaction executed (complete/failed) event