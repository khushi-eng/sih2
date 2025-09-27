# AI Learning Path Generator - Deployment Guide

This guide provides step-by-step instructions for deploying the AI-Powered Personalized Learning Path Generator application.

## Prerequisites

- Node.js (v16 or higher)
- MongoDB (local or MongoDB Atlas)
- Git
- Vercel account (for frontend deployment)
- Render account (for backend deployment)

## Local Development Setup

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd ai-learning-path-generator
```

### 2. Install Dependencies

```bash
# Install root dependencies
npm install

# Install backend dependencies
cd server
npm install

# Install frontend dependencies
cd ../client
npm install
```

### 3. Environment Setup

#### Backend Environment Variables

Create `server/.env` file:

```env
# MongoDB Connection
MONGODB_URI=mongodb://localhost:27017/ai-learning-path
# For MongoDB Atlas: mongodb+srv://username:password@cluster.mongodb.net/ai-learning-path

# JWT Secret
JWT_SECRET=your-super-secret-jwt-key-here

# Server Configuration
PORT=5000
NODE_ENV=development

# CORS Configuration
CLIENT_URL=http://localhost:3000
```

#### Frontend Environment Variables

Create `client/.env` file:

```env
REACT_APP_API_URL=http://localhost:5000
```

### 4. Start Development Servers

```bash
# From root directory
npm run dev

# Or start individually:
# Backend
cd server && npm run dev

# Frontend
cd client && npm start
```

The application will be available at:
- Frontend: http://localhost:3000
- Backend API: http://localhost:5000

## Production Deployment

### Option 1: Vercel + Render (Recommended)

#### Backend Deployment on Render

1. **Create a new Web Service on Render**
   - Connect your GitHub repository
   - Set build command: `cd server && npm install`
   - Set start command: `cd server && npm start`
   - Set environment variables:
     ```
     MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/ai-learning-path
     JWT_SECRET=your-production-jwt-secret
     NODE_ENV=production
     CLIENT_URL=https://your-frontend-url.vercel.app
     ```

2. **Deploy Backend**
   - Render will automatically deploy when you push to your repository
   - Note the backend URL (e.g., `https://your-app.onrender.com`)

#### Frontend Deployment on Vercel

1. **Create a new project on Vercel**
   - Connect your GitHub repository
   - Set root directory to `client`
   - Set build command: `npm run build`
   - Set output directory: `build`

2. **Environment Variables**
   ```
   REACT_APP_API_URL=https://your-backend-url.onrender.com
   ```

3. **Deploy Frontend**
   - Vercel will automatically deploy when you push to your repository

### Option 2: Vercel + Railway

#### Backend Deployment on Railway

1. **Create a new project on Railway**
   - Connect your GitHub repository
   - Set root directory to `server`
   - Set environment variables:
     ```
     MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/ai-learning-path
     JWT_SECRET=your-production-jwt-secret
     NODE_ENV=production
     CLIENT_URL=https://your-frontend-url.vercel.app
     ```

2. **Deploy Backend**
   - Railway will automatically deploy when you push to your repository

### Option 3: Full Vercel Deployment

#### Backend on Vercel (Serverless)

1. **Create `vercel.json` in root directory:**

```json
{
  "version": 2,
  "builds": [
    {
      "src": "server/index.js",
      "use": "@vercel/node"
    }
  ],
  "routes": [
    {
      "src": "/api/(.*)",
      "dest": "server/index.js"
    }
  ]
}
```

2. **Deploy both frontend and backend to Vercel**
   - Connect your GitHub repository
   - Vercel will detect the configuration and deploy both

## MongoDB Setup

### Option 1: MongoDB Atlas (Recommended for Production)

1. **Create MongoDB Atlas Account**
   - Go to https://www.mongodb.com/atlas
   - Create a free cluster

2. **Configure Database**
   - Create a database named `ai-learning-path`
   - Create collections: `users`, `learnerprofiles`, `nsqfprograms`, `labourmarketdatas`

3. **Get Connection String**
   - Copy the connection string
   - Replace `<password>` with your database password
   - Use this in your environment variables

### Option 2: Local MongoDB

1. **Install MongoDB**
   ```bash
   # macOS
   brew install mongodb-community

   # Ubuntu
   sudo apt-get install mongodb

   # Windows
   # Download from https://www.mongodb.com/try/download/community
   ```

2. **Start MongoDB**
   ```bash
   mongod
   ```

## Environment Variables Reference

### Backend (.env)

| Variable | Description | Example |
|----------|-------------|---------|
| `MONGODB_URI` | MongoDB connection string | `mongodb://localhost:27017/ai-learning-path` |
| `JWT_SECRET` | Secret key for JWT tokens | `your-super-secret-jwt-key-here` |
| `PORT` | Server port | `5000` |
| `NODE_ENV` | Environment mode | `development` or `production` |
| `CLIENT_URL` | Frontend URL for CORS | `http://localhost:3000` |

### Frontend (.env)

| Variable | Description | Example |
|----------|-------------|---------|
| `REACT_APP_API_URL` | Backend API URL | `http://localhost:5000` |

## Testing the Deployment

### 1. Test Backend API

```bash
# Health check
curl https://your-backend-url.com/api/health

# Test NSQF programs endpoint
curl https://your-backend-url.com/api/nsqf
```

### 2. Test Frontend

1. Visit your frontend URL
2. Try registering a new account
3. Complete the profile setup
4. Check recommendations

### 3. Test Full Flow

1. Register as a learner
2. Complete profile setup
3. View recommended programs
4. Check learning path generation

## Troubleshooting

### Common Issues

1. **CORS Errors**
   - Ensure `CLIENT_URL` in backend matches your frontend URL
   - Check that CORS is properly configured

2. **Database Connection Issues**
   - Verify MongoDB URI is correct
   - Check network connectivity
   - Ensure database user has proper permissions

3. **Build Failures**
   - Check Node.js version compatibility
   - Ensure all dependencies are installed
   - Check for TypeScript errors

4. **Environment Variables**
   - Ensure all required variables are set
   - Check variable names match exactly
   - Restart services after changing variables

### Debug Commands

```bash
# Check backend logs
cd server && npm run dev

# Check frontend build
cd client && npm run build

# Test API endpoints
curl -X POST https://your-backend-url.com/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{"name":"Test User","email":"test@example.com","password":"password123","role":"learner"}'
```

## Performance Optimization

### Backend Optimization

1. **Enable Compression**
   ```javascript
   const compression = require('compression');
   app.use(compression());
   ```

2. **Add Caching**
   ```javascript
   const redis = require('redis');
   const client = redis.createClient();
   ```

3. **Database Indexing**
   - Add indexes for frequently queried fields
   - Use MongoDB Atlas for automatic scaling

### Frontend Optimization

1. **Code Splitting**
   - Implement lazy loading for routes
   - Use dynamic imports for heavy components

2. **Image Optimization**
   - Use WebP format
   - Implement lazy loading

3. **Bundle Analysis**
   ```bash
   cd client && npm run build
   npx serve -s build
   ```

## Security Considerations

1. **Environment Variables**
   - Never commit `.env` files
   - Use strong JWT secrets
   - Rotate secrets regularly

2. **API Security**
   - Implement rate limiting
   - Add input validation
   - Use HTTPS in production

3. **Database Security**
   - Use MongoDB Atlas security features
   - Enable IP whitelisting
   - Use strong passwords

## Monitoring and Maintenance

### Health Checks

1. **Backend Health Check**
   ```bash
   curl https://your-backend-url.com/api/health
   ```

2. **Database Health**
   - Monitor connection pool
   - Check query performance
   - Set up alerts for failures

### Logging

1. **Backend Logging**
   ```javascript
   const winston = require('winston');
   const logger = winston.createLogger({
     level: 'info',
     format: winston.format.json(),
     transports: [
       new winston.transports.File({ filename: 'error.log', level: 'error' }),
       new winston.transports.File({ filename: 'combined.log' })
     ]
   });
   ```

2. **Frontend Error Tracking**
   - Use Sentry or similar service
   - Implement error boundaries
   - Log user interactions

## Scaling Considerations

1. **Database Scaling**
   - Use MongoDB Atlas for automatic scaling
   - Implement read replicas
   - Consider sharding for large datasets

2. **Application Scaling**
   - Use load balancers
   - Implement horizontal scaling
   - Consider microservices architecture

3. **CDN Integration**
   - Use Vercel's CDN for static assets
   - Implement edge caching
   - Optimize for global performance

## Support and Maintenance

### Regular Tasks

1. **Security Updates**
   - Update dependencies monthly
   - Monitor security advisories
   - Apply patches promptly

2. **Performance Monitoring**
   - Monitor response times
   - Track error rates
   - Optimize slow queries

3. **Data Backup**
   - Regular database backups
   - Test restore procedures
   - Document recovery processes

### Getting Help

1. **Documentation**
   - Check API documentation
   - Review error logs
   - Consult deployment logs

2. **Community Support**
   - GitHub Issues
   - Stack Overflow
   - Discord/Slack communities

3. **Professional Support**
   - Consider managed services
   - Hire DevOps consultants
   - Use monitoring services
