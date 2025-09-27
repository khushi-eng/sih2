# AI Learning Path Generator - Quick Start

## 🚀 Quick Start (5 minutes)

### Prerequisites
- Node.js 16+ installed
- MongoDB running locally or MongoDB Atlas account

### 1. Install Dependencies
```bash
npm run install-all
```

### 2. Setup Environment
```bash
# Copy environment template
cp server/env.example server/.env

# Edit server/.env with your MongoDB connection string
# For local MongoDB: mongodb://localhost:27017/ai-learning-path
# For MongoDB Atlas: mongodb+srv://username:password@cluster.mongodb.net/ai-learning-path
```

### 3. Start the Application
```bash
npm run dev
```

### 4. Access the Application
- Frontend: http://localhost:3000
- Backend API: http://localhost:5000

## 🎯 Test the Application

### 1. Register a New Account
- Go to http://localhost:3000/register
- Create an account as a "Learner"
- Use any email and password

### 2. Complete Profile Setup
- After registration, you'll be redirected to profile setup
- Fill in your educational background, skills, and career goals
- Complete all 4 steps

### 3. View Recommendations
- Go to the Dashboard to see your personalized learning path
- Check the "Recommendations" page for AI-powered suggestions
- Browse NSQF programs in the "Programs" section

### 4. Test Different Roles
- Register as a "Trainer" to access trainer dashboard
- Register as an "Admin" to access admin dashboard

## 📊 Sample Data

The application comes with pre-loaded sample data:

### NSQF Programs
- Software Development Fundamentals (Level 3)
- Data Analysis and Visualization (Level 4)
- Medical Assistant Training (Level 2)
- Farm Management and Modern Agriculture (Level 3)
- Tourism and Hospitality Management (Level 4)

### Labour Market Data
- Technology sector trends and skills demand
- Healthcare sector job market information
- Agriculture sector growth projections

## 🔧 Development

### Project Structure
```
├── client/                 # React frontend
│   ├── src/
│   │   ├── components/     # UI components
│   │   ├── pages/         # Page components
│   │   ├── contexts/      # React contexts
│   │   └── lib/          # Utilities
├── server/                # Express backend
│   ├── models/           # MongoDB models
│   ├── routes/           # API routes
│   ├── middleware/       # Custom middleware
│   └── utils/            # Utility functions
```

### Key Features Implemented

#### ✅ Authentication System
- JWT-based authentication
- Role-based access control (Learner, Trainer, Admin)
- Secure password hashing

#### ✅ Learner Profile Management
- Educational background tracking
- Skills assessment (technical & soft skills)
- Career goals and preferences
- Socio-economic context

#### ✅ AI Recommendation Engine
- Rules-based recommendation system
- Profile vector generation
- NSQF level mapping
- Career path suggestions
- Skill gap analysis

#### ✅ NSQF Program Management
- Complete program catalog
- Level-based filtering
- Sector-wise organization
- Prerequisites and outcomes

#### ✅ Dashboard Interfaces
- Learner dashboard with progress tracking
- Trainer dashboard for module management
- Admin dashboard for system management

#### ✅ Responsive Design
- Mobile-friendly interface
- Modern UI with TailwindCSS
- shadcn/ui components
- Dark/light theme support

## 🚀 Deployment

### Quick Deploy to Vercel
1. Push your code to GitHub
2. Connect to Vercel
3. Set environment variables
4. Deploy!

See [DEPLOYMENT.md](DEPLOYMENT.md) for detailed deployment instructions.

### Environment Variables Needed
```env
# Backend
MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/ai-learning-path
JWT_SECRET=your-super-secret-jwt-key-here
CLIENT_URL=https://your-frontend-url.vercel.app

# Frontend
REACT_APP_API_URL=https://your-backend-url.vercel.app
```

## 🎓 Learning Path Features

### Profile-Based Recommendations
The AI engine analyzes:
- Educational background
- Current skills (technical & soft)
- Career objectives
- Socio-economic factors
- Learning preferences

### NSQF Integration
- Maps learner profiles to NSQF levels (1-8)
- Suggests appropriate programs
- Creates structured learning paths
- Tracks progress through levels

### Career Insights
- Industry trends and growth projections
- Salary expectations based on market data
- Skill demand analysis
- Regional job market information

## 🔍 API Endpoints

### Authentication
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `GET /api/auth/me` - Get current user

### Learner Profile
- `GET /api/learner-profile` - Get profile
- `POST /api/learner-profile` - Create/update profile
- `PUT /api/learner-profile/skills` - Update skills
- `GET /api/learner-profile/stats` - Get statistics

### NSQF Programs
- `GET /api/nsqf` - Get programs (with filtering)
- `GET /api/nsqf/:id` - Get specific program
- `POST /api/nsqf` - Create program (Admin)

### Recommendations
- `POST /api/recommend` - Get personalized recommendations
- `GET /api/recommend/path/:level` - Get learning path for level
- `GET /api/recommend/career-insights` - Get career insights

## 🛠️ Customization

### Adding New NSQF Programs
1. Use the admin dashboard
2. Or add directly to the database
3. Follow the NSQF program schema

### Modifying Recommendation Algorithm
1. Edit `server/routes/recommend.js`
2. Adjust scoring weights
3. Add new recommendation factors

### Styling Changes
1. Modify TailwindCSS classes
2. Update shadcn/ui components
3. Customize theme in `client/src/index.css`

## 📈 Future Enhancements

### Planned Features
- Machine learning model integration
- Advanced analytics dashboard
- Mobile app development
- Integration with learning management systems
- Real-time progress tracking
- Social learning features

### AI/ML Improvements
- Implement collaborative filtering
- Add content-based recommendations
- Use deep learning for better predictions
- Integrate with external APIs (LinkedIn, job portals)

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📄 License

MIT License - see LICENSE file for details

## 🆘 Support

- Check the [DEPLOYMENT.md](DEPLOYMENT.md) for deployment issues
- Review API documentation in the code
- Check GitHub issues for known problems
- Create an issue for bugs or feature requests

---

**Ready to start your personalized learning journey?** 🎯

Register now and discover your AI-powered learning path!
