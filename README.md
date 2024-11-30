Trello API Postman Project Overview This project demonstrates the use of Postman to interact with the Trello API for managing boards, lists, cards, checklists, and checklist items. It includes a full suite of HTTP methods (POST, GET, PUT, DELETE) to cover CRUD operations, utilizes dynamic environment variables, and leverages token-based authorization for secure access.

Key features:

Dynamic variable handling using Postman environment variables. Environment variable management: Values set dynamically from POST responses and validated with stored data. Comprehensive API testing: Includes all CRUD operations for Trello components. Automated test runs using Newman. HTML reporting for run results. Prerequisites Postman: Installed on your local machine. Newman: Install via Node.js using: bash Copy code npm install -g newman Trello Account: Sign up at Trello. Trello API Token and Key: Obtain from the Trello Developer API. Project Structure Collections: Contains requests for all Trello entities (Board, List, Card, Checklist, CheckItems). Environment: Includes environment variables such as baseUrl, token, boardId, listId, etc. Test Scripts: Ensures response data matches environment variables. Newman Config: Configured to execute collections and generate HTML reports. Features

    Authorization Token-based authentication for full API access. Add your API key and token in the environment file: json Copy code { "baseUrl": "https://api.trello.com/1", "apiKey": "YOUR_API_KEY", "token": "YOUR_ACCESS_TOKEN" }
    Dynamic Environment Variables Variables like boardId, listId, cardId, etc., are dynamically set after POST requests using Postman test scripts: javascript Copy code pm.environment.set("boardId", pm.response.json().id); Subsequent requests validate these variables against the API responses.
    CRUD Operations Board: POST /boards - Create a new board. GET /boards/{id} - Fetch details of a board. PUT /boards/{id} - Update a board. DELETE /boards/{id} - Delete a board. List: Similar CRUD operations for lists. Card: Handles cards under lists. Checklist & CheckItems: Includes operations for managing checklists and their items.
    Automated Testing with Newman Run collections using Newman: bash Copy code newman run collection.json -e environment.json Generate an HTML report: bash Copy code newman run collection.json -e environment.json -r html,cli
    HTML Reports Provides a detailed view of each API request's status, response time, and success/failure. Usage Instructions Import Collection and Environment:

Open Postman and import the provided collection and environment files. Set Up Environment:

Add your apiKey and token in the environment variables. Run Requests:

Use the collection runner or Newman to execute the requests. Validate Responses:

Ensure the values in the response match the dynamically set variables. Generate Reports:

Use Newman with the HTML reporter to visualize test run results. Contributions Contributions are welcome! If you have ideas to enhance this project, feel free to submit a pull request or open an issue.
