# PredictiveEstates 🏡

A full-stack real estate application with machine learning-powered property price prediction. Built with React, Node.js, and Python ML models.

## 🌟 Features

### Core Features
- **Property Listings**: Browse and view detailed property information
- **User Authentication**: Secure login/logout with Auth0
- **Property Management**: Add, edit, and manage property listings
- **Favorites & Bookings**: Save favorite properties and book visits
- **Interactive Maps**: Location-based property search with Leaflet
- **Responsive Design**: Modern UI with Mantine components

### AI-Powered Features
- **Price Prediction**: Machine learning model for property price estimation
- **Intelligent Search**: Search properties by location, price, and features

## 🛠️ Tech Stack

### Frontend
- **React 18** - Modern React with hooks
- **Vite** - Fast build tool and development server
- **Mantine** - React components library
- **React Router** - Client-side routing
- **Leaflet** - Interactive maps
- **Framer Motion** - Animations
- **React Query** - Data fetching and caching
- **Auth0** - Authentication and authorization
- **Axios** - HTTP client

### Backend
- **Node.js** - Server runtime
- **Express.js** - Web application framework
- **Prisma** - Database ORM
- **MongoDB** - NoSQL database
- **Auth0** - JWT authentication
- **Python Shell** - ML model integration

### Machine Learning
- **Python** - ML model development
- **Scikit-learn** - Machine learning algorithms
- **Pandas** - Data manipulation
- **NumPy** - Numerical computing
- **Random Forest** - Regression model
- **StandardScaler** - Feature normalization

## 📁 Project Structure

```
PredictiveEstates/
├── client/                 # React frontend application
│   ├── src/
│   │   ├── components/     # Reusable UI components
│   │   ├── pages/          # Page components
│   │   ├── hooks/          # Custom React hooks
│   │   ├── context/        # React context providers
│   │   └── utils/          # Utility functions
│   ├── public/             # Static assets
│   └── package.json
├── server/                 # Node.js backend API
│   ├── controllers/        # Route handlers
│   ├── routes/             # API routes
│   ├── config/             # Configuration files
│   ├── prisma/             # Database schema
│   ├── model.pkl           # Trained ML model
│   ├── predict.py          # ML prediction script
│   └── package.json
└── MachineLearning/        # ML model development
    ├── modeltrain.py       # Model training script
    ├── housing.csv         # Training dataset
    └── Untitled.ipynb      # Jupyter notebook
```

## 🚀 Getting Started

### Prerequisites
- Node.js (v16 or higher)
- Python (v3.8 or higher)
- MongoDB Atlas account or local MongoDB
- Auth0 account

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/PredictiveEstates.git
   cd PredictiveEstates
   ```

2. **Set up the backend**
   ```bash
   cd server
   npm install
   ```

3. **Set up the frontend**
   ```bash
   cd ../client
   npm install
   ```

4. **Install Python dependencies**
   ```bash
   pip install pandas numpy scikit-learn pickle-mixin
   ```

### Environment Configuration

1. **Server Environment (.env)**
   ```env
   DATABASE_URL="mongodb+srv://username:password@cluster.mongodb.net/database"
   PORT=8000
   ```

2. **Auth0 Configuration**
   - Update `client/src/main.jsx` with your Auth0 domain and client ID
   - Update `server/config/auth0Config.js` with your Auth0 settings

### Database Setup

1. **Generate Prisma client**
   ```bash
   cd server
   npx prisma generate
   ```

2. **Push database schema**
   ```bash
   npx prisma db push
   ```

### Running the Application

1. **Start the backend server**
   ```bash
   cd server
   npm run dev
   ```

2. **Start the frontend development server**
   ```bash
   cd client
   npm run dev
   ```

3. **Access the application**
   - Frontend: `http://localhost:5173`
   - Backend API: `http://localhost:8000`

## 🤖 Machine Learning Model

### Model Details
- **Algorithm**: Random Forest Regressor
- **Features**: Location, property age, rooms, bedrooms, population, income, proximity to ocean
- **Preprocessing**: Log transformation, feature scaling, one-hot encoding
- **Performance**: Trained on California housing dataset

### Prediction API
The ML model is integrated via a Python script that processes property features and returns price predictions.

**Endpoint**: `POST /api/predict`

**Request Body**:
```json
{
  "latitude": 37.85,
  "longitude": -122.22,
  "housing_median_age": 41.0,
  "total_rooms": 880.0,
  "total_bedrooms": 129.0,
  "population": 322.0,
  "households": 126.0,
  "median_income": 8.3252,
  "ocean_proximity": "NEAR BAY"
}
```

## 🔧 API Endpoints

### User Routes
- `POST /api/user/register` - Register new user
- `POST /api/user/bookVisit/:id` - Book property visit
- `POST /api/user/allBookings` - Get user bookings
- `POST /api/user/toFav/:id` - Add to favorites
- `POST /api/user/allFav` - Get user favorites

### Property Routes
- `GET /api/residency/allresd` - Get all properties
- `GET /api/residency/:id` - Get specific property
- `POST /api/residency/create` - Create new property (authenticated)

### ML Prediction
- `POST /api/predict` - Get property price prediction

## 📱 Key Components

### Frontend Components
- **Hero**: Landing page with search functionality
- **PropertyCard**: Property display cards with favorites
- **SearchBar**: Property search with filters
- **Map**: Interactive property location maps
- **AddPropertyModal**: Property creation form
- **Prediction**: ML-powered price prediction interface

### Backend Controllers
- **userCntrl**: User management and authentication
- **resdCntrl**: Property CRUD operations
- **predict.py**: ML model inference

## 🎨 UI/UX Features

- **Responsive Design**: Mobile-first approach
- **Dark/Light Mode**: Theme switching capability
- **Interactive Maps**: Real-time location selection
- **Image Upload**: Cloudinary integration for property images
- **Form Validation**: Client and server-side validation
- **Loading States**: Smooth loading animations
- **Error Handling**: User-friendly error messages

## 🔐 Security Features

- **JWT Authentication**: Secure token-based auth with Auth0
- **Protected Routes**: Authentication required for sensitive operations
- **Input Validation**: Server-side data validation
- **CORS Configuration**: Proper cross-origin resource sharing
- **Environment Variables**: Secure configuration management

## 📊 Data Models

### User Model
```javascript
{
  id: String,
  name: String,
  email: String (unique),
  image: String,
  bookedVisits: Json[],
  favResidenciesID: String[],
  ownedResidencies: Residency[]
}
```

### Property (Residency) Model
```javascript
{
  id: String,
  title: String,
  description: String,
  price: Number,
  address: String,
  city: String,
  country: String,
  image: String,
  facilities: Json,
  userEmail: String,
  createdAt: DateTime,
  updatedAt: DateTime
}
```

## 🚀 Deployment

### Frontend (Vercel/Netlify)
1. Build the project: `npm run build`
2. Deploy the `dist` folder
3. Update environment variables

### Backend (Heroku/Railway)
1. Set up environment variables
2. Deploy the server directory
3. Ensure MongoDB connection

### ML Model
The trained model files (`model.pkl`, `scaler.pkl`, `feature_order.pkl`) are included in the server directory for deployment.

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 🏆 Acknowledgments

- **KU 6th Semester Project** - Part of university curriculum
- **California Housing Dataset** - Used for ML model training
- **Auth0** - Authentication services
- **Mantine** - React components library
- **Leaflet** - Interactive maps

## 📧 Contact

For questions or support, please contact:
- **Developer**: Shubin Pokhrel
- **Email**: shubinpokhrel4@gmail.com
- **University**: KU (Kathmandu University)
- **Semester**: 6th Semester Project

---

**Built with ❤️ for the future of real estate technology**
