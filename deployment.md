
# 🚀 Deployment Documentation

## 📦 Project Stack Overview
- **Frontend:** Vue.js
- **Backend:** Laravel
- **Mobile Apps:** Java (Android), Swift (iOS)
- **Hosting/Infrastructure:** DigitalOcean Droplet (Ubuntu 22.04 LTS)

---

## ✅ Prerequisites

### Backend (Laravel)
- PHP >= 8.1
- Composer
- MySQL or MariaDB
- Nginx or Apache
- Redis (for queues - optional)

### Frontend (Vue.js)
- Node.js >= 18.x
- npm or yarn

### Mobile Development
- Android Studio (Java)
- Xcode (Swift + CocoaPods)

### Server (DigitalOcean Droplet)
- Ubuntu 22.04 LTS
- SSH access
- Git installed
- Domain with A record pointing to Droplet IP

---

## 🖥️ Deployment Steps

### 1. 🖧 Provision DigitalOcean Droplet
```bash
ssh root@your_droplet_ip
```

### 2. ⚙️ Set Up Server Environment
```bash
sudo apt update && sudo apt upgrade -y

# Install Nginx, PHP, MySQL
sudo apt install nginx mysql-server php php-mbstring php-xml php-bcmath php-curl php-mysql php-cli php-zip php-fpm unzip curl git -y

# Optional (for Laravel queues)
sudo apt install supervisor redis-server -y
```

---

## 🌐 Backend Deployment (Laravel)

### 3. ⬇️ Clone the Backend Project
```bash
git clone https://github.com/Hali-Stawi/dev-halistawi-backend.git
cd dev-halistawi-backend
```

### 4. ⚙️ Laravel Setup
```bash
cp .env.example .env
composer install
php artisan key:generate
```

### 5. 🛠️ Set File Permissions
```bash
sudo chown -R www-data:www-data .
sudo chmod -R 775 storage bootstrap/cache
```

### 6. 🔐 Configure .env
```env
APP_NAME=Halistawi
APP_ENV=production
APP_KEY=base64:...
APP_URL=https://halistawi.com

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=halistawi
DB_USERNAME=your_db_user
DB_PASSWORD=your_db_password

QUEUE_CONNECTION=database
```

### 7. 🗃️ Run Migrations and Seed
```bash
php artisan migrate --seed
```

---

### 8. 🛜 Nginx Config for Laravel
```nginx
server {
    listen 80;
    server_name halistawi.com;
    root /var/www/halistawi.com/html/public;

    index index.php index.html;
    
    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php8.3-fpm.sock;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include fastcgi_params;
    }

    location ~ /\.ht {
        deny all;
    }
}
```

### 9. 🔁 Queue Worker & Scheduler (Optional)
**Supervisor configuration example:**
```ini
[program:halistawi-queue]
process_name=%(program_name)s_%(process_num)02d
command=php /var/www/halistawi.com/html/artisan queue:work
autostart=true
autorestart=true
user=www-data
numprocs=1
redirect_stderr=true
stdout_logfile=/var/log/supervisor/halistawi-queue.log
```

---

## 🎨 Frontend Deployment (Vue.js)

### 10. ⬇️ Clone the Frontend Project
```bash
git clone https://github.com/Hali-Stawi/dev-halistawi-client.git
cd dev-halistawi-client
```

### 11. 🔧 Build Vue App
```bash
npm install
npm run build
```

### 12. 🚀 Deploy to Web Directory
```bash
sudo cp -r dist/* /var/www/clients.halistawi.com/html
```

### 13. 🌐 Nginx Config for Vue
```nginx
server {
    listen 80;
    server_name clients.halistawi.com;
    root /var/www/clients.halistawi.com/html;

    index index.html;
    location / {
        try_files $uri $uri/ /index.html;
    }
}
```

---

## 📱 Mobile App Deployment

### 14. 🔧 Android
- Open in Android Studio
- Update `BASE_URL` in Retrofit or network config
- Connect Firebase (if used)
- Build APK → `Build > Build Bundle / APK`

### 15. 🍎 iOS
- Open in Xcode
- Update `BASE_URL` and bundle settings
- Configure Apple Developer Account
- Archive and deploy via TestFlight

---

## 🔐 SSL (HTTPS) with Let’s Encrypt

```bash
sudo apt install certbot python3-certbot-nginx -y
sudo certbot --nginx -d halistawi.com -d clients.halistawi.com
```

> Auto-renewal is installed by default with Certbot.

---

## 🧪 Testing & Logs

- **Laravel Logs**: `storage/logs/laravel.log`
- **Nginx Logs**: `/var/log/nginx/access.log`, `/error.log`
- **MySQL Logs**: `/var/log/mysql/error.log`
- **Vue Build Logs**: from `npm run build`
- **Queue Logs** (Supervisor): `/var/log/supervisor/*.log`

---

## ✅ Final Deployment Checklist

| Component        | Status           |
|------------------|------------------|
| Laravel API      | ✅ Deployed       |
| Vue Frontend     | ✅ Built & Live   |
| Android App      | ✅ Compiled       |
| iOS App          | ✅ Submitted      |
| MySQL Database   | ✅ Configured     |
| Nginx            | ✅ Configured     |
| SSL (HTTPS)      | ✅ Enabled        |
| Queues & Cron    | ⚙️ Optional       |

---

## 🔄 Optional: CI/CD Suggestions

- **GitHub Actions** for automatic Laravel/Vue build and test on push.
- **Fastlane** for automating Android/iOS builds and store uploads.
- Use `.env.production` and `.env.development` separation for safer config management.

---

## 🛡️ Security Notes

- Disable root SSH login or use SSH keys.
- Regularly update OS and PHP/Node dependencies.
- Set proper permissions (`775`, `www-data`) for Laravel.
- Use fail2ban, ufw, or DigitalOcean firewall rules.
- Disable debug in production: `APP_DEBUG=false`.

---
