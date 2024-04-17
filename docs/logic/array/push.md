# Array Push

The Array Push node allows you to add one or more items to the end of an array. It is useful when you need to dynamically build or extend an array based on inputs or conditions in your spell.

## Inputs

- `array` (array): The input array to which items will be pushed. If left disconnected, the node will create a new empty array.
- `flow` (flow): The flow input triggers the node to execute and push items to the array.
- `Item` (any): One or more sockets representing the items to be pushed to the array. The number of sockets is dynamically determined by the `socketInputs` configuration.

## Outputs

- `flow` (flow): The flow output is triggered after the items have been pushed to the array.
- `array` (array): The updated array with the new items pushed to the end.

## Configuration

- `valueType` (string): Specifies the data type of the items being pushed to the array. Choose from "string", "number", "float", "boolean", "object", or "array". Leave blank to allow any data type.
- `socketInputs` (array): Defines the number and names of the input sockets for the items to be pushed. Each element in the array represents a socket. For example, `["item1", "item2"]` will create two input sockets named "item1" and "item2".

## Instructions

1. Connect an input array to the `array` input socket. If left disconnected, a new empty array will be created.
2. Connect the items you want to push to the array to the dynamically created input sockets (e.g., "Item").
3. Configure the `valueType` to specify the data type of the items being pushed (optional).
4. Configure the `socketInputs` array to define the number and names of the item input sockets (optional).
5. Connect a flow to the `flow` input socket to trigger the node's execution.
6. The updated array with the pushed items will be available at the `array` output socket.

## Example

Suppose you have a spell that collects user information from various sources and you want to consolidate the data into a single array. You can use the Array Push node to achieve this:

1. Create an empty array using the Create Array node.
2. Connect the empty array to the `array` input of the Array Push node.
3. Configure the `socketInputs` to `["name", "email", "age"]` to create three input sockets for the user's name, email, and age.
4. Connect the user's name, email, and age data to the corresponding input sockets of the Array Push node.
5. Connect a flow to the `flow` input to trigger the node's execution.
6. The updated array containing the user's information will be available at the `array` output.

## Best Practices

- Ensure that the data types of the items being pushed match the specified `valueType` (if configured) to avoid type mismatches.
- Use meaningful names for the `socketInputs` to improve the readability of your spell.
- If pushing a large number of items, consider using a loop or a separate spell to avoid creating too many input sockets.

## Common Issues

- If the `valueType` is configured and the data type of an item being pushed does not match, the node will throw an error.
- If the `array` input is left disconnected and no items are pushed, the node will output an empty array.

By using the Array Push node, you can easily add items to an array dynamically, making it a versatile tool for building and manipulating arrays in your Magick spells.