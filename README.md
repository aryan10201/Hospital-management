# Hospital Management System

A comprehensive web-based hospital management system built with React (TypeScript) frontend and Node.js/Express backend, using MySQL database for data storage.

## 🏥 Overview

This Hospital Management System provides a complete solution for managing hospital operations including patient registration, appointment scheduling, admission/discharge processes, prescription management, test result tracking, and user administration. The system supports multiple user roles with role-based access control.

## ✨ Features

### 🔐 Authentication & Authorization
- **Role-based access control** with 4 user types:
  - **Admin**: User management, system administration
  - **Doctor**: Patient management, appointment viewing, prescription access
  - **Front Desk**: Patient registration, appointment scheduling, admission/discharge
  - **Data Entry**: Prescription management, test result entry
- **Secure authentication** using Basic Auth with Base64 encoding
- **Session management** with protected routes

### 👥 Patient Management
- **Patient Registration**: Complete patient information capture
- **Patient Search**: Search by ID, name, or contact information
- **Patient History**: View admission history and medical records
- **Admission/Discharge**: Room assignment and bed management

### 📅 Appointment System
- **Appointment Scheduling**: Automated doctor assignment based on availability
- **Priority-based Scheduling**: High-priority appointments get preference
- **Appointment Rescheduling**: Easy rescheduling of past appointments
- **Doctor Dashboard**: Real-time appointment viewing for doctors

### 🏥 Room & Bed Management
- **Room Types**: General, Cabin, HDU (High Dependency Unit), ICU
- **Bed Availability**: Real-time bed tracking and allocation
- **Room Assignment**: Automatic room assignment based on availability
- **Discharge Management**: Automatic bed release on discharge

### 💊 Prescription & Treatment Management
- **Prescription Creation**: Add tests and treatments to prescriptions
- **Test Management**: Schedule and track medical tests
- **Treatment Tracking**: Monitor prescribed treatments and dosages
- **Test Results**: Upload test results with images and reports
- **Email Notifications**: Automated alerts for important test results

### 📊 Data Entry & Reporting
- **Test Result Entry**: Upload test results with images and reports
- **Prescription Management**: Add prescriptions for completed appointments
- **Data Validation**: Comprehensive input validation and error handling
- **Weekly Reports**: Automated email reports to doctors

### 👨‍💼 User Administration
- **User Management**: Add, delete, and manage system users
- **Role Assignment**: Assign appropriate roles to users
- **User Validation**: Username and password validation rules
- **Active/Inactive Users**: Soft delete functionality

## 🛠️ Technology Stack

### Frontend
- **React 18** with TypeScript
- **React Router DOM** for navigation
- **Tailwind CSS** for styling
- **Vite** as build tool
- **Moment.js** for date handling
- **Base64** encoding for authentication

### Backend
- **Node.js** with Express.js
- **MySQL** database with mysql2 driver
- **CORS** enabled for cross-origin requests
- **Basic Authentication** for security
- **Nodemailer** for email notifications

### Database
- **MySQL** with comprehensive schema
- **Multiple tables** for users, patients, appointments, prescriptions, tests, treatments, rooms, and admissions
- **Foreign key relationships** for data integrity
- **Sample data** included for testing

## 📁 Project Structure

```
Hospital-management/
├── backend/
│   ├── index.js          # Main server file
│   ├── auth.js           # Authentication middleware
│   ├── Nodemailer.js     # Email service
│   └── weekmail.js       # Weekly email reports
├── client/
│   ├── src/
│   │   ├── components/   # Reusable UI components
│   │   ├── routes/       # Page components
│   │   ├── API.js        # API service layer
│   │   └── main.tsx      # App entry point
│   ├── package.json
│   └── vite.config.ts
└── Database/
    ├── creation.sql      # Database schema
    ├── insertion.sql     # Sample data
    └── deletion.sql      # Cleanup scripts
```

## 🚀 Getting Started

### Prerequisites
- Node.js (v14 or higher)
- MySQL (v8.0 or higher)
- npm or yarn package manager

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd Hospital-management
   ```

2. **Set up the database**
   ```bash
   # Create MySQL database
   mysql -u root -p
   CREATE DATABASE Hospital;
   
   # Run the creation script
   mysql -u root -p Hospital < Database/creation.sql
   
   # Insert sample data
   mysql -u root -p Hospital < Database/insertion.sql
   ```

3. **Configure the backend**
   ```bash
   cd backend
   npm install
   ```
   
   Update database connection in `backend/index.js`:
   ```javascript
   var connection = mysql.createConnection({
     host: "localhost",
     user: "root",
     database: "Hospital",
     password: "your_password"
   });
   ```

4. **Start the backend server**
   ```bash
   cd backend
   node index.js
   ```
   Server will run on `http://localhost:3000`

5. **Configure and start the frontend**
   ```bash
   cd client
   npm install
   npm run dev
   ```
   Frontend will run on `http://localhost:5173`

## 🔑 Default Login Credentials

The system comes with pre-configured users for testing:

| Role | Username | Password | Access Level |
|------|----------|----------|--------------|
| Admin | admin1 | pass | Full system access |
| Doctor | doc1 | pass | Patient & appointment management |
| Front Desk | frontdesk1 | pass | Patient registration & scheduling |
| Data Entry | dataentry1 | pass | Prescription & test management |

## 📱 User Interface

### Admin Dashboard
- User management (add/delete users)
- System administration
- User role assignment

### Doctor Dashboard
- View upcoming appointments
- Search patient information
- Access patient medical history
- View treatments and test results

### Front Desk Interface
- Patient registration
- Appointment scheduling
- Admission/discharge management
- Room and bed management
- Appointment rescheduling

### Data Entry Interface
- Prescription management
- Test result entry
- Test scheduling
- Report generation

## 🔧 API Endpoints

### Authentication
- `GET /` - User authentication

### User Management
- `GET /users` - Get all users (Admin only)
- `POST /users` - Add new user (Admin only)
- `POST /users/delete` - Delete user (Admin only)

### Patient Management
- `POST /register` - Register new patient
- `GET /frontdesk/patients` - Get all patients (Front Desk)
- `GET /doctor/patients` - Get doctor's patients

### Appointments
- `GET /doctor/appointments` - Get doctor's appointments
- `POST /appointment/schedule` - Schedule appointment
- `POST /appointment/updateSchedule` - Reschedule appointment

### Admissions
- `POST /admit` - Admit patient
- `POST /discharge` - Discharge patient
- `GET /getAdmissionHistory` - Get admission history

### Prescriptions & Tests
- `POST /dataentry/prescription` - Add prescription
- `POST /dataentry/testresult` - Upload test results
- `GET /dataentry/appointments/noprescription` - Get appointments without prescriptions
- `GET /dataentry/test/update` - Get tests for result entry

## 🗄️ Database Schema

### Core Tables
- **User**: System users with roles and authentication
- **Patient**: Patient information and contact details
- **Appointment**: Doctor appointments with priority and scheduling
- **Admission**: Patient admissions with room assignments
- **Room**: Hospital rooms with bed availability
- **Prescription**: Medical prescriptions
- **Test**: Medical tests with results and reports
- **Treatment**: Prescribed treatments and dosages

### Relationship Tables
- **Prescription_Test**: Links prescriptions to tests
- **Prescription_Treatment**: Links prescriptions to treatments
- **Patient_Appointment**: Links patients to appointments
- **Patient_Admission**: Links patients to admissions

## 🔒 Security Features

- **Role-based access control** with protected routes
- **Input validation** on both client and server side
- **SQL injection prevention** using parameterized queries
- **Authentication middleware** for all protected endpoints
- **Password validation** with strength requirements
- **Username validation** with format requirements

## 📧 Email Notifications

- **Important test results** automatically emailed to doctors
- **Weekly reports** sent to doctors about their patients
- **Configurable email settings** in backend

## 🚀 Deployment

### Backend Deployment
1. Set up MySQL database on your server
2. Update database connection settings
3. Install dependencies: `npm install`
4. Start server: `node index.js`

### Frontend Deployment
1. Build the project: `npm run build`
2. Deploy the `dist` folder to your web server
3. Update API endpoints in `API.js` if needed

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🐛 Known Issues

- Email functionality requires proper SMTP configuration
- Image upload for test results needs file storage setup
- Database connection strings are hardcoded (should use environment variables)

## 🔮 Future Enhancements

- [ ] Real-time notifications
- [ ] Mobile app development
- [ ] Advanced reporting and analytics
- [ ] Integration with medical devices
- [ ] Multi-language support
- [ ] Advanced search and filtering
- [ ] Backup and recovery system
- [ ] Audit logging

## 📞 Support

For support and questions, please contact the development team or create an issue in the repository.

---

**Note**: This is a comprehensive hospital management system designed for educational and demonstration purposes. For production use, additional security measures, testing, and compliance with healthcare regulations should be implemented.
