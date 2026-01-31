# Carepulse - Healthcare Management System

Carepulse is a modern Healthcare Management System (HMS) designed to streamline healthcare operations by digitizing patient care workflows. The system enables efficient patient registration, secure medical record management, appointment scheduling, and administrative oversight. Built with Next.js and Appwrite, Carepulse provides a scalable, cloud-based solution for healthcare providers.

## Project Overview

Carepulse enables healthcare providers to:
- Register and manage patient profiles with comprehensive medical information
- Schedule, track, and manage appointments with multiple status states
- Store and manage patient identification documents securely
- Monitor appointment statistics and patient data through an admin dashboard
- Maintain secure patient records with proper consent management

## Core Functionalities

### 1. Patient Registration & Management
- **User Creation**: Create Appwrite user accounts with email, phone, and name
- **Patient Profile Registration**: Comprehensive patient registration form including:
  - Personal information (name, email, phone, birth date, gender, address, occupation)
  - Emergency contact details
  - Primary physician selection from available doctors
  - Insurance information (provider and policy number)
  - Medical history (allergies, current medications, family history, past medical history)
  - Identification document upload with multiple document type support
  - Privacy and consent management (treatment, disclosure, privacy consents)
- **Patient Profile Retrieval**: Fetch and display patient information by user ID
- **Document Management**: Secure storage and retrieval of patient identification documents

### 2. Appointment Management
- **Appointment Creation**: Create new appointments with:
  - Primary physician selection
  - Scheduled date and time
  - Appointment reason
  - Optional notes
- **Appointment Scheduling**: Schedule appointments with flexible date/time selection
- **Appointment Cancellation**: Cancel appointments with cancellation reason tracking
- **Appointment Status Tracking**: Three status states:
  - `pending` - Awaiting confirmation
  - `scheduled` - Confirmed and scheduled
  - `cancelled` - Cancelled appointments
- **Appointment Updates**: Update existing appointments with new information

### 3. Admin Dashboard
- **Statistics Overview**: Real-time appointment statistics including:
  - Scheduled appointments count
  - Pending appointments count
  - Cancelled appointments count
- **Appointment List**: Data table displaying all recent appointments with:
  - Patient information
  - Doctor assignments
  - Appointment dates and times
  - Status indicators
  - Action capabilities
- **Admin Access**: Secure admin access via passkey authentication

### 4. User Interface & Experience
- **Responsive Design**: Modern, responsive UI built with Tailwind CSS
- **Form Validation**: Comprehensive client and server-side validation using Zod
- **Phone Number Validation**: International phone number format validation
- **Date Picker**: User-friendly date selection for appointments and birth dates
- **File Upload**: Drag-and-drop file upload for identification documents
- **Loading States**: Visual feedback during form submissions and data fetching
- **Error Handling**: Comprehensive error handling with Sentry integration

### 5. Security & Compliance
- **User Authentication**: Appwrite-based user management and authentication
- **Document Storage**: Secure file storage using Appwrite Storage
- **Privacy Consents**: Required consent management for:
  - Treatment consent
  - Disclosure consent
  - Privacy consent
- **Data Validation**: Server-side validation for all user inputs
- **Error Monitoring**: Sentry integration for production error tracking

## Technology Stack

### Frontend
- **Next.js 15.4.5** - React framework with App Router
- **React 19.1.0** - UI library
- **TypeScript 5** - Type-safe development
- **Tailwind CSS 4.1.11** - Utility-first CSS framework
- **Radix UI** - Accessible component primitives:
  - Alert Dialog
  - Checkbox
  - Label
  - Popover
  - Radio Group
  - Select
  - Separator
  - Slot
- **Shadcn/ui** - Component library built on Radix UI
- **Lucide React** - Icon library

### Backend & Services
- **Appwrite** - Backend-as-a-Service platform providing:
  - Database (NoSQL document database)
  - Storage (File storage for documents)
  - Users (User management and authentication)
  - Messaging (Communication services)

### Form Management & Validation
- **React Hook Form 7.62.0** - Form state management
- **Zod 4.0.15** - Schema validation
- **@hookform/resolvers 5.2.1** - Zod integration for React Hook Form

### Additional Libraries
- **react-phone-number-input** - International phone number input
- **libphonenumber-js** - Phone number parsing and validation
- **react-datepicker** - Date selection component
- **react-dropzone** - File upload with drag-and-drop
- **@tanstack/react-table** - Data table component for admin dashboard
- **next-themes** - Theme management (dark/light mode support)
- **cmdk** - Command menu component
- **input-otp** - OTP input component

### Monitoring & Observability
- **Sentry** - Error tracking and performance monitoring
- **OpenTelemetry** - Distributed tracing support

### Development Tools
- **ESLint** - Code linting
- **PostCSS** - CSS processing
- **TypeScript** - Static type checking

### Installation

1. **Install dependencies**
   ```bash
   npm install
   # or
   yarn install
   # or
   pnpm install
   ```

2. **Set up environment variables**

   Create a `.env.local` file in the `carepulse` directory:

   ```env
   # Appwrite Configuration
   NEXT_PUBLIC_ENDPOINT=https://cloud.appwrite.io/v1
   PROJECT_ID=your_appwrite_project_id
   API_KEY=your_appwrite_api_key
   DATABASE_ID=your_database_id
   PATIENT_COLLECTION_ID=your_patient_collection_id
   DOCTOR_COLLECTION_ID=your_doctor_collection_id
   APPOINTMENT_COLLECTION_ID=your_appointment_collection_id
   NEXT_PUBLIC_BUCKET_ID=your_storage_bucket_id

   # Application
   NODE_ENV=development
   NEXT_PUBLIC_APP_URL=http://localhost:3000

   # Optional: Sentry
   SENTRY_DSN=your_sentry_dsn
   SENTRY_ORG=your_sentry_org
   SENTRY_PROJECT=your_sentry_project
   SENTRY_AUTH_TOKEN=your_sentry_auth_token
   ```

3. **Set up Appwrite**

   - Create an Appwrite project at [appwrite.io](https://appwrite.io)
   - Create a database and the following collections:
     - **Patients Collection**: Store patient profiles
       - Fields: `userId`, `name`, `email`, `phone`, `birthDate`, `gender`, `address`, `occupation`, `emergencyContactName`, `emergencyContactNumber`, `primaryPhysician`, `insuranceProvider`, `insurancePolicyNumber`, `allergies`, `currentMedication`, `familyMedicalHistory`, `pastMedicalHistory`, `identificationType`, `identificationNumber`, `identificationDocumentId`, `identificationDocumentUrl`
     - **Doctors Collection**: Store doctor information
       - Fields: `name`, `image`, `specialization`, etc.
     - **Appointments Collection**: Store appointment data
       - Fields: `userId`, `patient`, `primaryPhysician`, `reason`, `schedule`, `status`, `note`
   - Create a Storage bucket for patient documents
   - Configure collection permissions and indexes as needed

4. **Configure Appwrite Permissions**

   - Set up appropriate read/write permissions for collections
   - Configure file upload permissions for the storage bucket
   - Set up user authentication settings

### Running the Development Server

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
```
