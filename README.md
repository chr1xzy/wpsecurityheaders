# WordPress Security Headers

Security headers help prevent your site from hacking. Copy and paste the below code into the wordpress theme functions.php. It will prevent cross scripting attacks, clickjacking, sniffing, etc. More details are listed on the link


https://securityheaders.com/?q=DOMAINNAME.COM&hide=on&followRedirects=on


functions.php will be located in your theme directory

/wp-content/themes/[themename]/


functions.php can also be accessed through wpadmin

Appearance / Editor / [pick theme in dropdown - top right] / functions.php


Copy and paste the following (can stick it at the bottom of the functions.php file)

```
// Security headers begin

add_action('send_headers', function(){
// Enforce the use of HTTPS
header("Strict-Transport-Security: max-age=31536000; includeSubDomains");
// Cross Site Scripting (XSS) attacks
// header ("Content-Security-Policy: script-src 'self'");
header ("Content-Security-Policy: form-action https:; upgrade-insecure-requests");
// Prevent Clickjacking
header("X-Frame-Options: SAMEORIGIN");
// Block Access If XSS Attack Is Suspected
header("X-XSS-Protection: 1; mode=block");
// Prevent MIME-Type Sniffing
header("X-Content-Type-Options: nosniff");
// Referrer Policy
header("Referrer-Policy: no-referrer-when-downgrade");
}, 1);

// Security headers end
```

You can then reload the security headers link above and see if the changes took.

If for some reason the website gives you an error (shouldn't), you can ftp or use your webhost control panel to re-edit the file and remove the code. Funky blank spaces added from copy and pasting rarely occur. 
