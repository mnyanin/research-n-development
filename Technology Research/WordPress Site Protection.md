
# General Practices

- Don't install random plugins/themes
- Don't copy and paste code from un-trusted sources
- Use a strong password and make sure your user isn't named Admin
- Disable [xmlrpc.php](https://www.hostinger.com/tutorials/xmlrpc-wordpress)
- Change your WordPress Login Page
- Stay on top of WordPress, Plugin and Theme updates
- Use WordFence to monitor potential vulnerabilities
- If your hosting provider allows it, block IP ranges from countries you have no intention of doing business with (EX: China, Russia, Iran, etc.) This will significantly reduce the amount of probing that occurs
- If running a VPS or dedicated server, ensure you have fail2ban enabled
- Use a plugin like **MalCare** or **Sucuri** for proactive malware scanning and one-click cleanup if something slips through
- For HTTPS, make sure SSL is forced across your site (FORCE_SSL_ADMIN in wp-config).
- Security headers (like X-Content-Type-Options or Content-Security-Policy) in your .htaccess or server config can block XSS and other threats.
- Consider two-factor authentication (2FA) with a plugin like **WP 2FA** for an extra layer on logins.

# Resources

- https://github.com/password123456/setup-wordpress-with-security-best-practice