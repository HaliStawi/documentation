
# Halistawi Application

Halistawi is a comprehensive health application that integrates multiple platforms to deliver a seamless healthcare management experience. It supports web (Vue.js + Laravel), Android (Java), and iOS platforms, hosted on DigitalOcean.

---

## 📦 Project Structure

- **Web Frontend**: Vue.js
- **Backend API**: Laravel (PHP)
- **Android App**: Java
- **iOS App**: Native (Swift)
- **Hosting**: DigitalOcean (Droplets, Managed Databases, etc.)
- **Database**: MySQL

---

## 🚀 Deployment Documentation

Detailed deployment instructions for all platforms are available here:

📄 [Deployment Guide](https://github.com/HaliStawi/documentation/blob/main/deployment.md)

This includes:
- Environment setup
- Web, API, Android, and iOS deployment
- Cron jobs and queues
- SSL configuration
- Domain setup

---

## 📂 Repositories

| Platform     | Repository URL |
|--------------|----------------|
| Web Frontend | [Vue.js Repo](https://github.com/HaliStawi/frontend) |
| Backend API  | [Laravel Repo](https://github.com/HaliStawi/backend) |
| Android App  | [Android Repo](https://github.com/HaliStawi/android) |
| iOS App      | [iOS Repo](https://github.com/HaliStawi/ios) |
| Documentation | [Docs Repo](https://github.com/HaliStawi/documentation) |

---

## ⚙️ Technologies Used

- **Frontend**: Vue.js 3, Vuex, Axios
- **Backend**: Laravel 10, Sanctum for auth, MySQL
- **Mobile**: Java (Android), Swift (iOS)
- **DevOps**: Nginx, PHP-FPM, Supervisor, GitHub Actions (CI/CD)
- **Others**: Docker (optional), Redis (for queues), S3 (for storage)

---

## 🔐 Security & Roles

- JWT & token-based authentication
- Role-based access (Admin, Super Admin, User, etc.)
- OTP verification

---

## 🧪 Testing

- Postman collection available for backend API
- Unit and Feature tests in Laravel using PHPUnit
- Manual and device testing for Android & iOS

---

## 🛠 Post-Deployment Checklist

Refer to: [Post Deployment Checklist](./post_deployment_checklist.md)

Includes:
- SSL & Domain verification
- Background workers validation
- Queue/cron setup
- Error monitoring

## 👥 Contributors

- [John Kunyuga] – Project Lead

---

## 📫 Contact

For issues, reach out via GitHub Issues or contact [support@halistawi.com].

## 📜 License

MIT License. See `LICENSE` file for details.

---

© 2025 Halistawi Health Systems. All rights reserved.
