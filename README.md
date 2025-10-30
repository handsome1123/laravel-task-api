Insatll Xampp 

===============================================

Install Composer (Windows)

1. Go to the official site:
   👉 [https://getcomposer.org/download/](https://getcomposer.org/download/)

2. Click **"Composer-Setup.exe"** to download the Windows installer.

3. Run the installer:

   * Keep the default options.
   * When it asks for PHP path, browse to your PHP installation, e.g.:

     ```
     C:\xampp\php\php.exe
     ```
   * Let the installer **add Composer to your PATH** automatically.

4. After installation, **close and reopen PowerShell**.

---

### 🧩 Step 3. Verify installation

Run:

```bash
composer -V
```

✅ If you see something like `Composer version 2.x.x`, it’s working.

---

================================================

**If your PHP’s OpenSSL certificate file is outdated or missing**, so Composer can’t verify secure HTTPS connections. Let’s fix it step-by-step 👇

---

### 🧰 Step 1. Download a fresh certificate bundle

1. Go to:
   👉 [https://curl.se/ca/cacert.pem](https://curl.se/ca/cacert.pem)
2. Right-click → **Save As...** → save it as

   ```
   C:\xampp\php\extras\ssl\cacert.pem
   ```

   (create folders if needed)

---

### ⚙️ Step 2. Update PHP’s configuration

1. Open this file:

   ```
   C:\xampp\php\php.ini
   ```
2. Search for:

   ```
   ;curl.cainfo=
   ;openssl.cafile=
   ```
3. Remove the semicolons (`;`) and set the new path:

   ```ini
   curl.cainfo="C:\xampp\php\extras\ssl\cacert.pem"
   openssl.cafile="C:\xampp\php\extras\ssl\cacert.pem"
   ```
4. Save the file.

---

### 🔄 Step 3. Restart everything

* Close PowerShell or Command Prompt.
* Restart XAMPP’s **Apache** (and MySQL if running).
* Reopen PowerShell.

---

### 🚀 Step 4. Try again

Run:

```bash
composer -V
```

If it shows a version number → you’re good to go!


### 5️⃣ Tell Composer explicitly (optional but recommended)

Run these commands to make sure Composer always uses that file:

```bash
setx COMPOSER_CAFILE "C:\xampp\php\extras\ssl\cacert.pem"
setx SSL_CERT_FILE "C:\xampp\php\extras\ssl\cacert.pem"
```

Then **close and reopen PowerShell again**.

---

### 6️⃣ Test again

```bash
composer diagnose
```

✅ You should now see:

```
Checking https connectivity to packagist: OK
Checking github.com rate limit: OK
```

---

### 🚀 Then you can safely run:

```bash
composer create-project laravel/laravel laravel-task-api
```

---

If it **still fails**, please run this:

```bash
php -r "echo ini_get('curl.cainfo');"
```














<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

## About Laravel

Laravel is a web application framework with expressive, elegant syntax. We believe development must be an enjoyable and creative experience to be truly fulfilling. Laravel takes the pain out of development by easing common tasks used in many web projects, such as:

- [Simple, fast routing engine](https://laravel.com/docs/routing).
- [Powerful dependency injection container](https://laravel.com/docs/container).
- Multiple back-ends for [session](https://laravel.com/docs/session) and [cache](https://laravel.com/docs/cache) storage.
- Expressive, intuitive [database ORM](https://laravel.com/docs/eloquent).
- Database agnostic [schema migrations](https://laravel.com/docs/migrations).
- [Robust background job processing](https://laravel.com/docs/queues).
- [Real-time event broadcasting](https://laravel.com/docs/broadcasting).

Laravel is accessible, powerful, and provides tools required for large, robust applications.

## Learning Laravel

Laravel has the most extensive and thorough [documentation](https://laravel.com/docs) and video tutorial library of all modern web application frameworks, making it a breeze to get started with the framework.

You may also try the [Laravel Bootcamp](https://bootcamp.laravel.com), where you will be guided through building a modern Laravel application from scratch.

If you don't feel like reading, [Laracasts](https://laracasts.com) can help. Laracasts contains thousands of video tutorials on a range of topics including Laravel, modern PHP, unit testing, and JavaScript. Boost your skills by digging into our comprehensive video library.

## Laravel Sponsors

We would like to extend our thanks to the following sponsors for funding Laravel development. If you are interested in becoming a sponsor, please visit the [Laravel Partners program](https://partners.laravel.com).

### Premium Partners

- **[Vehikl](https://vehikl.com/)**
- **[Tighten Co.](https://tighten.co)**
- **[WebReinvent](https://webreinvent.com/)**
- **[Kirschbaum Development Group](https://kirschbaumdevelopment.com)**
- **[64 Robots](https://64robots.com)**
- **[Curotec](https://www.curotec.com/services/technologies/laravel/)**
- **[Cyber-Duck](https://cyber-duck.co.uk)**
- **[DevSquad](https://devsquad.com/hire-laravel-developers)**
- **[Jump24](https://jump24.co.uk)**
- **[Redberry](https://redberry.international/laravel/)**
- **[Active Logic](https://activelogic.com)**
- **[byte5](https://byte5.de)**
- **[OP.GG](https://op.gg)**

## Contributing

Thank you for considering contributing to the Laravel framework! The contribution guide can be found in the [Laravel documentation](https://laravel.com/docs/contributions).

## Code of Conduct

In order to ensure that the Laravel community is welcoming to all, please review and abide by the [Code of Conduct](https://laravel.com/docs/contributions#code-of-conduct).

## Security Vulnerabilities

If you discover a security vulnerability within Laravel, please send an e-mail to Taylor Otwell via [taylor@laravel.com](mailto:taylor@laravel.com). All security vulnerabilities will be promptly addressed.

## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
 