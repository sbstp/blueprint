## `handshake` Namespace
The handshake namespace allows plugins to register themselves, to update their interest set, to query another plugin's status and to be notified when another plugin sends its handshake to the daemon.

### `handshake/init`
This message allows newly connected plugins to describe themselves and to send their interest set (globbing patterns). This must be the first message sent by the plugins. Messages sent by a plugin which has not sent his handshake will be ignored. A plugin that has not sent its handshake (and therfore its interest set) will not receive any message. This is why the plugin should send it's handshake as soon as possible.
```json
{
    "type": "handshake/init",
    "id": "..",
    "name": "name of your plugin",
    "description": "description of your plugin",
    "globs": [
        "irc/in/kick",
        "irc/in/join",
        "etc."
    ]
}
```

### `handshake/update`
The update message allows you to update your interest set, but not your name or description.
```json
{
    "type": "handshake/update",
    "id": "..",
    "globs": [
        "irc/in/*",
        "etc."
    ]
}

```

### `handshake/info`
This message is sent by the broker to let other plugins know that a plugin has just connected to the daemon.
```json
{
    "type": "handshake/info",
    "id": "..",
    "name": "name of the plugin",
    "description": "description of the plugin"
}
```

### `handshake/service`
This message is sent by a plugin to know if another plugin (or sevice) is available.
```json
{
    "type": "handshake/service",
    "id": "..",
    "service": "name of the plugin you want"
}
```
The reply looks like this:
```json
{
    "type": "handshake/service",
    "id": "..",
    "avail": true/false,
    "name": "name, if the plugin is available",
    "description": "description, if the plugin is availalble"
}
```
### Dependencies
A plugin that depends on the `irc` service should send a `handshake/service` message about `irc` to the daemon. If `irc` is not yet available, then the plugin must wait for the `handshake/info` of the `irc` plugin. The client libraries should manage dependencies for the user.
