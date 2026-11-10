# Hotel Listing Web Application

A full-stack accommodation listing web application built with Node.js, Express.js, MongoDB, and EJS. The application allows users to explore accommodation listings, create and manage listings, and interact through reviews.

## Overview

The project follows a server-rendered MVC-style structure. Express.js handles routing and application logic, MongoDB stores application data, and EJS templates render the user interface.

Cloudinary is used for listing image storage, while Passport Local supports user authentication.

## Features

- **Browse listings:** View the available accommodation listings.
- **Listing details:** Open an individual listing to view its information.
- **Create listings:** Authenticated users can add new listings.
- **Edit and delete listings:** Listing management routes include authentication and ownership checks for editing.
- **User authentication:** Signup, login, and logout using Passport Local.
- **Reviews:** Logged-in users can add reviews and review authors can delete their reviews.
- **Image uploads:** Upload listing images using Multer and Cloudinary Storage.
- **Input validation:** Validate listing and review data using Joi.
- **Session management:** Maintain login sessions with Express Session and MongoDB-backed session storage.
- **Flash messages:** Display success and error messages to users.
- **Error handling:** Centralised asynchronous error handling and custom application errors.

## Tech Stack

| Area | Technologies |
|---|---|
| Runtime | Node.js |
| Backend framework | Express.js |
| Database | MongoDB, Mongoose |
| View engine | EJS, ejs-mate |
| Authentication | Passport.js, passport-local, passport-local-mongoose |
| Session management | express-session, connect-mongo |
| Image upload | Multer, Cloudinary, multer-storage-cloudinary |
| Validation | Joi |
| Other utilities | dotenv, connect-flash, method-override, cookie-parser |
| Maps integration dependency | Mapbox SDK |

## Application Structure

```text
Hotel_Listing-FULL-STACK-PROJECT/
├── controllers/
│   ├── listings.js
│   ├── reviews.js
│   └── users.js
│
├── init/
├── models/
├── public/
├── routes/
│   ├── listing.js
│   ├── review.js
│   └── user.js
│
├── utils/
├── views/
├── app.js
├── cloudConfig.js
├── middleware.js
├── schema.js
└── package.json
```

## Getting Started

### Prerequisites

Install the following before running the application:

- [Node.js](https://nodejs.org/)
- npm (included with Node.js)
- MongoDB database (MongoDB Atlas is used through the configured connection string)
- Cloudinary account for listing image uploads
- Git

### 1. Clone the repository

```bash
git clone https://github.com/Priyanshurawatofficial/Hotel_Listing-FULL-STACK-PROJECT.git
cd Hotel_Listing-FULL-STACK-PROJECT
```

### 2. Install dependencies

```bash
npm install
```

### 3. Configure environment variables

Create a `.env` file in the project root.

The application reads the following environment variables:

```env
atlasdb_url=your_mongodb_connection_string
SECRET=your_session_secret
Secret=your_mongodb_session_store_secret
CLOUD_NAME=your_cloudinary_cloud_name
CLOUD_API_KEY=your_cloudinary_api_key
CLOUD_API_SECRET=your_cloudinary_api_secret
```

Use your own credentials. The application currently references both `SECRET` and `Secret` (different capitalization) in its session-store configuration. Keep the variable names consistent with the code unless you update the configuration.

**Security:** Never commit your `.env` file or expose database passwords, session secrets, or Cloudinary credentials in the repository.

### 4. Start the application

The current `package.json` does not define a start script. Run the application directly:

```bash
node app.js
```

The server is configured to listen on:

```text
http://localhost:3000
```

Open the URL in your browser after the server starts and successfully connects to MongoDB.

## Main Application Routes

| Method | Route | Description |
|---|---|---|
| `GET` | `/` | Display the listings page |
| `GET` | `/listings` | Browse all listings |
| `GET` | `/listings/new` | Open the new-listing form (login required) |
| `POST` | `/listings` | Create a listing (login required) |
| `GET` | `/listings/:id` | View a listing |
| `GET` | `/listings/:id/edit` | Open the edit form (owner access required) |
| `PUT` | `/listings/:id` | Update a listing (owner access required) |
| `DELETE` | `/listings/:id` | Delete a listing |
| `POST` | `/listings/:id/reviews` | Add a review (login required) |
| `DELETE` | `/listings/:id/reviews/:reviewId` | Delete a review (author access required) |
| `GET` | `/signup` | Open the signup page |
| `POST` | `/signup` | Register a user |
| `GET` | `/login` | Open the login page |
| `POST` | `/login` | Authenticate a user |
| `GET` | `/logout` | Log out |

## How It Works

1. A visitor opens the application and browses accommodation listings.
2. A user can register or log in to access listing-related actions.
3. Authenticated users can create listings and upload images.
4. Listing owners can edit their listings.
5. Users can add reviews to listings, and review authors can remove their own reviews.
6. Listing, user, and review data are persisted in MongoDB.

## Learning Outcomes

This project demonstrates practical experience with:

- Building server-rendered web applications using Express and EJS.
- Implementing CRUD operations with MongoDB and Mongoose.
- Designing modular routes, controllers, and middleware.
- Implementing authentication and session-based user management.
- Uploading and storing images with Cloudinary.
- Validating request data using Joi.
- Handling asynchronous errors and application-level exceptions.

## Future Improvements

- Add search, filtering, and sorting for accommodation listings.
- Improve listing and review authorisation checks across all operations.
- Add automated tests for routes, middleware, and controllers.
- Add pagination for large listing collections.
- Document and configure the Mapbox integration if location features are enabled.
- Add deployment instructions and a hosted demo link.

## Author

**Priyanshu Rawat**

- GitHub: [@Priyanshurawatofficial](https://github.com/Priyanshurawatofficial)
- LinkedIn: [Priyanshu Rawat](https://www.linkedin.com/in/priyanshu-rawat-86063844a/)

---

If you find this project useful, feel free to explore the repository and share feedback.
