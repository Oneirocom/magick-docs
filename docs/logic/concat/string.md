# Concat

The Concat node is used to concatenate two strings together into a single output string. It's a simple but versatile utility node that can be used whenever you need to join pieces of text together.

## Inputs

1. `a` (string, default: ""): The first string to concatenate.
2. `b` (string, default: ""): The second string to concatenate.

## Outputs

1. `result` (string): The concatenated output string.

## Configuration

This node has no additional configuration options.

## Usage

To use the Concat node:

1. Add a Concat node to your spell.
2. Connect the output of a node providing the first string to the `a` input.
3. Connect the output of a node providing the second string to the `b` input.
4. The concatenated string will be available at the `result` output.

## Example

Let's say you have a spell that generates a personalized greeting message. You have the user's first name and last name as separate strings, and you want to combine them into a full name.

1. Add a Concat node to your spell.
2. Connect the first name string to the `a` input.
3. Add a String node with a space character (" ") as its value and connect it between the first and last name.
4. Connect the last name string to the `b` input.
5. The `result` output will now contain the full name, e.g. "John Doe".

You can then connect this full name to another Concat node along with a greeting like "Hello " to create the final personalized greeting: "Hello John Doe".

## Tips

- If you need to concatenate more than two strings, you can chain multiple Concat nodes together, with the `result` of one feeding into the `a` input of the next.
- Remember that either input can be an empty string. This can be useful for conditionally including or excluding parts of the concatenated string.

## Caution

Be careful not to accidentally connect a non-string value to the `a` or `b` input. The Concat node expects string inputs and may produce unexpected results or errors with other data types.