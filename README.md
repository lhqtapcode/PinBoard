# PinInterest Project

A Pinterest-inspired web application built with Node.js, Express, and MongoDB.

## Features

- User authentication (register, login, profile management)
- Create, view, update, and delete pins
- Image upload and display
- Responsive design
- Masonry layout for pins display
- User profiles
- Settings management

## Project Structure

```
PinInterest/
│
├── config/
│   └── db.js                # Database connection
│
├── controllers/
│   ├── authController.js    # Authentication logic
│   ├── pinsController.js    # Pins CRUD operations
│   └── usersController.js   # User management
│
├── middleware/
│   └── auth.js              # Authentication middleware
│
├── models/
│   ├── Pin.js               # Pin model schema
│   └── user.js              # User model schema
│
├── public/                  # Static assets
│   ├── css/
│   │   ├── auth.css         # Authentication styles
│   │   ├── main.css         # Main application styles
│   │   └── modal.css        # Modal styles
│   │
│   ├── js/
│   │   ├── auth.js          # Frontend authentication
│   │   ├── main.js          # Main application logic
│   │   ├── modal.js         # Modal handling
│   │   └── pins.js          # Pin display and manipulation
│   │
│   ├── index.html           # Home page
│   ├── login.html           # Login page
│   ├── register.html        # Registration page
│   └── 404.html             # 404 error page
│
├── routes/
│   ├── auth.js              # Authentication routes
│   ├── pins.js              # Pins routes
│   └── users.js             # User routes
│
├── .env                     # Environment variables
├── package.json             # Project dependencies
├── package-lock.json        # Dependency lock file
└── server.js                # Main application entry point
```

## Prerequisites

- Node.js (v14.x or higher)
- MongoDB Atlas account (or local MongoDB instance)
- npm or yarn package manager

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/pininterest-project.git
   cd pininterest-project
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Create a `.env` file in the root directory with the following variables (or use the one provided):
   ```
   PORT=3001
   MONGO_URI=mongodb+srv://PinBoard:PinBoard123@pinboard.2jgva.mongodb.net/?retryWrites=true&w=majority&appName=PinBoard
   JWT_SECRET=pinboard-secret-key
   ```

4. Start the development server:
   ```bash
   npm run dev
   ```

5. Open your browser and navigate to `http://localhost:3001` to use the application.

## API Endpoints

### Authentication
- `POST /auth/register` - Register a new user
- `POST /auth/login` - Login and get authentication token
- `GET /auth/me` - Get current user profile (requires auth)

### Pins
- `GET /pins` - Get all pins
- `GET /pins/:id` - Get a specific pin by ID
- `GET /pins/user/:userId` - Get all pins from a specific user
- `POST /pins` - Create a new pin (requires auth)
- `PUT /pins/:id` - Update a pin (requires auth)
- `DELETE /pins/:id` - Delete a pin (requires auth)

### Users
- `GET /users` - Get all users
- `GET /users/:id` - Get a specific user by ID
- `PUT /users/:id` - Update user profile (requires auth)
- `PUT /users/:id/password` - Change user password (requires auth)

## Authentication Flow

1. User registers with username, email, and password
2. The server hashes the password and stores the user in the database
3. User logs in with email and password
4. The server verifies credentials and returns a JWT token
5. The client stores the token in localStorage
6. For protected routes, the token is sent in the Authorization header
7. The server validates the token for authenticated requests

## Development Notes

- The frontend uses vanilla JavaScript (no frameworks)
- Authentication is handled with JWT tokens
- The database is MongoDB Atlas
- Images are currently stored as base64 data URLs (in a production app, use a service like AWS S3)
- The application uses a responsive design approach

## Future Enhancements

- Add like/save functionality
- Implement follow/unfollow users
- Add comments on pins
- Implement categories and tags
- Add search functionality on the backend
- Implement image optimization
- Add social sharing

## Troubleshooting

- If you encounter CORS issues, make sure your server is configured properly
- Check browser console for errors when interacting with the application
- If authentication fails, verify that your JWT_SECRET is correctly set
- For database connection issues, ensure your MongoDB URI is correct
- If the port is already in use, the server will automatically try the next port

## License

This project is licensed under the MIT License - see the LICENSE file for details.
