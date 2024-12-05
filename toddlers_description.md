# Toddler Descriptions

## RunningToddler
The `RunningToddler` is the main consumer in the system. It loads all the plugins implementing the `ToddlerBase` interface and processes messages it receives. If a message matches one of the topics the toddler cares about, it processes that message.

## ToddlerBase
The `ToddlerBase` class is the base class for all toddlers. It provides methods to configure and process messages. Each subclass must define specific logic for handling messages from different topics.
