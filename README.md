# MMA API

The **MMA API** provides comprehensive access to data from the world of Mixed Martial Arts (MMA). Designed for developers, sports analysts, and MMA enthusiasts, this API offers real-time updates, detailed fighter statistics, event information, and more, enabling robust integration into various applications. This API can be located on [RapidAPI](https://rapidapi.com/belchiorarkad-FqvHs2EDOtP/api/mma-api1)

## Key Features

- **Live Event Data**: Access real-time updates during MMA events, including fight results and statistics.
- **Fighter Information**: Retrieve detailed profiles and statistics for MMA fighters, including win/loss records, weight classes, and more.
- **Event Schedule**: Get information on upcoming MMA events, including dates, locations, and fight cards.
- **Historical Data**: Access past event results, fighter statistics, and historical fight data for in-depth analysis.

## Getting Started

1. **Sign Up**: Create an account on RapidAPI.
2. **Subscribe**: Select a subscription plan that suits your needs.
3. **API Key**: Obtain your unique API key to begin making requests.
4. **Documentation**: For detailed usage instructions, visit the [MMA API Documentation](https://rapidapi.com/belchiorarkad-FqvHs2EDOtP/api/mma-api1).


## Endpoint: Search

### Description:
This endpoint allows users to search for MMA players. Users can provide a query string to search for specific players. The endpoint supports pagination and allows users to specify the number of results per page.

### Method:
GET

### Route:
`/search`

### Parameters:
- `query` (required): The search query string.
- `limit` (optional, default: 50): The maximum number of results to return per page.
- `page` (optional, default: 1): The page number for pagination.

### Response:
The endpoint returns a JSON object containing the search results.

#### Success Response:
- Status Code: 200 OK
- Response Body: JSON object containing the search results.

#### Error Responses:
- Status Code: 400 Bad Request
  - Response Body: JSON object with an error message indicating that the query parameter is missing.

- Status Code: 500 Internal Server Error
  - Response Body: JSON object with an error message indicating that something went wrong on the server side.



##MMA Fighter Profile


### Parameters:
- `fighterId` (required): The fighter id.

You can get the fighterId  on the ESPN website or by making a call to scoreboard endpoints and in the json response you will find the id.


## MMA Leagues
/available-leagues

Get the available leagues

## UFC Rankings Endpoint

This endpoint retrieves UFC rankings data. If the data is available in the cache, it returns it directly from the cache. Otherwise, it fetches the data, caches it for 15 minutes, and then returns it.


### Response:
- **200 OK:** If successful, returns a JSON object containing UFC rankings data.
- **500 Internal Server Error:** If an error occurs during the process, it returns an error message in JSON format.

### Caching:
- The data is cached for 15 minutes (900,000 milliseconds) to reduce response time and API load.

## MMA Rankings

This endpoint retrieves the rankings

### Parameters:
- `year` (required): The year (Format YYYY).
- `league` (Default: 'ufc'): The league.


## MMA Schedule

Get the schedules

## Parameters:
- `year` (required): The year (Format YYYY).


## Fighter Fight History Endpoint


This endpoint retrieves the fight history of a fighter based on their unique ID.


### Parameters
- `fighterId`: The unique identifier of the fighter whose fight history is requested.

### Request
- Method: GET
- Headers: None
- Query Parameters:
  - `fighterId` (required): The unique identifier of the fighter.

### Responses
- Success Response:
  - Code: 200 OK
  - Content: JSON object containing the fighter's fight history.
- Error Responses:
  - Code: 400 Bad Request
    - Content: `{ "error": "Invalid fighterId." }` if the `fighterId` is missing or empty.
  - Code: 500 Internal Server Error
    - Content: `{ "error": "<Error message>" }` if an unexpected error occurs during the request.


## Fighter Details Endpoint

This endpoint retrieves comprehensive details for a fighter based on their unique ID.


### Parameters
- `fighterId`: The unique identifier of the fighter whose details are requested.

### Request
- Method: GET
- Headers: None
- Query Parameters:
  - `fighterId` (required): The unique identifier of the fighter.

### Responses
- Success Response:
  - Code: 200 OK
  - Content: JSON object containing the fighter's detailed information.
- Error Responses:
  - Code: 400 Bad Request
    - Content: `{ "error": "Invalid fighterId." }` if the `fighterId` is missing or empty.
  - Code: 500 Internal Server Error
    - Content: `{ "error": "<Error message>" }` if an unexpected error occurs during the request.


## Fighter Stats Endpoint

This endpoint retrieves statistical data for a fighter based on their unique ID.


### Parameters
- `fighterId`: The unique identifier of the fighter whose statistics are requested.

### Request
- Method: GET
- Headers: None
- Query Parameters:
  - `fighterId` (required): The unique identifier of the fighter.

## Responses
- Success Response:
  - Code: 200 OK
  - Content: JSON object containing the fighter's statistical data.
- Error Responses:
  - Code: 400 Bad Request
    - Content: `{ "error": "Invalid fighterId." }` if the `fighterId` is missing or empty.
  - Code: 500 Internal Server Error
    - Content: `{ "error": "<Error message>" }` if an unexpected error occurs during the request.



## Player Profile Endpoint (Version 2)

This endpoint retrieves detailed information about a fighter based on their unique ID.


### Parameters
- `fighterId`: The unique identifier of the fighter whose profile information is requested.

### Request
- Method: GET
- Headers: None
- Query Parameters:
  - `fighterId` (required): The unique identifier of the fighter.

### Responses
- Success Response:
  - Code: 200 OK
  - Content: JSON object containing the fighter's profile information.
- Error Responses:
  - Code: 400 Bad Request
    - Content: `{ "error": "Invalid fighterId." }` if the provided `fighterId` is not a valid number.
  - Code: 500 Internal Server Error
    - Content: `{ "error": "<Error message>" }` if an unexpected error occurs during the request.


## MMA Scoreboard
Endpoint: GET /scoreboard
This endpoint provides access to a scoreboard for various leagues, with the ability to filter by year, month, and day.  

If the year parameter is missing from the request query, it will respond with a 400 error indicating that the year is required. Upon successful retrieval of the scoreboard data, it returns a JSON response containing the requested scoreboard information.



### Parameters:

- `league`: Specifies the league for which the scoreboard is requested. Default value is 'ufc'.
- `year`: Specifies the year for which the scoreboard is requested. Required parameter.
- `month`: Specifies the month for which the scoreboard is requested. Optional parameter.
- `day`: Specifies the day for which the scoreboard is requested. Optional parameter.
Response:

Upon successful retrieval, returns a JSON object containing the scoreboard information.
In case of an error during processing, it responds with an appropriate error status code and a JSON object containing the error message.
Example Usage:
/scoreboard?league=ufc&year=2024


## MMA Scoreboard by Event
Endpoint: GET /scoreboard-by-event
This endpoint retrieves scoreboard information for a specific event within a given league. It allows querying by the event ID.



### Parameters:

- `league`: Specifies the league for which the scoreboard is requested. Default value is 'ufc'.
- `eventId`: Specifies the unique ID of the event for which the scoreboard is requested. Required parameter.
Response:

Upon successful retrieval, returns a JSON object containing the scoreboard information for the specified event.
In case of an error during processing, it responds with an appropriate error status code and a JSON object containing the error message.

**You can get the eventId using the endpoint**>
getEventId

/scoreboard-by-event?league=ufc&eventId=600039893


## Get Event Id

This endpoint returns the leagues with its eventId.

### Parameters:
- `year`: The year
- `league` (Default: ufc)

## MMA News

This endpoint retrieves the latest MMA news 

### Parameters:
- `limit` (Default: 15)
- `league` (Default: 'ufc')


## MMA News by Fighter

Get the MMA News by Fighter

### Parameters:
- `fighterId`: The fighter Id.

## Commonly Asked Questions

### 1. What kind of data can I access through the MMA API?
You can access live event data, fighter profiles, event schedules, and historical fight data.

### 2. How do I authenticate my API requests?
You must include your API key in the headers of your requests as outlined in the API documentation.

### 3. Are there usage limits for the API?
Yes, usage limits vary based on your chosen subscription plan. Check the RapidAPI dashboard for specifics.

### 4. Can I filter data by specific fighters or events?
Yes, the API allows filtering to retrieve data for specific fighters or events.

### 5. Is historical data available for past fights?
Yes, the MMA API includes historical data for previous events and fights, allowing for detailed analysis and comparisons.

For more information and to start using the MMA API, visit [MMA API on RapidAPI](https://rapidapi.com/belchiorarkad-FqvHs2EDOtP/api/mma-api1).
