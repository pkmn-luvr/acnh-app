# Animal Crossing New Horizon's Companion App

## Table of Contents
- [API Endpoints](#api-endpoints)
  - [Fossils](#fossils)
  - [Art](#art)
  - [Fish](#fish)
  - [Deep Sea Creatures](#deep-sea-creatures)
  - [Bugs](#bugs)
- [App Outline](#app-outline)
  - [Back-end Structure (Node.js)](#back-end-structure-nodejs)
  - [Front-end Structure (Node.js)](#front-end-structure-nodejs)
- [Schema Design](#schema-design)

## API Endpoints

### Fossils
- Individual Fossil: `https://api.nookipedia.com/nh/fossils/individuals/{fossil}`
- All Fossils: `https://api.nookipedia.com/nh/fossils/individuals`
  - Fields:
    - Name
    - Image_url
    - Url to Nookipedia

### Art
- Individual Artwork: `https://api.nookipedia.com/nh/art/{artwork}`
- All Artwork: `https://api.nookipedia.com/nh/art`
  - Fields:
    - Name
    - Image_url
    - Url to Nookipedia

### Fish
- All Fish: `https://api.nookipedia.com/nh/fish`
- Individual Fish: `https://api.nookipedia.com/nh/fish/{fish}`
  - Fields:
    - Name
    - Image_url
    - Url to Nookipedia
    - Rarity
    - North Hemisphere availability array
    - South Hemisphere availability array

### Deep Sea Creatures
- All Sea Creatures: `https://api.nookipedia.com/nh/sea`
- Individual Sea Creature: `https://api.nookipedia.com/nh/sea/{sea_creature}`
  - Fields:
    - Name
    - Image_url
    - Url to Nookipedia
    - Rarity
    - North Hemisphere availability array
    - South Hemisphere availability array

### Bugs
- All Bugs: `https://api.nookipedia.com/nh/bugs`
- Individual Bug: `https://api.nookipedia.com/nh/bugs/{bug}`
  - Fields:
    - Name
    - Image_url
    - Url to Nookipedia
    - Rarity
    - North Hemisphere availability array
    - South Hemisphere availability array


## App Outline

### Starting Development
- **Back-end**: Set up a basic Express server and establish the database connection.
- **Front-end**: Lay out React components and set up routes.
- **Integrate API**: Fetch and display data dynamically from the Nookipedia API.

#### Back-end Structure (Node.js)
- **Server Setup**: Set up Express server.
- **Routes**: Define routes and implement controllers to handle the logic for each route.
- **Models**: Define models for database schemas.

#### Front-end Structure
- **Start with Create React App**
  - Run `npx create-react-app acnh-companion-app`
- **Components**: Create components for displaying the different types of data (fossils, art, fish, deep-sea creatures, and bugs).
- **Pages**: Implement pages that will be routed to.
- **React Router**: Use for routing to different pages of the app.
- **Services**: Handle API calls in a separate services directory.
- **UX Considerations**: Incorporate loading states and feedback for user actions, dashboard-style display.

### Schema Design
- **Users**
  - `id`: Primary Key
  - `username`: String
  - `email`: String
  - `passwordHash`: String
  - `userHemisphere`: String
  - `createdAt`: DateTime
  - `updatedAt`: DateTime
- **Collections**
  - `id`: Primary Key
  - `userId`: Foreign Key (References Users.id)
  - `itemType`: String (e.g., "Fossil", "Fish")
  - `itemName`: String
  - `collected`: Boolean
  - `donated`: Boolean
  - `Image_url`: String
  - `createdAt`: DateTime
  - `updatedAt`: DateTime
- **Critter_Availability**
  - `id`: Primary Key
  - `critterName`: String
  - `critterType`: String (e.g., "Bug", "Fish")
  - `monthsAvailableNorth`: JSON [1,2,...,12]
  - `monthsAvailableSouth`: JSON [1,2,...,12]
  - `timesAvailable`: JSON (e.g., [{"start": "9am", "end": "4pm"}, {"start": "9pm", "end": "4am"}])
  - `Image_url`: String
  - `donated`: Boolean
  - `createdAt`: DateTime
  - `updatedAt`: DateTime

