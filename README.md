# Beer Tap Dispensers

This is a Beer Tap Dispensers application built using Node.js, Express, and MongoDB. The application manages beer dispensers and tracks their usage.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

You need to have Node.js and MongoDB installed on your machine to run this project locally. MongoDB should be running on `localhost:27017` (the default MongoDB port).
Here is the current Url from .env `mongodb://localhost:27017/beerDispenser`

## Models

### Dispenser

- `status` (open or closed)
- `flow_volume` (how many liters of beer come out per second)
- `openTime` (when the dispenser was last opened)
- `totalServed` (total volume of beer served)
- `totalRevenue` (total revenue from the dispenser)
- `pricePerLiter` (price per liter of beer)
- `totalUses` (how many times the dispenser has been used)
- `totalOpenTime` (total time the dispenser has been open in seconds)
- `currentVolume` (current volume of beer left in the dispenser)

### DispenserHistory

- `dispenser` (ID of the dispenser)
- `openedAt` (when the dispenser was opened)
- `closedAt` (when the dispenser was closed)
- `served` (volume of beer served during this use)
- `revenue` (revenue generated during this use)

## Modules

### DispenserService

- `createDispenser`: Creates a new dispenser with the provided data.
- `openDispenser`: Opens a dispenser. If the dispenser is already open or if its current volume is 0, it throws an error.
- `closeDispenser`: Closes a dispenser and calculates the volume of beer served, the revenue generated, and the remaining beer. If the dispenser served more than 3 litres or the remaining volume is less than 1 litre, it closes the dispenser.
- `getDispenser`: Retrieves a dispenser by ID.

### DispenserHistoryService

- `createDispenserHistory`: Creates a new dispenser history record with the provided dispenser data.
- `getReport`: Retrieves a report of dispenser usage and revenue for a given time period.

## API Endpoints

- `POST /dispenser`: Create a new dispenser
- `PATCH /dispenser/:id/open`: Open a dispenser
- `PATCH /dispenser/:id/close`: Close a dispenser
- `GET /dispenser/:id`: Get a dispenser
- `GET /report/dispenser?startTime=<startTime>&endTime=<endTime>`: Get a report of dispenser usage and revenue for a given time period
- `GET /report/analytics/:id`: Get detailed usage and revenue data for a specific dispenser

Replace `<startTime>`, `<endTime>`, and `<id>` with actual start and end times in ISO 8601 date and time format (for example, `2023-08-01T00:00:00.000Z`) and the id of the dispenser respectively.

## Note

This application assumes that all dispensers start with the same initial volume of beer, and that this initial volume is larger than the `flow_volume * totalOpenTime`. If a dispenser's volume goes below 1 litre, the dispenser will be closed automatically.

## Screenshots

### Branch Manager

![Branch](https://github.com/nkutechologies/Capital-Market-Analytics/assets/71810407/4e2fd8ef-a1f0-4130-85ea-800050d7c6de)

### Capital Mangement

![Capital Management](https://github.com/nkutechologies/Capital-Market-Analytics/assets/71810407/1567ff2c-ac90-4231-b43e-f6dc58342673)

### Financial Summary

![Financial Summary](https://github.com/nkutechologies/Capital-Market-Analytics/assets/71810407/218938fa-66ed-4dc2-872a-3c03b427ef22)


## Videos



https://github.com/nkutechologies/Capital-Market-Analytics/assets/71810407/d382734a-5d46-43c2-a1b0-745084ace301



https://github.com/nkutechologies/Capital-Market-Analytics/assets/71810407/77043928-aa95-4a0a-8042-eec41afddfbc



https://github.com/nkutechologies/Capital-Market-Analytics/assets/71810407/5cec62c0-05b5-4a91-bb36-b1a8b310c1b8

