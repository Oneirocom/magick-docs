# Fetch

The Fetch node allows you to make HTTP requests to external APIs and services from within your Magick spell. It supports common HTTP methods like GET, POST, PUT, DELETE, and PATCH, and allows you to configure headers, request body, and authentication.

## Inputs

- `url` (string, required): The URL to make the request to.
- `method` (string, optional): The HTTP method to use for the request. Choices include:
  - `GET` (default)
  - `POST`
  - `PUT` 
  - `DELETE`
  - `PATCH`
- `headers` (object, optional): An object containing the headers to send with the request. Defaults to `{}`.
- `body` (object, optional): The request body to send. Defaults to `{}`.
- `authToken` (string, optional): An authentication token to include in the request.
- `authTokenHeader` (string, optional): The name of the header to use for the `authToken`.
- `flow` (flow): The input flow to trigger the node.

## Outputs

- `response` (object): The response from the API, including the response body, status code, and headers.
- `flow` (flow): The output flow to trigger the next node in the spell.

## Configuration

This node has no additional configuration options.

## Usage

1. Add a Fetch node to your spell.
2. Connect the input flow to trigger the node when desired.
3. Enter the `url` of the API endpoint you want to call.
4. Select the appropriate HTTP `method` for your request.
5. If needed, provide:
   - `headers` object for any custom headers
   - `body` object for POST/PUT/PATCH requests
   - `authToken` and `authTokenHeader` for authenticated requests
6. Connect the `response` output to downstream nodes to use the API response.
7. Connect the output `flow` to trigger the next action.

## Example 

Here's an example of using the Fetch node to make a GET request to the JSONPlaceholder API:

```
Trigger -> Fetch -> Log
```

Fetch node configuration:
- `url`: `https://jsonplaceholder.typicode.com/posts/1`
- `method`: `GET`

Log node configuration: 
- `message`: `{{flow.response.body}}`

When the spell is triggered, it will make a GET request to the specified URL and log the response body to the console.

## Best Practices

- Always specify the full URL, including the protocol (https://)
- Use the appropriate HTTP method for your request semantics
- Include all required headers, such as `Content-Type` and authentication headers
- Validate and sanitize any user-provided inputs that are used to construct the request
- Handle errors gracefully by checking the response status code
- Use the Debugger node to inspect the `response` object if needed

## Common Issues

- Forgetting to include the protocol (https://) in the `url`
- Using the wrong HTTP `method` for the intended action
- Omitting required headers like `Content-Type` or authentication tokens
- Not handling non-2xx response status codes
- Expecting the response body to be a string instead of an object

If you run into issues, double check your configuration and use the Debugger node to inspect the `response` object and identify any problems with the request or response.