# 🏥 Pneumonia Detection App

A web-based medical application that uses **Machine Learning** and **Convolutional Neural Networks** to assist radiologists in detecting pneumonia from chest X-ray images. This application provides a complete workflow for medical professionals to upload, analyze, and report on patient X-ray images with AI-powered assistance.

![App Overview](Sample%20Image/1.jpg)

## 🎯 Features

- **🤖 AI-Powered Detection**: Uses TensorFlow.js CNN model for pneumonia detection
- **👥 Dual User System**: Separate interfaces for Radiographers and Radiologists
- **📊 Patient Management**: Complete patient record management system
- **📧 Automated Reporting**: Email-based diagnosis reports to patients
- **🔐 Secure Authentication**: JWT-based authentication system
- **📱 Responsive Design**: Mobile-friendly interface
- **🖼️ Image Processing**: Advanced X-ray image viewing and analysis

![User Interface](Sample%20Image/2.jpg)

## 🏥 Medical Workflow

The application streamlines the entire pneumonia detection process from patient intake to final diagnosis, ensuring efficient collaboration between medical professionals.

![Medical Workflow](Sample%20Image/Untitled%20design%20(1).jpg)

## 🏗️ Technology Stack

### Backend
- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **MongoDB** - Database
- **Mongoose** - ODM for MongoDB
- **JWT** - Authentication
- **Multer** - File upload handling
- **SendGrid** - Email service

### Frontend
- **Handlebars (HBS)** - Templating engine
- **Bootstrap** - CSS framework
- **TensorFlow.js** - Client-side ML inference
- **Vanilla JavaScript** - Client-side logic

### Machine Learning
- **TensorFlow.js** - ML model runtime
- **CNN Architecture** - 5-layer convolutional neural network
- **Binary Classification** - Normal vs Pneumonia detection

## 🚀 Quick Start

### Prerequisites
- Node.js (v14 or higher)
- MongoDB
- SendGrid API key

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd pneumonia-detection-app-main
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Environment Setup**
   Create a `config/dev.env` file with the following variables:
   ```env
   PORT=3000
   MONGODB_URL=mongodb://localhost:27017/pneumonia-detection
   SENDGRID_API_KEY=your_sendgrid_api_key
   ```

4. **Start the application**
   ```bash
   # Development mode
   npm run dev
   
   # Production mode
   npm start
   ```

5. **Access the application**
   Open your browser and navigate to `http://localhost:3000`

## 📋 User Workflow

The application follows a structured workflow that ensures proper medical protocols and efficient collaboration between healthcare professionals.

### For Radiographers
1. **Login/Register** to the Radiographer portal
2. **Upload Patient Data** including X-ray images
3. **Manage Patient Records** - view, edit, delete
4. **Track Patient Information** with complete medical history

### For Radiologists
1. **Login/Register** to the Radiologist portal
2. **Review Patient Records** uploaded by radiographers
3. **Analyze X-ray Images** using the AI model
4. **Generate Reports** and send to patients via email
5. **Make Final Medical Decisions** based on AI assistance

![Workflow Diagram](Sample%20Image/3.jpg)

## 🤖 Machine Learning Model

The application uses a pre-trained Convolutional Neural Network with the following architecture:

- **Input Layer**: 64x64x3 RGB images
- **Convolutional Layers**: 5 Conv2D layers with ReLU activation
- **Pooling Layers**: MaxPooling2D for dimensionality reduction
- **Dense Layers**: Fully connected layers with dropout
- **Output Layer**: Sigmoid activation for binary classification

### Model Performance
- **Accuracy**: Optimized for medical image classification
- **Input Format**: Chest X-ray images (JPEG/PNG)
- **Output**: Probability score (0 = Normal, 1 = Pneumonia)

## 📊 Database Schema

### Collections

#### Radiographers
```javascript
{
  firstName: String,
  lastName: String,
  email: String (unique),
  password: String,
  address: String,
  mobile: String,
  country: String,
  tokens: [String]
}
```

#### Radiologists
```javascript
{
  firstName: String,
  lastName: String,
  email: String (unique),
  password: String,
  address: String,
  mobile: String,
  country: String,
  tokens: [String]
}
```

#### Patients
```javascript
{
  name: String,
  email: String,
  age: String,
  mobile: String,
  date: String,
  xray: {
    data: Buffer
  },
  radiographerName: String
}
```

## 🔐 Security Features

- **JWT Authentication** for secure user sessions
- **Password Validation** (minimum 8 characters)
- **Email Validation** using validator library
- **Role-based Access Control** for different user types
- **Secure File Upload** with type validation

## 📧 Email Integration

The application automatically sends diagnosis reports to patients via SendGrid:

- **HTML Email Templates** with professional formatting
- **Patient Details** including test results
- **X-ray Image Attachments** for reference
- **Different Templates** for Normal vs Pneumonia results

## 🛠️ API Endpoints

### Authentication
- `POST /Radiographer/signin/login` - Radiographer login
- `POST /Radiologist/signin/login` - Radiologist login
- `GET /radiographer/Account/logout` - Logout
- `GET /radiologist/Account/logout` - Logout

### Patient Management
- `POST /Radiographer/Account/addPatient` - Add new patient
- `GET /Radiographer/Account/getPatient` - Get all patients
- `GET /Radiographer/Account/getPatientImage` - Get patient X-ray
- `GET /Radiographer/Account/deletePatient` - Delete patient

### Analysis & Reporting
- `GET /Radiologist/Account/getModel` - Get ML model
- `GET /Radiologist/Account/sendPatientInfo` - Send diagnosis report
- `POST /Contact/Query` - Contact form submission

## 📁 Project Structure

```
pneumonia-detection-app-main/
├── src/
│   ├── app.js                 # Main Express server
│   ├── models/
│   │   └── user.js           # Database schemas
│   ├── routers/
│   │   └── userRouters.js    # API routes
│   ├── middleware/
│   │   ├── auth.js           # Radiographer auth
│   │   └── radiologistAuth.js # Radiologist auth
│   └── db/
│       └── mongoose.js       # Database connection
├── public/
│   ├── tfjs-models/          # ML model files
│   ├── radiographer/         # Radiographer frontend JS
│   ├── radiologist/          # Radiologist frontend JS
│   └── assets/               # CSS, JS, images
├── templates/views/          # Handlebars templates
├── package.json
└── README.md
```

## 🚀 Deployment

### Environment Variables
Make sure to set the following environment variables:

```env
PORT=3000
MONGODB_URL=mongodb://localhost:27017/pneumonia-detection
SENDGRID_API_KEY=your_sendgrid_api_key
```

### Production Considerations
- Use a production MongoDB instance
- Set up proper error handling and logging
- Configure HTTPS for secure data transmission
- Set up monitoring and backup systems

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the ISC License - see the [package.json](package.json) file for details.

## 👥 Team

- **Meldon D'Cunha** - [meldondcunha10@gmail.com](mailto:meldondcunha10@gmail.com)
- **Nimesh Naik** - [nimesh.naik19@gmail.com](mailto:nimesh.naik19@gmail.com)

## 📞 Contact

- 9892500239

## ⚠️ Disclaimer

This application is designed to **assist** medical professionals in their diagnosis process. It should **not replace** professional medical judgment. Always consult with qualified healthcare providers for medical decisions.

---

**Built with ❤️ for better healthcare**
