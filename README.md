# Savli Industrial Services website package

This package upgrades the supplied static website with an accessible enquiry form, PHP backend, MySQL storage, and a password-protected admin page.

## Included
- `index.php` — website and enquiry form (responsive layout, keyboard focus styling, skip link, labelled controls)
- `submit-enquiry.php` — validates and stores enquiries with PDO prepared statements and CSRF/honeypot checks
- `admin.php` — protected dashboard for viewing the latest 500 enquiries
- `config.php` — database credentials and admin password hash (must be configured before deployment)
- `setup.sql` — database table definition
- `.htaccess` — disables directory listing and blocks direct web access to configuration/setup files on Apache hosting
- `savli_industrial_services_website.html` — HTML preview only; the PHP `index.php` is the deployable homepage

## Deploy on PHP + MySQL hosting
1. Create a MySQL database and database user in your hosting control panel. Grant that user access to the database.
2. Open phpMyAdmin, select the new database, and import `setup.sql`.
3. Edit `config.php` with the exact database host, database name, username and password shown by your host.
4. Generate an admin password hash on a PHP machine/terminal:
   `php -r "echo password_hash('CHOOSE-A-STRONG-PASSWORD', PASSWORD_DEFAULT), PHP_EOL;"`
   Replace `REPLACE_WITH_PASSWORD_HASH` in `config.php` with the resulting hash. Do not use the example phrase as your real password.
5. Replace both `+919999999999` placeholders in `index.php` with the business's real international-format number (digits only after the plus). Update the WhatsApp URL too. Update any business details that are not accurate.
6. Upload the **contents** of this package to the hosting document root (usually `public_html`). Ensure `index.php` is in that root. Use PHP 8.1+ and enable PDO MySQL.
7. Enable the hosting provider's free SSL certificate, then test `https://yourdomain.com`, submit a test enquiry, and sign in at `https://yourdomain.com/admin.php`.
8. Delete the standalone `.html` preview if you do not need it. Do not upload this package to static-only hosting such as GitHub Pages: PHP backend scripts require PHP hosting.

## Important
- The backend will not store enquiries until the database and `config.php` are correctly configured.
- This package does not send email notifications. Check the admin dashboard regularly; email notifications can be added after you provide the business email and SMTP settings.
- Use a strong unique admin password, keep `config.php` private, keep hosting/PHP updated, and back up the database.
- Verify all business claims, GST details, photos, contact details, and service descriptions before launch.
- The contact links still contain a placeholder number until you replace it.
