
# Deployment Documentation

## Project Stack Overview
- **Frontend:** Vue.js
- **Backend:** Laravel
- **Mobile Apps:** Java (Android), Swift (iOS)
- **Hosting/Infrastructure:** DigitalOcean (Droplet)

## Prerequisites

### Backend (Laravel)
- PHP >= 8.1
- Composer
- MySQL
- Nginx

### Frontend (Vue.js)
- Node.js >= 18.x
- npm / yarn

### Mobile
- Android Studio (Java)
- Xcode (Swift)

### Server (DigitalOcean)
- Ubuntu 22.04 LTS
- SSH access
- Git installed

## Deployment Steps

### 1. Provision DigitalOcean Droplet
```bash
ssh root@your_droplet_ip
```

### 2. Set Up Environment
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install nginx mysql-server php php-mbstring php-xml php-bcmath php-curl php-mysql unzip curl git -y
```

### 3. Clone Your Projects
```bash
git clone https://github.com/Hali-Stawi/dev-halistawi-backend.git
git clone https://github.com/Hali-Stawi/dev-halistawi-client.git
git clone https://github.com/Hali-Stawi/dev-android.git
git clone https://github.com/Hali-Stawi/dev-apple.git
```

### 4. Deploy Laravel (Backend)
```bash
cd laravel-backend
cp .env.example .env
composer install
php artisan key:generate
chown -R www-data:www-data storage bootstrap/cache
php artisan migrate --seed
```

### 5. Configure Laravel Environment
Update `.env` with:
```env
APP_NAME=YourApp
APP_ENV=production
APP_KEY=base64:...
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=your_db
DB_USERNAME=your_user
DB_PASSWORD=your_password
```

### 6. Set Up Nginx (Laravel)
```nginx
server {
    listen 80;
    server_name halistawi.com;
    root /var/www/halistawi.com/html/public;

    index index.php;
    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }
    location ~ \.php$ {
        fastcgi_pass unix:/var/run/php/php8.3-fpm.sock;
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name;
        include fastcgi_params;
    }
    location ~ /\.ht {
        deny all;
    }
}
```

### 7. Deploy Vue Frontend
```bash
cd vue-frontend
npm install
npm run build
```
Copy dist/ to Nginx directory or use it via subdomain.

### 8. Set Up Nginx (Vue.js)
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

### 9. Android / iOS Mobile Build
- Connect Android Studio/Xcode to your Git repo
- Update `BASE_URL` to match backend API (e.g., `https://halistawi.com/api/`)
- Build APK or archive and deploy via Play Store / App Store

## Final Checklist

| Component       | Status         |
|----------------|----------------|
| Laravel API     | ✅ Deployed     |
| Vue Frontend    | ✅ Built        |
| Android         | ✅ Compiled     |
| iOS             | ✅ Uploaded     |
| SSL             | ✅ Enabled      |

