# Messages

Messages are used to communicate between plugins. A message is a line of JSON,
terminated with a `\n` character. All messages have at least these fields.

```json
{
    "type": "foo/bar",
    "id":   "unique-id"
}
```

The `type` field identifies the message's type. In the above example, we have
the type `bar` in the `foo` namespace.

The `id` field uniquely identifies the message. This is used for
request/response messages.
