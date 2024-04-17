# Stream Message

The Stream Message node allows you to send a message to the spell's output stream during execution. It is useful for logging, debugging, or providing feedback to the user at specific points in your spell's logic.

## Inputs

- `flow` (required): The input flow that triggers the node to send the message.
- `content` (optional): The message content to be streamed. Can be any string value. If left blank, an empty message will be sent.

## Outputs

- `flow`: The output flow after the message has been sent, allowing the spell to continue execution.

## Configuration

This node has no additional configuration options.

## Usage

1. Add a Stream Message node to your spell.
2. Connect the input `flow` to the point in your spell where you want to send a message.
3. Set the `content` input to the message you want to send. This can be a static string, a variable, or an expression.
4. Connect the output `flow` to the next node in your spell.

When the spell execution reaches the Stream Message node, it will send the specified message to the spell's output stream and then continue with the rest of the spell logic.

## Example

Here's an example of using the Stream Message node in a spell:

```
// ... (previous nodes)
// Send a message to the output stream
(Stream Message)
  content = "Processing complete. Moving on to next step..."
// ... (subsequent nodes)
```

In this example, the Stream Message node is used to send a status update to the user after some processing has finished, before the spell moves on to the next step.

## Best Practices

- Use Stream Message nodes sparingly to avoid cluttering the output stream. Focus on key points where messages will be most helpful.
- Keep messages concise and informative. Clearly convey the spell's status or the meaning of the message.
- Consider using expressions or variables for the `content` input to create dynamic, context-specific messages.

## Gotchas

- Remember that the Stream Message node does not pause spell execution. The message is sent and the flow immediately continues to the next node.
- Sending too many messages, especially in loops, can flood the output stream and make it difficult to follow the spell's progress.

With the Stream Message node, you can add helpful messages to your spell's output to keep users informed and to aid in debugging and development. Use it judiciously to communicate key information at the right points in your spell's execution flow.