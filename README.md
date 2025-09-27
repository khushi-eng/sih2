# AI Learning Path Generator

A full-stack MERN web application that helps learners choose the right vocational training by generating personalized learning paths based on NSQF (National Skills Qualifications Framework) levels.

## 🚀 Quick Start

```bash
# Install dependencies
npm run install-all

# Setup environment (copy server/env.example to server/.env)
# Add your MongoDB connection string

# Start development servers
npm run dev
```

Access the application at:
- Frontend: http://localhost:3000
- Backend API: http://localhost:5000

## ✨ Features

- **AI-Powered Recommendations**: Personalized learning paths based on learner profile
- **NSQF Integration**: Maps profiles to National Skills Qualifications Framework levels
- **Role-Based Access**: Learner, Trainer, and Admin dashboards
- **Progress Tracking**: Visual dashboards with progress charts
- **Responsive Design**: Mobile-friendly interface with modern UI
- **Real-Time Updates**: Dynamic recommendations as learners progress

## 🎯 User Roles

### Learner
- Complete profile setup with education, skills, and goals
- Receive AI-powered learning recommendations
- Track progress through NSQF levels
- View personalized career paths

### Trainer
- Manage training modules and content
- Track learner progress and engagement
- View analytics and performance metrics
- Create and update course materials

### Admin
- Manage NSQF programs and qualifications
- Upload labour market data
- Monitor system usage and analytics
- Manage user accounts and permissions

## 🛠️ Tech Stack

- **Frontend**: React, TailwindCSS, shadcn/ui
- **Backend**: Node.js, Express.js
- **Database**: MongoDB
- **Authentication**: JWT
- **AI/ML**: Rules-based recommendation system

## 📊 Sample Data

The application includes:
- 5 sample NSQF programs across different sectors
- Labour market data for Technology, Healthcare, and Agriculture
- Pre-configured user roles and permissions

## 🚀 Deployment

### Vercel + Render (Recommended)
1. Deploy backend to Render
2. Deploy frontend to Vercel
3. Configure environment variables
4. Connect to MongoDB Atlas

### Full Vercel Deployment
1. Use the included `vercel.json` configuration
2. Deploy both frontend and backend to Vercel
3. Configure serverless functions

See [DEPLOYMENT.md](DEPLOYMENT.md) for detailed instructions.

## 📚 Documentation

- [Quick Start Guide](QUICKSTART.md) - Get up and running in 5 minutes
- [Deployment Guide](DEPLOYMENT.md) - Production deployment instructions
- [API Documentation](server/routes/) - Backend API endpoints

## 🔧 Development

### Project Structure
```
├── client/                 # React frontend
├── server/                # Express backend
├── docs/                  # Documentation
└── deployment/            # Deployment configs
```

### Key Components
- **Authentication System**: JWT-based with role management
- **Profile Management**: Comprehensive learner profiling
- **Recommendation Engine**: AI-powered learning path generation
- **NSQF Integration**: Skill-based program mapping
- **Dashboard Interfaces**: Role-specific dashboards

## 🎓 Learning Path Features

### Profile Analysis
- Educational background assessment
- Skills evaluation (technical & soft skills)
- Career goal analysis
- Socio-economic context consideration

### AI Recommendations
- Personalized program suggestions
- Skill gap identification
- Career path recommendations
- Market insights and trends

### Progress Tracking
- Visual progress indicators
- Learning milestone tracking
- Performance analytics
- Achievement recognition

## 🔍 API Endpoints

### Authentication
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `GET /api/auth/me` - Get current user

### Learner Profile
- `GET /api/learner-profile` - Get profile
- `POST /api/learner-profile` - Create/update profile
- `PUT /api/learner-profile/skills` - Update skills

### NSQF Programs
- `GET /api/nsqf` - Get programs with filtering
- `GET /api/nsqf/:id` - Get specific program
- `POST /api/nsqf` - Create program (Admin)

### Recommendations
- `POST /api/recommend` - Get personalized recommendations
- `GET /api/recommend/path/:level` - Get learning path for level

## 🎯 Use Cases

### For Learners
- Discover suitable vocational training programs
- Understand career progression paths
- Identify skills to develop
- Track learning progress

### For Training Providers
- Manage course offerings
- Track learner engagement
- Analyze program effectiveness
- Optimize curriculum design

### For Administrators
- Monitor system usage
- Manage program catalog
- Update market data
- Ensure quality standards

## 🔮 Future Enhancements

- Machine learning model integration
- Advanced analytics dashboard
- Mobile app development
- LMS integration
- Social learning features
- Real-time collaboration

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📄 License

MIT License - see LICENSE file for details

## 🆘 Support

- Check [Quick Start Guide](QUICKSTART.md) for setup issues
- Review [Deployment Guide](DEPLOYMENT.md) for deployment problems
- Create GitHub issues for bugs or feature requests

---

**Ready to transform vocational education with AI?** 🚀

Start your personalized learning journey today!