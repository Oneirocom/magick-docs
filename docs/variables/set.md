# Set

The Set node allows you to create and assign values to variables within a spell. Variables can store data that you want to use later in the spell or pass between different nodes.

## Inputs

- `flow` (required): The flow from the previous node in the spell.

## Outputs

- `flow`: The flow continues to the next node in the spell, with the variables set.

## Configuration

- `variableNames`: An array of variable names to create. Enter the desired variable names here.

## Usage

1. Add the Set node to your spell.
2. In the node configuration, enter the names of the variables you want to create in the `variableNames` array.
3. Connect the input flow from the previous node to the Set node's `flow` input.
4. Connect the Set node's `flow` output to the next node in your spell.
5. The variables will now be available to use in subsequent nodes within the spell.

## Example

Let's say you want to create two variables, `userName` and `userAge`, to store information about a user. Here's how you would use the Set node to accomplish this:

1. Add the Set node to your spell.
2. In the `variableNames` configuration, enter `["userName", "userAge"]`.
3. Connect the input flow to the Set node.
4. In a later node, such as an HTTP Request node, you can reference these variables using `{{userName}}` and `{{userAge}}` in the URL or body.

## Best Practices

- Give your variables descriptive names that reflect their purpose to keep your spell organized and maintainable.
- If you need to create many variables, consider using multiple Set nodes to group related variables together logically.

## Common Issues

- Forgetting to connect the input flow to the Set node will result in the variables not being created and available in the spell.
- If you try to reference a variable that hasn't been created with the Set node, you'll get an error when running the spell.