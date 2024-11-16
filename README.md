# 📚 Book Authentication System

A full-stack MERN application for managing and authenticating books with advanced features including user authentication, role-based access control, and secure book management.

## 🚀 Features

### User Management
- Multi-level authentication (Admin, Moderator, User)
- JWT-based authentication
- Password encryption using bcrypt
- Email verification
- Password reset functionality
- OAuth integration (Google, GitHub)
- Session management

### Book Management
- CRUD operations for books
- Advanced search with filters
- Book categorization
- Image upload for book covers
- ISBN validation
- Book borrowing system
- Reading progress tracking
- Review and rating system

### Security Features
- Input validation and sanitization
- Rate limiting
- CORS configuration
- XSS protection
- CSRF protection
- Request logging
- Error handling middleware

## 🛠️ Tech Stack

### Frontend
- React 18
- Redux Toolkit for state management
- React Router v6 for routing
- Axios for API requests
- Material-UI/Tailwind CSS for styling
- React Query for data fetching
- Form validation with Formik & Yup

### Backend
- Node.js with Express.js
- MongoDB with Mongoose ODM
- JWT for authentication
- Bcrypt for password hashing
- Multer for file uploads
- Express-validator for validation
- Winston for logging
- Jest for testing

## 📊 Database Schema

### User Collection
```javascript
{
  username: String (required, unique),
  email: String (required, unique),
  password: String (required, hashed),
  role: String (enum: ['admin', 'moderator', 'user']),
  verified: Boolean,
  createdAt: Date,
  updatedAt: Date,
  lastLogin: Date,
  profile: {
    name: String,
    avatar: String,
    bio: String
  }
}
```

### Book Collection
```javascript
{
  title: String (required),
  author: String (required),
  ISBN: String (unique),
  publishedYear: Number,
  genre: [String],
  description: String,
  coverImage: String,
  status: String (enum: ['available', 'borrowed']),
  addedBy: ObjectId (ref: 'User'),
  createdAt: Date,
  updatedAt: Date,
  reviews: [{
    user: ObjectId (ref: 'User'),
    rating: Number,
    comment: String,
    date: Date
  }]
}
```

## 🚀 Installation

1. Clone the repository
```bash
git clone https://github.com/yourusername/book-auth-system.git
cd book-auth-system
```

2. Install dependencies
```bash
# Install backend dependencies
cd backend
npm install

# Install frontend dependencies
cd ../frontend
npm install
```

3. Environment Setup
```bash
# Backend .env
PORT=5000
MONGODB_URI=your_mongodb_uri
JWT_SECRET=your_jwt_secret
SMTP_HOST=your_smtp_host
SMTP_PORT=your_smtp_port
SMTP_USER=your_smtp_user
SMTP_PASS=your_smtp_pass

# Frontend .env
REACT_APP_API_URL=http://localhost:5000/api
```

## 🏃‍♂️ Running the Application

### Development Mode
```bash
# Run backend
cd backend
npm run dev

# Run frontend
cd frontend
npm start
```

### Production Mode
```bash
# Build frontend
cd frontend
npm run build

# Start backend
cd backend
npm start
```

## 📁 Project Structure

```
book-auth-system/
├── backend/
│   ├── config/
│   ├── controllers/
│   ├── middleware/
│   ├── models/
│   ├── routes/
│   ├── utils/
│   └── server.js
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── redux/
│   │   ├── services/
│   │   ├── utils/
│   │   └── App.js
│   └── package.json
└── README.md
```

## 🔒 API Endpoints

### Authentication
- POST /api/auth/register - Register new user
- POST /api/auth/login - User login
- POST /api/auth/verify-email - Verify email
- POST /api/auth/forgot-password - Request password reset
- POST /api/auth/reset-password - Reset password

### Books
- GET /api/books - Get all books
- GET /api/books/:id - Get single book
- POST /api/books - Create new book (Auth required)
- PUT /api/books/:id - Update book (Auth required)
- DELETE /api/books/:id - Delete book (Admin only)
- POST /api/books/:id/review - Add book review
- GET /api/books/search - Search books

### Users
- GET /api/users/profile - Get user profile
- PUT /api/users/profile - Update profile
- GET /api/users/borrowed-books - Get borrowed books
- POST /api/users/borrow/:bookId - Borrow book

## 🔐 Security Best Practices

1. Authentication
   - Implement JWT with refresh tokens
   - Store passwords using bcrypt (salt rounds: 10)
   - Implement rate limiting for login attempts

2. API Security
   - Input validation using express-validator
   - Implement request size limits
   - Use helmet for security headers
   - Enable CORS with specific origins

3. Error Handling
   - Custom error classes
   - Global error middleware
   - Structured error responses

## 📝 Testing

```bash
# Run backend tests
cd backend
npm test

# Run frontend tests
cd frontend
npm test
```

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.
