# 🌌 Solar System Explorer

A full-stack web application that provides an interactive exploration of our solar system's planets. Built with Node.js, Express, MongoDB, and deployed using Kubernetes with a comprehensive CI/CD pipeline.

![Node.js](https://img.shields.io/badge/Node.js-18%2C%2020-green)
![MongoDB](https://img.shields.io/badge/MongoDB-Database-green)
![Docker](https://img.shields.io/badge/Docker-Containerized-blue)
![Kubernetes](https://img.shields.io/badge/Kubernetes-Orchestrated-blue)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-CI%2FCD-black)
[![NodeJs Application Workflow](https://github.com/shashi2504/nodejs-application/actions/workflows/solar-system.yml/badge.svg)](https://github.com/shashi2504/nodejs-application/actions/workflows/solar-system.yml)

## 🚀 Features

- **Interactive Planet Explorer**: Browse through 8 planets of our solar system with detailed information
- **Dynamic Data Loading**: Real-time planet data fetched from MongoDB database
- **Responsive Design**: Beautiful UI with animated solar system background
- **Health Monitoring**: Built-in health check endpoints for production monitoring
- **Container-Ready**: Fully containerized application with Docker support
- **Cloud-Native**: Kubernetes-ready with separate development and production configurations

## 🛠️ Tech Stack

### Backend
- **Runtime**: Node.js (v18, v20)
- **Framework**: Express.js
- **Database**: MongoDB with Mongoose ODM
- **Testing**: Mocha, Chai, NYC for code coverage

### Frontend
- **HTML5/CSS3**: Responsive design with custom animations
- **JavaScript**: Vanilla JS for client-side interactions
- **Styling**: Custom CSS with gradient backgrounds and animations

### DevOps
- **Containerization**: Docker
- **Orchestration**: Kubernetes
- **CI/CD**: GitHub Actions
- **Cloud Storage**: AWS S3 for test reports
- **Monitoring**: Slack notifications

## 📋 Prerequisites

- Node.js (v18 or v20)
- MongoDB (local or cloud instance)
- Docker (for containerization)
- Kubernetes cluster (for deployment)

## 🔧 Installation

### Local Development

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd solar-system
   

2. **Install dependencies**
   ```bash
   npm install

3. **Set up environment variables**
   Create a \`.env\` file in the root directory:
   ```env
   MONGO_URI=mongodb://localhost:27017/superData
   MONGO_USERNAME=your-username
   MONGO_PASSWORD=your-password
   NODE_ENV=development
   

4. **Start the application**
   ```bash
   npm start
   ```

   The application will be available at \`http://localhost:3000\`

### Docker Setup

1. **Build the Docker image**
   ```bash
   docker build -t solar-system:latest .

2. **Run the container**
   ```bash
   docker run -d \
     -p 3000:3000 \
     -e MONGO_URI=your-mongo-uri \
     -e MONGO_USERNAME=your-username \
     -e MONGO_PASSWORD=your-password \
     solar-system:latest
   

## 🧪 Testing

### Run Unit Tests
```bash
npm test
```

### Run Tests with Coverage
```bash
npm run coverage
```

### Test Endpoints
- **Health Check**: \`GET /live\` - Returns \`{"status": "live"}\`
- **Readiness Check**: \`GET /ready\` - Returns \`{"status": "ready"}\`
- **OS Info**: \`GET /os\` - Returns pod hostname and environment
- **Planet Data**: \`POST /planet\` - Returns planet information

## 📁 Project Structure

```
solar-system/
├── app.js                  # Express application setup
├── app-controller.js       # Client-side JavaScript
├── app.test.js            # Test suite
├── index.html             # Frontend interface
├── package.json           # Dependencies and scripts
├── Dockerfile             # Container configuration
├── .github/
│   ├── workflows/
│   │   ├── solar-system.yml      # Main CI/CD pipeline
│   │   └── reuse-deployments.yml # Reusable deployment workflow
│   └── custom-actions/           # Custom GitHub Actions
├── kubernetes/
│   ├── development/       # Dev environment K8s manifests
│   └── production/        # Prod environment K8s manifests
└── images/               # Static assets
```

## 🚀 CI/CD Pipeline

The project includes a comprehensive GitHub Actions pipeline that:

1. **Unit Testing**: Runs tests on Node.js v18 and v20
2. **Code Coverage**: Generates coverage reports with NYC/Istanbul
3. **Containerization**: Builds and pushes Docker images to Docker Hub and GHCR
4. **Artifact Storage**: Uploads test reports to AWS S3
5. **Deployment**: Automated deployment to Kubernetes (dev/prod)
6. **Integration Testing**: Validates deployment health
7. **Notifications**: Sends status updates to Slack

### Pipeline Triggers
- **Main branch**: Deploys to production
- **Feature branches**: Deploys to development

## 🌐 API Documentation

### Get Planet Information
```http
POST /planet
Content-Type: application/json

{
  "id": 3
}
```

**Response:**
```json
{
  "id": 3,
  "name": "Earth",
  "description": "Earth is the third planet from the Sun...",
  "image": "https://example.com/earth.jpg",
  "velocity": "29.78 km/s",
  "distance": "149.6 million km"
}
```

## 🐳 Kubernetes Deployment

### Deploy to Development
```bash
kubectl apply -f kubernetes/development/
```

### Deploy to Production
```bash
kubectl apply -f kubernetes/production/
```

### Required Secrets
```bash
kubectl create secret generic mongo-db-creds \
  --from-literal=MONGO_URI=your-uri \
  --from-literal=MONGO_USERNAME=your-username \
  --from-literal=MONGO_PASSWORD=your-password
```

## 🔒 Security

- MongoDB credentials stored as Kubernetes secrets
- Environment-specific configurations
- Health check endpoints for monitoring
- Secure container registry (GHCR)

## 👥 Contact

For questions or support, please open an issue in the GitHub repository.

---

**Note**: Make sure to populate your MongoDB with planet data before running the application. The application expects planets with IDs 1-8 in the database.


