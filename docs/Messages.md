# Messages API

Service partners can attach messages to cases that can be viewed by
Service provider and exported to their internal systems.

**Note** Mandatory parameters are marked with \* sign.

## POST /api/v2/case-messages/create

Add a new message to specific *Case*.

### Access

Partner, Provider

### Input (request body)


| Name            | Type         | Description                                |
|-----------------|--------------|--------------------------------------------|
| guid\*          | Guid         | Guid of the case                           |
| content         | String       | Message text                               |
| messageType\*   | String(32)   | Message type (always `serviceComment`)     |

### Example

```
{
  "guid": "1e0abcb7-b94c-4072-a9c0-37072a1ef015",
  "content": "Test message",
  "messageType": "serviceComment"
}
```

### Output

```
{
  "id": 1,
  "caseId": 7748,
  "guid": "1e0abcb7-b94c-4072-a9c0-37072a1ef015",
  "senderAccountId": 1009,
  "content": "Test message",
  "messageType": "serviceComment",
  "createdAt": "2017-07-26T14:02:02.170Z",
  "updatedAt": "2017-07-26T14:02:02.170Z"
}
```

## GET /api/v2/case-messages

Get all messages attached to specific *Case*.

### Access

Partner, Provider

### Input:

| Name     | Type   | Description        |
|----------|--------|--------------------|
| guid\*   | Guid   | Guid of the case   |

### Example:

```
/api/v2/case-messages?accessToken=my_key&guid=1e0abcb7-b94c-4072-a9c0-37072a1ef015
```

### Output

```
[
  {
    "id": 1,
    "caseId": 7748,
    "guid": "1e0abcb7-b94c-4072-a9c0-37072a1ef015",
    "senderAccountId": 1009,
    "content": "Hello!",
    "messageType": "serviceComment",
    "createdAt": "2017-07-26T13:43:44.512Z",
    "updatedAt": "2017-07-26T13:43:44.512Z"
  },
  {
    "id": 2,
    "caseId": 7748,
    "guid": "1e0abcb7-b94c-4072-a9c0-37072a1ef015",
    "senderAccountId": 1009,
    "content": "Test comemnt",
    "messageType": "serviceComment",
    "createdAt": "2017-07-26T13:54:53.058Z",
    "updatedAt": "2017-07-26T13:54:53.058Z"
  }
]
```