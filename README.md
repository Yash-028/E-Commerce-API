# API Functions

My main mission behind this repo is to show you my ability to work with this
kind of technology and how I organize the project and code. The repo supports
basic functionality like GRUD operations, authentication (JWT/cookies), grouping
users by rules, protecting the endpoints, and others.

**I haven't used any kind of AI tools like ChatGPT, CoPIlot, or any other "
crutches" for the mind.**

## The API comes with the following functionality

- Prevent cross site scripting - XSS
- Add a rate limit for requests of 100 requests per 10 minutes
- Protect against http param polution (hpp)
- Add headers for security (helmet)
- Use cors to make API public
- Data pagination

### Users, Carts, Products and Authentication

- Authentication is done by using:
    - JWT for authentication
    - JWT or cookie expires in 10 minutes - By default
    - Possibility to store the token in cookie - Optional
    - Reading/validating the token from "Authentication" header - By default
    - Reading/validating the token from a cookie - Optional
    - Invalidating of the JWT - Putting it on blacklist until it expires *
      *Coming soon!**
- Sign In/Out:
    - User can login with email and password
    - Plain text password will compare with stored hashed password
    - Once logged in, a token will be sent along with a cookie (token = xxx) and
      in response body as well
    - Invalidating of the JWT on sign-out - **Coming soon!**
    - Removing the cookie
- Users:
    - All users are stored in collection (MongoDB like datastore)
    - Only the admin has full access to CRUD operations over a any user.
    - Passwords is hashed before store it in the collection
    - Changing a user password - Owner or Admin
    - Mutating a user's data - The owner (user) or admin
    - Creating/Deleting a user - Only admin has this ability
    - Password reset - **Coming soon!**
    - Verifying user creation (by email) - **Coming soon!**
    - All CRUD operations above require an authentication
    - Some of the CRUD operations above require authorization (with an admin
      role)
- Carts:
    - All carts are stored in collection (MongoDB like datastore)
    - Mutating the cart data - The owner (user) or admin
    - Creating/Deleting a cart - Only admin has this ability
    - Only the admin has full access to CRUD operations over any cart.
    - All CRUD operations above require an authentication
    - Some of the CRUD operations above require authorization (with an admin
      role)
- Products:
    - All products are stored in collection (MongoDB like datastore)
    - Fetching a list of products **`GET /api/v1/products`** - Do not require
      authentication/authorization
    - Fetching a single product **`GET /api/v1/products/:productId`** - Do not
      require authentication/authorization
    - Mutating the product data - Only admin has this ability
    - Creating/Deleting a product - Only admin has this ability
    - Some of the operations above require an authentication
    - Some of the CRUD operations above require authorization (with an admin
      role)

| # | email                 | pass   | Role    | effects             |
|---|-----------------------|--------|---------|---------------------|
| 1 | admin@my-site.com     | 12345  | admin   | Super user          |
| 2 | visitor@my-site.com   | 13579  | visitor | Mutate its own data |
| 3 | visitor-1@my-site.com | 024680 | visitor | Mutate its own data |

## API Endpoints

## Main tasks

All tasks automation are based
on [NPM scripts](https://docs.npmjs.com/misc/scripts).

| Tasks                     | Description                                           |
|---------------------------|-------------------------------------------------------|
| `npm run start:dev`       | Running the app in **dev** mode                       |
| `npm run build`           | Building the code in **production-ready** mode        |
| `npm run start`           | Running the app in **prod** mode                      |
| `npm run test`            | Running the unit tests ( using jest)                  |
| `npm run test:dev`        | Running the unit with `--watchAll` mode ( using jest) |
| `npm run prettier-format` | Code formatting                                       |

## Requirements

- [Node](https://nodejs.org/en/) `^16.15.0`
- [NPM](https://www.npmjs.com/) `^8.5.5`

## Installation

After confirming that your environment meets the
above [requirements](#requirements), it is time to clone the project
locally by doing the following:

```bash
$ git clone git@github.com:DeanHristov/fake-api-e-commerce.git <project-name>
$ cd <project-name>
```

When you're done with the steps above, run the following command:

```bash
$ npm install # or yarn install
```

## Running the Project

Running the app in **development** mode.

```bash
$ npm run start:dev
```

## Running the Project in production mode.

Firstly, build the app with the following command:

```bash
$ npm run build
```

Running the app in **production** mode.

```bash
$ npm start
```

## Used technologies

- NodeJS- https://nodejs.org/en/
- Git - https://git-scm.com/
- TypeScript - https://www.typescriptlang.org/
- ExpressJS - https://expressjs.com/
- NeDB - https://github.com/louischatriot/nedb
- Postman - https://www.postman.com/
