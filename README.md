# Global Kitchen API

A small Node.js REST API for managing recipes. This project uses Express and Mongoose to provide endpoints for creating, reading, updating, and deleting recipes.

**Tech Stack**
- **Runtime:** Node.js
- **Framework:** Express
- **Database:** MongoDB (Mongoose)

**Features**
- Create, read, update, and delete recipes
- Filter recipes by category (query parameter)
- Basic validation in services/models

**Quick Start / Installation**
1. Clone the repository:

```bash
git clone <your-repo-url>
cd GlobalKitchen
```

2. Install dependencies:

```bash
npm install
```

3. Create a `.env` file in the project root and set required environment variables (example below).

4. Run the server:

```bash
npm start
# or for development with live reload (if you have nodemon):
npm run dev
```

**Environment Variables**
- `MONGODB_URI` - MongoDB connection string (e.g. from MongoDB Atlas)
- `PORT` - Optional port (defaults to 5000 in the current `server.js`)

**NPM Scripts**
- `start` - Run `node server.js`
- `dev` - Run `nodemon server.js` (if you have nodemon installed)

**API Endpoints**
The recipe routes are defined in [routes/recipeRoutes.js](routes/recipeRoutes.js). They provide the following endpoints (intended to be mounted under a base path such as `/api/recipes`):

- `GET /` - List all recipes (optionally filter by `?category=`)
- `POST /` - Create a new recipe
- `PATCH /:id` - Update a recipe by id
- `DELETE /:id` - Delete a recipe by id

Note: In the current `server.js` the routes are not automatically mounted — to enable the API, import and mount the router. For example in `server.js`:

```js
const recipeRoutes = require('./routes/recipeRoutes');
app.use('/api/recipes', recipeRoutes);
```

**Data Model**
The recipe schema is defined in [models/recipe.js](models/recipe.js). Typical fields include:
- `title` (string) — recipe title
- `ingredients` (array) — list of ingredients
- `instructions` (string)
- `cookingTime` (number) — minutes
- `difficulty` (string) — one of `Easy`, `Medium`, `Hard`
- `category` (string)

Refer to [models/recipe.js](models/recipe.js) for the exact schema used in this repo.

**Project Structure**
- `server.js` — application entry
- `routes/recipeRoutes.js` — route definitions
- `controllers/recipeController.js` — HTTP handlers
- `services/recipeServices.js` — business logic and DB calls
- `models/recipe.js` — Mongoose schema
- `config/db.js` — database connection (if present)
- `middleware/errorMiddleware.js` — error handling middleware

**Notes & Next Steps**
- There are a few places in the code with small typos (for example in `models/recipe.js` and `services/recipeServices.js`) that may prevent the app from running as-is. If you want, I can fix those and add a test script.

**Contributing**
Contributions are welcome — open an issue or submit a pull request.

---

Created for the GlobalKitchen project.
