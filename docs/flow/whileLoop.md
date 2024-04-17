# While Loop

The While Loop node in Magick allows you to repeatedly execute a series of nodes as long as a specified condition remains true. It's useful for implementing iterative logic and loops within your spells.

## Inputs

- `flow` (required): The entry point for the loop. Connect the node(s) that should execute before the loop begins.
- `condition` (required): A boolean value determining whether the loop should continue. The loop will run as long as this input is `true`.

## Outputs

- `completed`: Triggers when the loop has finished executing, either because the condition became `false` or the maximum iterations were reached.
- `loopBody`: Connects to the node(s) that should execute on each iteration of the loop.

## Configuration

- `maxIterations`: The maximum number of times the loop is allowed to run before forcibly exiting. This prevents infinite loops. Default is 10.

## Instructions

1. Add a While Loop node to your spell.
2. Connect the node(s) that should run before the loop starts to the `flow` input.
3. Connect a node that outputs a boolean value to the `condition` input. This will be checked at the start of each iteration to determine if the loop should continue.
4. Connect the `loopBody` output to the first node that should run on each loop iteration. 
5. Chain additional nodes to implement the logic that should repeat each iteration.
6. Connect the final node of the loop body back to the While Loop node's `flow` input to complete the loop circuit.
7. Connect the `completed` output to any nodes that should run after the loop has finished.
8. If needed, adjust the `maxIterations` configuration value to set an appropriate limit for your use case.

## Example

Here's an example spell that uses a While Loop to count down from 10 to 1:

1. Add a Variable node configured with the name "count" and an initial value of 10. 
2. Connect the Variable node to the `flow` input of a While Loop node.
3. Add a Greater Than node and connect the Variable to both its inputs. This will output `true` as long as count is greater than 0.
4. Connect the Greater Than node to the While Loop's `condition` input.
5. Connect the While Loop's `loopBody` to a Subtract node. Connect the Variable to the Subtract node's first input and set the second input to 1. This will decrement count by 1 each iteration.
6. Connect the Subtract node's output back to the Variable to update its value.
7. Also connect the Subtract node to a Debug node to log the current value of count.
8. Connect the Debug node back to the While Loop node's `flow` input.
9. Finally, connect the While Loop's `completed` output to a final Debug node with the message "Loop finished!".

When run, this spell will log the values 10 through 1 to the debug console, then log "Loop finished!" once the loop condition becomes false (i.e. count is no longer greater than 0).

## Best Practices

- Keep loop bodies as small and focused as possible. If a loop is becoming long or complex, consider refactoring the logic into a separate spell and invoking it as a module.
- Be mindful of the `maxIterations` limit. Choose a value high enough that the loop can complete under normal conditions, but not so high that a buggy infinite loop would hang your spell for too long.
- Ensure there is logic in place to eventually make the loop condition `false`, otherwise the loop will run until the iteration limit and may not complete its intended task. 
- Avoid mutating loop control variables (like a counter) inside the loop body. Instead, use nodes like Increment/Decrement or Assign to update values in a controlled way.

## Gotchas

- The loop condition is only checked at the start of each iteration. If the condition becomes `false` in the middle of an iteration, the current iteration will still complete.
- If the loop completes by hitting the `maxIterations` limit, the `completed` output will still trigger. Check the iteration counter if you need to determine whether the loop exited "naturally" or not.
- Be cautious when using While Loop with asynchronous code. Ensure all async operations complete before concluding an iteration, or unintended behavior may occur.