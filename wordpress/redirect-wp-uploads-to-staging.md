# Redirect wp-uploads to development/production server

If you're working on a WordPress project locally and don't want to keep syncing
the `wp-uploads` folder with the development/production server, simply add this
to the default WordPress `.htaccess`:

    <IfModule mod_rewrite.c>
    RewriteEngine On

    # Redirect upload requests to staging site
    RewriteRule ^wp-content/uploads/(.*)$ http://staging.domain.com/wp-content/uploads/$1 [L,R=301]

    # Default WP redirects follow...
    RewriteBase /
    RewriteRule ^index\.php$ - [L]
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteRule . /index.php [L]
    </IfModule>

Your local site will now use the images on the development/production server!
