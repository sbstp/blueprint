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

## `irc` Namespace
The irc namespace contains IRC server input/output messages.

### `irc/in/join`
```json
{
    "type": "irc/in/join",
    "id":   "..",
    "chan": "#channel",
    "who":  "user"
}
```

### `irc/in/part`
```json
{
    "type": "irc/in/part",
    "id":   "..",
    "chan": "#channel",
    "who":  "user",
    "text": "part message"
}
```

### `irc/in/kick`
```json
{
    "type": "irc/in/kick",
    "id":   "..",
    "chan": "#channel",
    "who":  "kickee",
    "by":   "kicker",
    "text": "kick message"
}
```

### `irc/in/quit`
```json
{
    "type": "irc/in/quit",
    "id":   "..",
    "who":  "user",
    "text": "quit message"
}
```

### `irc/in/nick`
```json
{
    "type": "irc/in/nick",
    "id":   "..",
    "who":  "user",
    "nick": "user2"
}
```

### `irc/in/mode`
```json
{
    "type": "irc/in/mode",
    "id":   "..",
    "chan": "#channel",
    "who":  "user",
    "by":   "admin",
    "mode": "+o"
}
```

### `irc/in/msg`
```json
{
    "type": "irc/in/msg",
    "id":   "..",
    "chan": "#channel",
    "who":  "user",
    "text": "message"
}
```

### `irc/out/join`
```json
{
    "type": "irc/out/join",
    "id":   "..",
    "chan": "#channel"
}
```

### `irc/out/part`
```json
{
    "type": "irc/out/part",
    "id":   "..",
    "chan": "#channel",
    "text": "part message"
}
```

### `irc/out/kick`
```json
{
    "type": "irc/out/kick",
    "id":   "..",
    "chan": "#channel",
    "who":  "kickee",
    "text": "kick message"
}
```

### `irc/out/quit`
```json
{
    "type": "irc/out/quit",
    "id":   "..",
    "text": "quit message"
}
```

### `irc/out/nick`
```json
{
    "type": "irc/out/nick",
    "id":   "..",
    "nick": "cylonn2"
}
```

### `irc/out/mode`
```json
{
    "type": "irc/out/mode",
    "id":   "..",
    "chan": "#channel",
    "who":  "user",
    "mode": "+o"
}
```

### `irc/out/msg`
```json
{
    "type": "irc/out/msg",
    "id":   "..",
    "chan": "#channel",
    "text": "hello world"
}
```
