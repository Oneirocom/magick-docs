# Event History

The Event History node in Magick allows you to retrieve a historical record of events that have occurred within a flow. This node is particularly useful for debugging, auditing, or analyzing the behavior of your flows over time.

## Inputs

- `flow` (required): The input flow containing the events to retrieve the history for.
- `entries` (optional, default: 10): The number of historical event entries to retrieve.

## Outputs

- `flow`: The original input flow, passed through unchanged.
- `events`: An array of event objects representing the historical events.
- `strings`: An array of formatted strings representing the historical events in a human-readable format.

## Configuration Options

- `hiddenProperties` (default: `["hiddenProperties", "eventState", "availableEvents"]`): An array of property names to exclude from the output event objects.
- `eventState` (default: `["sender", "agentId"]`): An array of event state properties to include in the output event objects.
- `eventStateProperties` (default: `["client", "connector", "channel", "from user", "to user"]`): An array of additional event state properties to include in the output event objects.
- `availableEvents` (default: `["messageReceived", "webhookReceived", "messageSend", "messageStream"]`): An array of event types that are available for selection.
- `selectedEvents` (default: `[]`): An array of specific event types to include in the output. If empty, all available event types will be included.

## Usage

1. Connect a flow containing events to the `flow` input of the Event History node.
2. (Optional) Specify the desired number of historical event entries to retrieve using the `entries` input. The default is 10.
3. (Optional) Customize the configuration options to control which event properties and types are included in the output.
4. The node will output the original `flow`, an array of `events` objects representing the historical events, and an array of `strings` containing a human-readable representation of the events.

## Example

Here's an example of how to use the Event History node in a Magick spell:

```markdown
1. Connect a Webhook Trigger node to listen for incoming webhooks.
2. Connect the output of the Webhook Trigger node to the input of a Custom Code node.
3. In the Custom Code node, perform some processing or data manipulation based on the webhook payload.
4. Connect the output of the Custom Code node to the `flow` input of an Event History node.
5. Configure the Event History node to retrieve the last 20 events and include only "webhookReceived" events.
6. Connect the `events` output of the Event History node to a Debug node to log the historical events for analysis.
```

In this example, the Event History node is used to capture and inspect the history of webhook events processed by the flow, allowing for debugging and understanding the flow's behavior over time.

## Best Practices

- Use the Event History node judiciously, as retrieving large amounts of historical data can impact performance. Start with a smaller `entries` value and increase it only if necessary.
- Be selective about which event types and properties you include in the output to avoid unnecessary data retrieval and processing.
- Use the `strings` output for human-readable logging and debugging, while the `events` output is more suitable for programmatic processing.

## Common Issues

- If the `events` or `strings` outputs are empty, ensure that the connected flow has actually processed events and that the `selectedEvents` configuration matches the event types present in the flow.
- If the retrieved events don't contain the expected properties, review the `eventState` and `eventStateProperties` configuration options to ensure the desired properties are included.

By leveraging the Event History node, you can gain valuable insights into the historical behavior of your flows, aiding in debugging, auditing, and understanding the processing of events over time.