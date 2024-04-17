# Message History

The Message History node retrieves a specified number of recent messages from the conversation history in a Magick flow.

## Inputs

- `flow` (required): The input flow containing the conversation history.
- `entries` (optional): The number of message entries to retrieve from the history. Default is 10.

## Outputs

- `flow`: The input flow, passed through unmodified.
- `messages`: An array of the retrieved message history entries.

## Configuration

- `hiddenProperties`: An array specifying properties to exclude from the output messages. Default is `["hiddenProperties", "eventState"]`.
- `eventState`: An array specifying additional event state properties to include in the output messages. Default is `["channel", "connector"]`.

## Usage

1. Connect the input `flow` to the flow containing the conversation history you want to retrieve messages from.
2. (Optional) Set the `entries` input to the desired number of recent messages to retrieve. If not specified, the default of 10 will be used.
3. (Optional) Modify the `hiddenProperties` and `eventState` configuration arrays to customize what data is included or excluded from the output messages.
4. Connect the output `messages` to any nodes that need to consume or process the retrieved message history.
5. The output `flow` can be used to pass the input flow through to subsequent nodes unmodified.

## Example

Here's an example of using the Message History node in a spell:

```
// ... previous nodes in spell ...

// Retrieve the last 5 messages from the conversation
const messageHistoryNode = magick.nodes.queries.messages.getMessageHistory({
  flow: inputFlow,
  entries: 5
});

// Use the retrieved messages in a subsequent node
const processMessagesNode = magick.nodes.custom.processMessages({
  messages: messageHistoryNode.outputs.messages
});

// ... additional nodes in spell ...
```

In this example, the Message History node retrieves the last 5 messages from the `inputFlow`. The retrieved `messages` are then passed to a custom `processMessages` node for further handling.

## Best Practices

- Only retrieve as many messages as you actually need to avoid unnecessary processing overhead.
- Use the `hiddenProperties` and `eventState` configurations to include or exclude data properties as needed for your use case. This can help reduce the size of the output and improve performance.
- Remember that the `messages` output is an array ordered from oldest to newest message. The most recent message will be the last element in the array.

## Gotchas

- The Message History node only retrieves messages that are already in the flow's history. It does not fetch any new messages that may have arrived since the flow was triggered.
- If the specified `entries` count exceeds the total number of messages in the flow's history, the node will simply return all available messages. No error is thrown.