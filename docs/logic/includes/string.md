# Includes

The Includes node checks if one string includes another string and outputs a boolean result.

## Inputs

1. `a` (string): The string to search within. This is the string that may contain the substring you are looking for.
2. `b` (string): The substring to search for. This is the string that you want to check if it is included in the `a` input.

## Outputs

1. `result` (boolean): Returns `true` if string `a` includes string `b`, otherwise returns `false`.

## Configuration

This node has no additional configuration options.

## Usage

To use the Includes node:

1. Connect a string to the `a` input. This is the string you want to search within.
2. Connect a string to the `b` input. This is the substring you want to check for inclusion in `a`.
3. The `result` output will emit `true` if `b` is found within `a`, otherwise it will emit `false`.

## Example

Let's say you have a spell that processes customer feedback messages. You want to check if each message includes the word "great" and keep a count of the positive messages.

You could use the Includes node like this:

1. Connect the customer message string to the `a` input. 
2. Connect a Constant node with the value "great" to the `b` input.
3. Connect the `result` output to a Filter node to only pass through messages where `result` is `true`.
4. Connect the filtered messages to a Count node to keep a running total of positive messages.

In this example, the Includes node allows you to easily check each message for specific positive keywords and filter the messages accordingly for further aggregation.

## Best Practices

- Make sure the input types match. Both inputs should be strings.
- The search is case-sensitive. Use a Transform node beforehand to convert the strings to a consistent case if needed.
- If you need to check for multiple substrings, you can chain multiple Includes nodes together with OR logic for more complex checks.

## Common Issues

- Passing a non-string value to either input will cause an error. Ensure you are passing strings.
- An empty string input for `b` will always return `true` since technically an empty string is included in every string. Check your logic if you get unexpected `true` results.