# Array Create

The Array Create node allows you to create a new array in your Magick spell. It is a fundamental node for working with collections of data.

## Inputs

- `flow` (required): The flow input triggers the node to execute and create the new array.

## Outputs

- `flow`: The flow output passes the flow control to the next node after the array is created.
- `array`: The newly created array.

## Configuration

- `valueType` (optional, default: "string"): Specifies the data type for the elements in the array. Can be one of: "string", "number", "float", "boolean", "object", "array".
- `socketInputs` (optional): Allows you to specify a list of input sockets for providing the initial values of the array. Each socket input will be added as an element to the array in the order they are listed.

## Usage

1. Add an Array Create node to your spell.
2. (Optional) Configure the `valueType` if you need the array to hold elements other than strings.
3. (Optional) Add input sockets in the `socketInputs` configuration to provide initial values for the array.
4. Connect the `flow` input to trigger the node and create the array.
5. Use the `array` output to pass the newly created array to other nodes in your spell.

## Example

Here's an example of using the Array Create node to create an array of numbers and then logging it to the console:

```json
{
  "nodes": [
    {
      "type": "action/array/create",
      "configuration": {
        "valueType": "number",
        "socketInputs": [
          { "name": "value1", "valueType": "number", "defaultValue": 1 },
          { "name": "value2", "valueType": "number", "defaultValue": 2 },
          { "name": "value3", "valueType": "number", "defaultValue": 3 }
        ]
      },
      "id": "createArray"
    },
    {
      "type": "debug/log",
      "inputs": {
        "message": "={{ createArray.array }}"
      },
      "id": "logArray"
    }
  ],
  "spellConnections": [
    {
      "from": "createArray",
      "to": "logArray"
    }
  ]
}
```

In this example, we create an array of numbers with initial values 1, 2, and 3 using the socket inputs. We then pass this array to a Debug Log node to print it to the console.

## Best Practices

- Specify the `valueType` configuration if you know the type of elements the array will hold. This makes your spell more readable and can help prevent errors.
- Use descriptive names for socket inputs to make it clear what each value represents.

## Common Issues

- Forgetting to connect the `flow` input will result in the node not executing and the array not being created.
- Mismatching the `valueType` of the array and the types of the socket input values can lead to unexpected behavior or errors.