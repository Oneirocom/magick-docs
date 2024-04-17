# Search Many Knowledge

The Search Many Knowledge node allows you to perform multiple searches on a knowledge base within a single node in Magick. This is useful when you need to retrieve information on several related topics or queries at once.

## Inputs

- `flow` (required): The input flow from the previous node(s) in the spell.
- `queries` (required): An array of search queries to run against the knowledge base. Each query should be a string.
- `count` (optional): The maximum number of search results to return for each query. Default is 2.
- `metadata` (optional): An object containing any additional metadata to include in the search request. Default is an empty object `{}`.

## Outputs

- `flow`: The output flow to be passed to the next node(s) in the spell.
- `knowledge`: An array of knowledge objects returned by the searches. Each object represents a piece of relevant information from the knowledge base.
- `data`: An array of raw data objects returned by the searches, before being processed into knowledge objects.

## Configuration

This node does not have any additional configuration options.

## Usage

1. Connect the input `flow` from the previous node(s) in your spell to this node's `flow` input.
2. Specify the search `queries` you want to run as an array of strings. For example: `["What is Magick?", "How do I create a new spell in Magick?"]`
3. (Optional) Set the maximum result `count` for each query. The default is 2 results per query.
4. (Optional) Provide any additional request `metadata` as an object. 
5. Connect the `flow`, `knowledge`, and/or `data` outputs to the next node(s) in your spell as needed.

## Example

Here's an example of how to use the Search Many Knowledge node in a spell:

```
// Previous nodes...

// Search Many Knowledge node
{
  "type": "action/knowledge/searchMany",
  "inputs": {
    "flow": "{{flow}}",
    "queries": ["What is Magick?", "How do I create a new spell in Magick?"],
    "count": 3
  },
  "outputs": {
    "flow": "{{flow}}",
    "knowledge": "{{knowledge}}",
    "data": "{{data}}"
  }
}

// Use the search results in subsequent nodes...
```

In this example, the node performs two searches - "What is Magick?" and "How do I create a new spell in Magick?" - and returns up to 3 results for each query. The resulting knowledge and data can then be used by later nodes in the spell.

## Best Practices

- Keep your search queries focused and specific. Overly broad queries may return less relevant results.
- Experiment with different `count` values to get the right balance of result quantity and quality for your use case. More isn't always better.
- Make use of the `metadata` input if you need to pass additional context to inform the search.

## Gotchas

- Be aware of the limitations of your knowledge base. This node can only return information that exists in the connected knowledge source.
- Very long or complex search queries may hit limitations of the underlying search system. If a search fails, try simplifying the query.