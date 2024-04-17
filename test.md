# Generate Text

The Generate Text node in Magick allows you to generate natural language text using AI language models. It provides a flexible and powerful way to create dynamic text content within your spells.

## Inputs

- `flow`: The input flow that triggers the text generation.
- `prompt` (string, default: ""): The prompt or initial text to guide the language model in generating the text.
- `system` (string, default: ""): A system message that sets the context or role for the language model.
- `messages` (array, default: []): An array of message objects representing the conversation history.
- `modelOverride` (string, default: ""): Allows overriding the default language model with a specific model name.
- `stop` (string, default: ""): A string or list of strings to stop the text generation when encountered.
- `temperature` (float, default: 0.5): Controls the randomness and creativity of the generated text. Higher values result in more diverse outputs.
- `maxRetries` (integer, default: 3): The maximum number of retries if the text generation fails.
- `top_p` (integer, default: 1): Controls the diversity of the generated text by limiting the cumulative probability of token selection.
- `seed` (integer, default: 42): A seed value for reproducible results.
- `maxTokens` (integer, default: 256): The maximum number of tokens (words or subwords) to generate in the output text.

## Outputs

- `response` (string): The generated text based on the provided inputs.
- `completionResponse` (object): The complete response object returned by the language model, containing additional metadata.
- `done`: The output flow indicating the completion of the text generation.
- `onStream`: The output flow triggered for each token or chunk of text generated during streaming.
- `stream` (string): The stream of generated text, emitted incrementally during streaming.

## Configuration

- `modelProviders` (array, default: []): An array of available language model providers.
- `modelProvider` (string, default: "openai"): The selected language model provider.
- `models` (array, default: []): An array of available language models for the selected provider.
- `model` (string, default: "gpt-3.5-turbo"): The selected language model for text generation.
- `customBaseUrl` (string, default: ""): A custom base URL for the language model API, if applicable.
- `hiddenProperties` (string, default: ["hiddenProperties", "modelProvider", "model", "models", "customBaseUrl"]): Properties to be hidden from the node's configuration interface.

## Usage

1. Connect the desired input flow to the `flow` input of the Generate Text node.
2. Set the `prompt` input to provide the initial text or question to guide the language model.
3. Optionally, set the `system` input to establish the context or role for the language model.
4. If needed, provide an array of `messages` representing the conversation history.
5. Adjust the `temperature`, `top_p`, and `maxTokens` inputs to control the randomness, diversity, and length of the generated text.
6. Connect the `done` output to the next node in your spell to continue the flow after text generation.
7. Retrieve the generated text from the `response` output.

## Example

Here's an example of how to use the Generate Text node in a Magick spell:

```markdown
1. Start
2. Generate Text
   - prompt: "Once upon a time, in a magical land far away..."
   - temperature: 0.7
   - maxTokens: 100
3. Log
   - message: "[Generated Text]"
4. End
```

In this example, the Generate Text node is used to generate a fairy tale-like story. The `prompt` input sets the beginning of the story, and the `temperature` and `maxTokens` inputs control the creativity and length of the generated text. The generated text is then logged using the Log node.

## Best Practices

- Provide clear and specific prompts to guide the language model towards the desired output.
- Experiment with different `temperature` and `top_p` values to find the right balance between creativity and coherence.
- Use the `stop` input to define specific strings or patterns that should terminate the text generation.