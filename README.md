# Property Listing Backend

A robust backend service for property listing and management with features like property search, favorites, recommendations, and caching.

## Features

- 🔐 Authentication & Authorization
- 🏠 Property Management (CRUD)
- ❤️ Favorites System
- 🔍 Advanced Property Search
- 💡 Smart Recommendations
- ⚡ Redis Caching
- 📊 Filtering & Pagination

## Tech Stack

- **Runtime**: Node.js
- **Framework**: Express.js
- **Language**: TypeScript
- **Database**: MongoDB
- **Cache**: Redis (Upstash)
- **Authentication**: JWT

## Prerequisites

- Node.js (v14 or higher)
- MongoDB
- Redis (Upstash)
- npm or yarn

## Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/property-listing-backend.git
cd property-listing-backend
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file in the root directory:
```env
# Server Configuration
PORT=5000
NODE_ENV=development

# MongoDB Configuration
MONGODB_URI=your_mongodb_uri

# Redis Configuration
REDIS_URL=your_redis_url

# JWT Configuration
JWT_SECRET=your_jwt_secret
JWT_EXPIRES_IN=24h
```

4. Start the development server:
```bash
npm run dev
```

## API Endpoints

### Authentication
- `POST /auth/register` - Register a new user
- `POST /auth/login` - Login user

### Properties
- `GET /properties` - Get all properties
- `GET /properties/:id` - Get property by ID
- `POST /properties` - Create new property
- `PUT /properties/:id` - Update property
- `DELETE /properties/:id` - Delete property
- `GET /properties/search` - Search properties

### Favorites
- `GET /favorites` - Get user's favorites
- `POST /favorites/:propertyId` - Add to favorites
- `DELETE /favorites/:propertyId` - Remove from favorites
- `GET /favorites/check/:propertyId` - Check favorite status

### Recommendations
- `GET /recommendations` - Get personalized recommendations
- `POST /recommendations/search` - Search with preferences

## Caching Strategy

The application uses Redis (Upstash) for caching with the following patterns:

### Cache Keys
- Property: `property:${id}`
- All Properties: `properties:all`
- Search Results: `search:${query}`
- User Favorites: `user:${userId}:favorites`
- Recommendations: `user:${userId}:recommendations`

### Cache TTL
- Default: 1 hour (3600 seconds)
- Configurable per cache operation

### Cache Invalidation
- On property create/update/delete
- On favorite add/remove
- On user preference changes

## Error Handling

The API uses standardized error responses:
```json
{
  "error": {
    "message": "Error description",
    "code": "ERROR_CODE"
  }
}
```

Common error codes:
- `UNAUTHORIZED`: Authentication required
- `FORBIDDEN`: Insufficient permissions
- `NOT_FOUND`: Resource not found
- `VALIDATION_ERROR`: Invalid request data
- `INTERNAL_ERROR`: Server error


## Development

### Scripts
- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm start` - Start production server

### Code Structure
```
src/
├── config/         # Configuration files
├── controllers/    # Route controllers
├── middleware/     # Custom middleware
├── models/         # Database models
├── routes/         # API routes
├── services/       # Business logic
├── app.ts         # Express app setup
└── index.ts       # Application entry point
```

```

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

