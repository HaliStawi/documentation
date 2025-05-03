
# Halistawi Application - Post Deployment Checklist

This checklist helps ensure all aspects of the Halistawi application (Laravel backend, Vue.js frontend, Android and iOS apps) are correctly deployed and functioning on the DigitalOcean server.

---

## ✅ Laravel Backend
- [ ] `.env` file is properly configured with production values
- [ ] Run `php artisan config:cache`, `route:cache`, `view:cache`
- [ ] Run `php artisan migrate --force`
- [ ] File permissions for `storage/` and `bootstrap/cache/` are correct
- [ ] Laravel queue worker is running (if used)
- [ ] Log files (`storage/logs/`) are writable
- [ ] SSL certificate is installed and valid
- [ ] API is responding at `/api/status` or similar endpoint

## ✅ Vue.js Frontend
- [ ] Production build completed using `npm run build`
- [ ] Static files deployed to web server (e.g., Nginx or Apache root)
- [ ] Environment variables in `.env.production` are correct
- [ ] CDN or cache-busting (if enabled) is working
- [ ] CORS settings allow API calls to Laravel backend

## ✅ Android App
- [ ] Release APK built and signed
- [ ] Version code and version name updated
- [ ] Uploaded to Google Play Console (Production or Internal Testing)
- [ ] Firebase Crashlytics, Analytics configured
- [ ] API URL in `build.gradle` or `.env` points to production

## ✅ iOS App
- [ ] Archive built using Xcode for Release
- [ ] All required provisioning profiles and certificates are valid
- [ ] Uploaded via Transporter or Xcode to App Store Connect
- [ ] Firebase Crashlytics, Analytics configured
- [ ] API URL correctly set in `Info.plist` or environment manager

## ✅ Server (DigitalOcean)
- [ ] Nginx/Apache running and pointing to correct directories
- [ ] Firewall (ufw) configured (only HTTP/HTTPS, SSH open)
- [ ] Fail2ban or intrusion prevention enabled
- [ ] Swap file configured for memory management
- [ ] Auto-renewal of SSL certificates (e.g., Certbot cron job) verified

---

Ensure each item above is reviewed and completed before considering deployment finalized.
