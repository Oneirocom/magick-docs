# Remove First

Removes the first item from an array.

## Inputs

- `flow`: The flow to execute this node.
- `array`: The input array to remove the first item from. Defaults to an empty array.

## Outputs

- `flow`: The flow to continue executing.

## Configuration

- `valueType`: The type of the array items. Can be one of: `string`, `number`, `float`, `boolean`, `object`, `array`. Leave blank to auto-detect.

## Example Usage

Suppose you have an array of names and you want to remove the first name from the list:

```json
["Alice", "Bob", "Charlie", "David"]
```

You can use the Remove First node to accomplish this:

1. Connect the array to the `array` input of the Remove First node. 
2. Leave the `valueType` configuration blank to auto-detect the item type as `string`.
3. The output will be the array with the first item removed:

```json
["Bob", "Charlie", "David"] 
```

## Tips

- If the input array is empty, the Remove First node will have no effect.
- The Remove First node modifies the input array in place. If you need to preserve the original array, first make a copy of it using the Duplicate node.

## Common Issues

- Forgetting to set the `valueType` configuration can lead to unexpected results if the array items are not of the auto-detected type. Always double check this setting.
- Connecting a non-array value to the `array` input will result in an error. Ensure you are passing a valid array.