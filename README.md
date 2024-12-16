# Express.js Route Handler Missing Error Handling for Invalid User IDs

This repository demonstrates a common error in Express.js route handlers:  missing error handling for invalid input parameters.  Specifically, the provided code attempts to parse a user ID from a route parameter as an integer without any validation. If the ID is not a valid integer, the `parseInt` function will return `NaN`, causing unexpected behavior or crashes.

## Bug

The `bug.js` file contains the problematic code. The route handler `GET /users/:id` fetches a user based on the provided ID. It uses `parseInt` to convert the ID to an integer but lacks proper error handling.  If an invalid ID (non-numeric) is provided, the application's behavior is unpredictable; it may throw an error or return an unexpected response. 

## Solution

The `bugSolution.js` file demonstrates the correct approach. Before parsing the ID to an integer, it checks if it's a valid number using `isNaN()`. If the ID is invalid, an appropriate error response (400 Bad Request) is returned.  If the user is not found, the response is updated to provide a clearer status message.