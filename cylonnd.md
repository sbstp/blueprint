# cylonnd

`cylonnd` is the core component of the project. It's a message broker and a process manager. It communicates with the plugins using a UNIX socket and a protocol similar to `JSON-RPC`.

`cylonnd` creates its socket in `/tmp/` with a random name. Then, it launches the plugins passing the socket's path as an argument.

## Broker
The broker dispatches messages using globbing patterns. When a plugin first registers itself to `cylonnd`, it must send a list of globbing patterns that describe what messages the plugin is interested in receiving. For instance, `irc/*` tells the broker to send all messages from the `irc` namespace to the plugin.

Example globbing patterns:
```
# The globbing can only occur at the end of the string.
irc/*
irc/in/msg
irc/in/*
```

## Plugins
A plugin has a name and a command. The name is used to refer to the plugin, for instance when you want to unload or reload it. `cylondd` automatically loads plugins that are described in the `init` file. The format is as follows:
```
# name: command
# comments
weather: python weather.py
```

## Protocol
Messages are encoded in `JSON`. Text is encoded in `UTF-8`. Each message is delimited by a line ending, `\n`. A message should always have a unique identifier. See the [messages](messages/) section for more information.
