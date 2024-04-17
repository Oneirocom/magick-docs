# Clear

The Clear node is used to empty an array variable, removing all its elements. It's useful when you need to reset an array to its initial empty state, typically at the beginning of a loop or after processing the array's contents.

## Inputs

1. `flow` (required): The flow input that triggers the node's execution.
2. `array` (required): The array variable to be cleared. If not provided, an empty array will be used as the default value.

## Outputs

1. `flow`: The flow output that is triggered after the array is cleared.
2. `array`: The cleared array variable, which will be an empty array.

## Configuration

This node does not have any configuration options.

## Usage

1. Connect the `flow` input to the desired trigger point in your spell, such as a button click or the completion of a previous action.
2. Connect the `array` input to the array variable you want to clear. If left unconnected, an empty array will be used.
3. Connect the `flow` output to the next action you want to perform after the array is cleared.
4. If needed, connect the `array` output to other nodes that require the cleared array.

## Example

Suppose you have a spell that processes an array of user-selected items. After processing the items, you want to clear the array so that the user can start a new selection. Here's how you can use the Clear node in this scenario:

1. Create an array variable named `selectedItems` to store the user-selected items.
2. Use a node like Get Items to populate the `selectedItems` array based on user input.
3. Process the items in the `selectedItems` array using nodes like For Each or Filter.
4. After processing the items, connect the `flow` output of the last processing node to the `flow` input of a Clear node.
5. Connect the `selectedItems` array to the `array` input of the Clear node.
6. The Clear node will empty the `selectedItems` array, preparing it for a new round of user selection.

## Best Practices

- Use the Clear node when you need to reset an array to its initial empty state, such as before starting a new iteration of a process that populates the array.
- If you want to create a new empty array without modifying an existing one, you can use the Create Array node instead.

## Common Issues

- Ensure that the `array` input is properly connected to the array variable you want to clear. If left unconnected, the Clear node will output an empty array, but it won't modify any existing array variables.
- Remember that clearing an array is a destructive operation. If you need to preserve the original array contents, consider creating a copy of the array before clearing it.