# Send Message

The Send Message node allows you to send a message within a Magick spell. It is useful for generating output, logging information, or communicating with other parts of your spell.

## Inputs

- `flow` (required): The input flow that triggers the node to send the message.
- `content` (optional): The content of the message to send. This can be any string value. If left blank, an empty message will be sent.

## Outputs

- `flow`: The output flow after the message has been sent. This allows you to chain additional nodes after sending the message.

## Configuration

This node does not have any additional configuration options.

## Usage

1. Add a Send Message node to your spell.
2. Connect the input `flow` to the output of the node that should trigger sending the message.
3. Set the `content` input to the message you want to send. This can be a static string or a dynamic value from a previous node.
4. Connect the output `flow` to the next node in your spell, if desired.

## Example

Here's an example of how to use the Send Message node in a spell:

```markdown
1. Start
2. Set Variable [name: "username", value: "John"]
3. Send Message [content: "Hello, {{username}}!"]
4. End
```

In this example:
1. The spell starts.
2. The Set Variable node sets a variable named `username` with the value `"John"`.
3. The Send Message node sends the message `"Hello, John!"`, using the `username` variable in the message content.
4. The spell ends.

## Best Practices

- Use the Send Message node for generating output, logging, or debugging your spell.
- Combine static text and dynamic values in the `content` input to create personalized or data-driven messages.
- Chain multiple Send Message nodes together to send a sequence of messages.

## Common Issues

- If the `content` input is left blank, an empty message will be sent. Make sure to provide a value if you want to send a non-empty message.
- Be mindful of the order of nodes in your spell. Make sure the Send Message node is connected and triggered at the appropriate point in your spell's flow.