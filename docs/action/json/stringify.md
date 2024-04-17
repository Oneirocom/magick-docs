# Json Stringify

The Json Stringify node converts a JSON object into a string representation. It is useful when you need to serialize JSON data for storage, transmission over a network, or integration with external systems that require a string format.

## Inputs

- `flow` (required): The incoming JSON object to be stringified.

## Outputs

- `flow`: The original JSON object, passed through unmodified.
- `string`: The stringified representation of the input JSON object.

## Configuration

- `hiddenProperties`: An array of property names that should be hidden from the node's configuration interface. Default: `["hiddenProperties", "valueTypes", "socketInputs", "valueTypeOptions"]`.
- `valueType`: The type of the output value. Leave empty for automatic type detection. Default: `""`.
- `valueTypeOptions`: An object specifying the available value types for the output socket. Default: `{"values": ["string", "number", "float", "boolean", "object", "array"], "socketName": "Item"}`.
- `socketInputs`: An array of additional input sockets to be added to the node. Default: `[]`.

## Usage

1. Connect a node that outputs a JSON object to the `flow` input of the Json Stringify node.
2. The stringified representation of the JSON object will be available at the `string` output socket.
3. Connect the `string` output to other nodes that expect a string input, such as a Write File node or an HTTP Request node.

## Example

Here's an example of using the Json Stringify node to convert a JSON object to a string and save it to a file:

```json
{
  "nodes": [
    {
      "id": "1",
      "type": "data/object",
      "outputs": {
        "output": {
          "name": "John",
          "age": 30,
          "city": "New York"
        }
      }
    },
    {
      "id": "2",
      "type": "action/json/stringify",
      "inputs": {
        "flow": { "nodeId": "1", "socket": "output" }
      }
    },
    {
      "id": "3",
      "type": "io/file/write",
      "inputs": {
        "data": { "nodeId": "2", "socket": "string" },
        "path": "output.json"
      }
    }
  ]
}
```

In this example:
1. The Object node (ID: 1) creates a JSON object with properties `name`, `age`, and `city`.
2. The Json Stringify node (ID: 2) receives the JSON object from the Object node and converts it into a string.
3. The Write File node (ID: 3) takes the stringified JSON from the Json Stringify node and saves it to a file named `output.json`.

## Best Practices

- Use the Json Stringify node whenever you need to convert a JSON object to a string format for compatibility with other systems or protocols.
- Make sure the input to the Json Stringify node is a valid JSON object to avoid parsing errors.

## Common Issues

- If the input to the Json Stringify node is not a valid JSON object, the node will throw an error. Ensure that the input is properly formatted JSON.
- Be aware that stringifying large JSON objects can be memory-intensive and may impact performance. Consider splitting large objects into smaller chunks if necessary.