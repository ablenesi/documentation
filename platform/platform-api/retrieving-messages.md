# Retrieving Messages

Depending on the use case, messages can be retrieved using either a System perspective or a User perspective.  The System perspective will list all messages in the conversation. A User perspective differs from the System in the following ways:

- It provides a `received_at` property.
- It provides an `is_unread` property.
- It removes all messages that have been deleted by this user but not globally deleted.

Use the following endpoint to request all messages in a conversation from a specific user's perspective.

```request
GET /apps/:app_uuid/users/:user_id/conversations/:conversation_uuid/messages
```

```console
curl  -X GET \
      -H 'Accept: application/vnd.layer+json; version=1.1' \
      -H 'Authorization: Bearer TOKEN' \
      -H 'Content-Type: application/json' \
      https://api.layer.com/apps/APP_UUID/users/USER_ID/conversations/CONVERSATION_ID/messages
```

### Successful Response `200 (OK)`

```json
[
    {
        "conversation": {
            "id": "layer:///conversations/051f1ca7-5760-47a5-bf73-048a747fee44",
            "url": "https://api.layer.com/apps/58330abe-b79e-11e5-b0dd-f4bc00000775/users/bcd5e1d8-d276-4b60-97fd-d4bb18308b07/conversations/051f1ca7-5760-47a5-bf73-048a747fee44"
        },
        "id": "layer:///messages/cf131537-a92b-46d7-a2b5-a89f94c707c5",
        "is_unread": true,
        "parts": [
            {
                "body": "Hello!",
                "mime_type": "text/plain"
            }
        ],
        "received_at": "2016-01-10T13:31:10.394Z",
        "recipient_status": {
            "2dfbc084-9800-427a-a965-5aef5a2c35b8": "sent",
            "bcd5e1d8-d276-4b60-97fd-d4bb18308b07": "read"
        },
        "sender": {
            "name": null,
            "user_id": "bcd5e1d8-d276-4b60-97fd-d4bb18308b07"
        },
        "sent_at": "2016-01-10T13:31:04.393Z",
        "url": "https://api.layer.com/apps/58330abe-b79e-11e5-b0dd-f4bc00000775/users/bcd5e1d8-d276-4b60-97fd-d4bb18308b07/messages/cf131537-a92b-46d7-a2b5-a89f94c707c5"
    },
    {
        "conversation": {
            "id": "layer:///conversations/051f1ca7-5760-47a5-bf73-048a747fee44",
            "url": "https://api.layer.com/apps/58330abe-b79e-11e5-b0dd-f4bc00000775/users/bcd5e1d8-d276-4b60-97fd-d4bb18308b07/conversations/051f1ca7-5760-47a5-bf73-048a747fee44"
        },
        "id": "layer:///messages/b9b39a23-1a3a-4e0e-8198-39c869814e58",
        "is_unread": false,
        "parts": [
            {
                "body": "We on for later?",
                "id": "layer:///messages/b9b39a23-1a3a-4e0e-8198-39c869814e58/parts/0",
                "mime_type": "text/plain"
            }
        ],
        "received_at": "2016-01-10T13:31:02.781Z",
        "recipient_status": {
            "2dfbc084-9800-427a-a965-5aef5a2c35b8": "sent",
            "bcd5e1d8-d276-4b60-97fd-d4bb18308b07": "read"
        },
        "sender": {
            "name": null,
            "user_id": "bcd5e1d8-d276-4b60-97fd-d4bb18308b07"
        },
        "sent_at": "2016-01-10T13:30:59.548Z",
        "url": "https://api.layer.com/apps/58330abe-b79e-11e5-b0dd-f4bc00000775/users/bcd5e1d8-d276-4b60-97fd-d4bb18308b07/messages/b9b39a23-1a3a-4e0e-8198-39c869814e58"
    }
]
```

Use the following endpoint to request all messages in a conversation from the System's perspective.

```request
GET /apps/:app_uuid/conversations/:conversation_uuid/messages
```

```console
curl  -X GET \
      -H 'Accept: application/vnd.layer+json; version=1.1' \
      -H 'Authorization: Bearer TOKEN' \
      -H 'Content-Type: application/json' \
      https://api.layer.com/apps/APP_UUID/conversations/CONVERSATION_ID/messages
```

### Successful Response `200 (OK)`

```json
[
    {
        "conversation": {
            "id": "layer:///conversations/051f1ca7-5760-47a5-bf73-048a747fee44",
            "url": "https://api.layer.com/apps/58330abe-b79e-11e5-b0dd-f4bc00000775/conversations/051f1ca7-5760-47a5-bf73-048a747fee44"
        },
        "id": "layer:///messages/cf131537-a92b-46d7-a2b5-a89f94c707c5",
        "is_unread": null,
        "parts": [
            {
                "body": "Hello!",
                "mime_type": "text/plain"
            }
        ],
        "received_at": null,
        "recipient_status": {
            "2dfbc084-9800-427a-a965-5aef5a2c35b8": "sent",
            "bcd5e1d8-d276-4b60-97fd-d4bb18308b07": "read"
        },
        "sender": {
            "name": null,
            "user_id": "bcd5e1d8-d276-4b60-97fd-d4bb18308b07"
        },
        "sent_at": "2016-01-10T13:31:04.393Z",
        "url": "https://api.layer.com/apps/58330abe-b79e-11e5-b0dd-f4bc00000775/conversations/051f1ca7-5760-47a5-bf73-048a747fee44/messages/cf131537-a92b-46d7-a2b5-a89f94c707c5"
    },
    {
        "conversation": {
            "id": "layer:///conversations/051f1ca7-5760-47a5-bf73-048a747fee44",
            "url": "https://api.layer.com/apps/58330abe-b79e-11e5-b0dd-f4bc00000775/conversations/051f1ca7-5760-47a5-bf73-048a747fee44"
        },
        "id": "layer:///messages/b9b39a23-1a3a-4e0e-8198-39c869814e58",
        "is_unread": null,
        "parts": [
            {
                "body": "We on for later?",
                "id": "layer:///messages/b9b39a23-1a3a-4e0e-8198-39c869814e58/parts/0",
                "mime_type": "text/plain"
            }
        ],
        "received_at": null,
        "recipient_status": {
            "2dfbc084-9800-427a-a965-5aef5a2c35b8": "sent",
            "bcd5e1d8-d276-4b60-97fd-d4bb18308b07": "read"
        },
        "sender": {
            "name": null,
            "user_id": "bcd5e1d8-d276-4b60-97fd-d4bb18308b07"
        },
        "sent_at": "2016-01-10T13:30:59.548Z",
        "url": "https://api.layer.com/apps/58330abe-b79e-11e5-b0dd-f4bc00000775/conversations/051f1ca7-5760-47a5-bf73-048a747fee44/messages/b9b39a23-1a3a-4e0e-8198-39c869814e58"
    }
]
```


Use the following endpoint to request a single message from a conversation from a specific user's perspective.

```request
GET /apps/:app_uuid/users/:user_id/messages/:message_uuid
```

```console
curl  -X GET \
      -H 'Accept: application/vnd.layer+json; version=1.1' \
      -H 'Authorization: Bearer TOKEN' \
      -H 'Content-Type: application/json' \
      https://api.layer.com/apps/APP_UUID/users/USER_ID/messages/MESSAGE_ID
```

### Successful Response `200 (OK)`

```json
{
    "conversation": {
        "id": "layer:///conversations/051f1ca7-5760-47a5-bf73-048a747fee44",
        "url": "https://api.layer.com/apps/58330abe-b79e-11e5-b0dd-f4bc00000775/users/bcd5e1d8-d276-4b60-97fd-d4bb18308b07/conversations/051f1ca7-5760-47a5-bf73-048a747fee44"
    },
    "id": "layer:///messages/cf131537-a92b-46d7-a2b5-a89f94c707c5",
    "is_unread": true,
    "parts": [
        {
            "body": "Hello!",
            "mime_type": "text/plain"
        }
    ],
    "received_at": "2016-01-10T13:31:10.394Z",
    "recipient_status": {
        "2dfbc084-9800-427a-a965-5aef5a2c35b8": "sent",
        "bcd5e1d8-d276-4b60-97fd-d4bb18308b07": "read"
    },
    "sender": {
        "name": null,
        "user_id": "bcd5e1d8-d276-4b60-97fd-d4bb18308b07"
    },
    "sent_at": "2016-01-10T13:31:04.393Z",
    "url": "https://api.layer.com/apps/58330abe-b79e-11e5-b0dd-f4bc00000775/users/bcd5e1d8-d276-4b60-97fd-d4bb18308b07/messages/cf131537-a92b-46d7-a2b5-a89f94c707c5"
}
```


Use the following endpoint to request a single message from a conversation from the System's perspective.

```request
GET /apps/:app_uuid/conversations/:conversation_uuid/messages/:message_uuid
```

```console
curl  -X GET \
      -H 'Accept: application/vnd.layer+json; version=1.1' \
      -H 'Authorization: Bearer TOKEN' \
      -H 'Content-Type: application/json' \
      https://api.layer.com/apps/APP_UUID/conversations/CONVERSATION_ID/messages/MESSAGE_ID
```

### Successful Response `200 (OK)`

```json
{
    "conversation": {
        "id": "layer:///conversations/051f1ca7-5760-47a5-bf73-048a747fee44",
        "url": "https://api.layer.com/apps/58330abe-b79e-11e5-b0dd-f4bc00000775/conversations/051f1ca7-5760-47a5-bf73-048a747fee44"
    },
    "id": "layer:///messages/cf131537-a92b-46d7-a2b5-a89f94c707c5",
    "is_unread": null,
    "parts": [
        {
            "body": "Hello!",
            "mime_type": "text/plain"
        }
    ],
    "received_at": null,
    "recipient_status": null,
    "sender": {
        "name": null,
        "user_id": "bcd5e1d8-d276-4b60-97fd-d4bb18308b07"
    },
    "sent_at": "2016-01-10T13:31:04.393Z",
    "url": "https://api.layer.com/apps/58330abe-b79e-11e5-b0dd-f4bc00000775/conversations/051f1ca7-5760-47a5-bf73-048a747fee44/messages/cf131537-a92b-46d7-a2b5-a89f94c707c5"
}
```
