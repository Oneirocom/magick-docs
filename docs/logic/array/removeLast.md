# Remove Last

Removes the last item from an array.

## Inputs

- `flow`: The flow input to trigger the node's execution.
- `array`: The input array to remove the last item from. Defaults to an empty array.

## Outputs

- `flow`: The flow output to continue the execution of the spell.

## Configuration

This node does not have any additional configuration options.

## Usage

1. Connect the `flow` input to the previous node's output that triggers the execution.
2. Connect the `array` input to an array variable or a node that outputs an array.
3. Connect the `flow` output to the next node in the spell's execution flow.

## Example

Suppose you have an array of names and want to remove the last name from the list. Here's how you can use the Remove Last node to achieve this:

1. Create an array variable with the following names: ["Alice", "Bob", "Charlie", "David"]
2. Connect the array variable to the `array` input of the Remove Last node.
3. Connect the `flow` output of the Remove Last node to the next node in your spell, for example, a Debug node to log the updated array.

After executing the spell, the Debug node will output the array ["Alice", "Bob", "Charlie"], with "David" removed from the end of the list.

## Best Practices

- Ensure that the input `array` is not empty before using the Remove Last node to avoid errors.
- If you need to remove multiple items from the end of an array, consider using a loop or a custom function node.

## Common Issues

- If the input `array` is empty, the Remove Last node will not modify the array and will simply pass it through to the output.
- Be cautious when using the Remove Last node in a loop, as it will continuously remove items from the end of the array until the loop condition is met or the array becomes empty.