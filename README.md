# cuq.in Free URL Shortener API

The cuq.in API allows you to easily shorten long URLs.

## API Actions

| Action  | Description                                         | Required Parameters               |
|---------|-----------------------------------------------------|-----------------------------------|
| add     | Create a shortened link by sending a long URL.      | `apiKey`, `url`                   |
| update  | Update an existing shortened link with a new long URL. | `apiKey`, `shortCode`, `url`    |
| getAll  | Retrieve all shortened URLs associated with your API key. | `apiKey`                      |
| delete  | Delete a shortened URL by its shortCode.            | `apiKey`, `shortCode`             |
| search  | Search URLs by keyword or long URL.                 | `apiKey`, `query`                 |

## Request Parameters

| Parameter   | Description                                                      | Type   | Required                                 |
|-------------|------------------------------------------------------------------|--------|------------------------------------------|
| `apiKey`    | The user's API key.                                              | string | Yes                                      |
| `action`    | The action to perform: `add`, `update`, `delete`, `search`, or `getAll`. | string | Yes                          |
| `url`       | The long URL to shorten or update.                               | string | Yes for `add` and `update` actions       |
| `shortCode` | The short URL code for delete or update actions.                 | string | Yes for `delete` and `update` actions    |
| `query`     | The keyword or URL to search for.                                | string | Yes for `search` action                  |

## Response Structure

| Field       | Description                                                      | Type    |
|-------------|------------------------------------------------------------------|---------|
| `status`    | Request status (`true` for success, `false` for error).          | boolean |
| `message`   | Details about the result or any error message.                   | string  |
| `code`      | HTTP status code (e.g., 200 for success, 400 for error).         | integer |
| `shortCode` | The generated short code (returned for the `add` action).        | string  |
| `shortUrl`  | The full shortened URL (returned for the `add` action).          | string  |
| `results`   | An array of shortened URLs (returned for `getAll` or `search`).  | array   |

## Usage Example (cURL)

```bash
curl -X POST https://cuq.in/api   -d apiKey=YOUR_API_KEY   -d action=add   -d url=https://example.com/very/long/url
```
