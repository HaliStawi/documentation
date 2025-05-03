# Halistawi Application

Halistawi is a multi-platform application built to serve users across web and mobile platforms, including Android and iOS. The application is powered by a Laravel backend and Vue.js frontend, with native mobile applications developed in Java (Android) and Swift (iOS).

---

## 📦 Project Structure

| Component     | Tech Stack          | Repository Link |
|---------------|---------------------|------------------|
| Backend API   | Laravel (PHP)       | [halistawi-backend](https://github.com/HaliStawi/halistawi-backend) |
| Web Frontend  | Vue.js              | [halistawi-frontend](https://github.com/HaliStawi/halistawi-frontend) |
| Android App   | Java (Android SDK)  | [halistawi-android](https://github.com/HaliStawi/halistawi-android) |
| iOS App       | Swift (Xcode)       | [halistawi-ios](https://github.com/HaliStawi/halistawi-ios) |
| Documentation | Markdown            | [documentation](https://github.com/HaliStawi/documentation) |

---

## 🚀 Deployment

Deployment instructions for all components (Vue.js, Laravel, Android, iOS) are available in the [Deployment Guide](https://github.com/HaliStawi/documentation/blob/main/deployment.md).

Please refer to this document for step-by-step instructions on:

- Setting up servers (DigitalOcean)
- Configuring environment files (`.env`)
- Running migrations and seeders
- Building and serving frontend
- Building Android and iOS apps

---

## 🧰 Prerequisites

### Backend (Laravel)
- PHP ≥ 8.1
- Composer
- MySQL / MariaDB
- Laravel CLI

### Frontend (Vue.js)
- Node.js ≥ 16
- npm / yarn
- Vue CLI

### Android
- Android Studio
- Java SDK
- Android SDK / Emulator or Device

### iOS
- macOS with Xcode
- Apple Developer Account
- iPhone or Simulator

---

## ⚙️ Setup Instructions

### Backend (Laravel)
```bash
git clone https://github.com/HaliStawi/halistawi-backend.git
cd halistawi-backend
cp .env.example .env
composer install
php artisan key:generate
php artisan migrate --seed
php artisan serve
```

### Frontend (Vue.js)
```bash
git clone https://github.com/HaliStawi/halistawi-frontend.git
cd halistawi-frontend
cp .env.example .env
npm install
npm run dev
```

### Android
Open the project in Android Studio and sync Gradle files. Then build and run the app on a device or emulator.

### iOS
Open the project in Xcode, configure signing, and run it on a simulator or physical device.

---

## 🛠 Environment Configuration

Each project contains a `.env.example` file. Copy it to `.env` and configure:

- API endpoints
- Database credentials
- Mail and storage settings
- Firebase or notification services (if any)

---

## 📄 Documentation

Detailed documentation and deployment instructions are available here:  
📘 **[Halistawi Deployment Documentation](https://github.com/HaliStawi/documentation/blob/main/deployment.md)**

This includes:
- Server setup (Ubuntu, Nginx)
- SSL with Let's Encrypt
- Laravel queue and scheduler configuration
- Frontend build and Nginx setup
- Mobile build and release process

---

## 👥 Contributors

- [John Kunyuga] – Project Lead

---

## 📫 Contact

For issues, reach out via GitHub Issues or contact [support@halistawi.com].
