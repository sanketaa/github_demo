# StoryBooks Node.js Practice Application

A tutorial-based full-stack Node.js application used to practice Git workflows, Express routing, MongoDB data modeling, Google OAuth, server-rendered views, and CRUD operations.

## Attribution and Purpose

The package metadata identifies this as the **StoryBooks** application by Brad Traversy. This repository is retained as a learning implementation and Git/GitHub practice project; it should not be presented as an independently designed production application.

The value of the project is the hands-on experience gained by working with a complete web application structure, following data through routes and models, configuring authentication, and managing changes with Git.

## Application Overview

StoryBooks allows users to:

- Sign in through Google OAuth
- Create public or private stories
- View public stories
- View stories published by a specific user
- Manage their own stories from a dashboard
- Edit and delete stories
- Enable or disable comments
- Add comments to stories

The interface is server-rendered with Handlebars, and MongoDB stores user, story, and comment data.

## Request Flow

```text
Browser
   |
   v
Express routes
   |
   +--> Passport / Google OAuth
   |
   +--> Mongoose models --> MongoDB
   |
   v
Handlebars views
```

## Technologies

- JavaScript and Node.js
- Express
- MongoDB and Mongoose
- Passport.js
- Google OAuth 2.0
- Express Handlebars
- Express Session
- Body Parser and Cookie Parser
- Method Override
- Git and GitHub

## Repository Structure

```text
.
├── app.js
├── config
│   ├── keys.js
│   └── passport.js
├── helpers
│   ├── auth.js
│   └── hbs.js
├── models
│   ├── Story.js
│   └── User.js
├── routes
│   ├── auth.js
│   ├── index.js
│   └── stories.js
├── views
│   ├── index
│   ├── layouts
│   ├── partials
│   └── stories
├── public
└── package.json
```

## Key Components

- `app.js`: Application setup, middleware, MongoDB connection, sessions, Passport, routes, and server startup.
- `config/passport.js`: Google OAuth strategy and user serialization.
- `models/User.js`: User identity and profile schema.
- `models/Story.js`: Story, visibility, comment, ownership, and timestamp schema.
- `routes/stories.js`: Story listing, creation, viewing, editing, deletion, and comments.
- `helpers/auth.js`: Authentication guards.
- `helpers/hbs.js`: Formatting and conditional helpers for Handlebars templates.

## Skills Demonstrated

- Navigating and modifying a multi-folder Node.js application
- Organizing routes, models, helpers, configuration, and views
- Modeling relationships with Mongoose object references
- Implementing OAuth-based sign-in with Passport
- Using sessions to preserve authenticated state
- Implementing create, read, update, and delete operations
- Rendering dynamic pages with Handlebars
- Working with public/private content and ownership rules
- Practicing Git commits and repository management

## Configuration

The committed `config/keys.js` contains placeholder values only:

```text
mongodb://CHANGEME
CHANGEME
```

Do not replace those placeholders with real secrets in a public repository. A modern version should read the MongoDB URI, OAuth client ID, OAuth secret, and session secret from environment variables or a secrets manager.

## Security and Modernization Notes

Do not deploy this historical project unchanged.

- The session secret is hard-coded and must be moved to protected configuration.
- OAuth credentials and the database URI must remain outside source control.
- Several write routes need explicit authentication and ownership enforcement.
- Input should be validated and sanitized before storage or rendering.
- Add CSRF protection, secure cookie settings, rate limiting, and security headers.
- Update Node.js and all dependencies, then resolve vulnerability findings.
- Replace deprecated Mongoose and Passport APIs.
- Avoid logging complete user objects.
- Add centralized error handling and safe user-facing error responses.
- Add automated tests for authentication, authorization, CRUD operations, and private-story access.
- Configure separate development, test, and production environments.

## Running as a Modernized Lab

Before running the project, update its dependencies and replace the placeholder configuration with environment-variable loading. A MongoDB database and Google OAuth application are required for the authentication flow.

The historical start command is:

```bash
npm install
npm start
```

The application uses port `5000` unless `PORT` is supplied.

## Portfolio Context

This repository shows practical exposure to a full-stack Node.js codebase and version-control workflow. Because it is tutorial-based, it should be described as a learning implementation. Strong discussion points include understanding the architecture, identifying authorization gaps, and explaining how the application should be modernized and secured.
