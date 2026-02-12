
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

1. Keep WordPress, themes, and plugins up to date: Updates often contain security patches that address vulnerabilities and protect against known attacks.
2. Use strong passwords: Use a combination of upper and lowercase letters, numbers, and special characters, and avoid using common words or phrases.
3. Use two-factor authentication: Two-factor authentication adds an extra layer of security by requiring a second form of authentication, such as a code sent to your phone or email.
4. Limit login attempts: Use a plugin or security tool to limit the number of login attempts to prevent brute force attacks.
5. Use a security plugin: There are many security plugins available for WordPress, such as Wordfence or Sucuri, that can help protect your site from attacks and malware.
6. Disable file editing: By default, WordPress allows you to edit theme and plugin files from within the admin panel. Disabling this feature can help prevent malicious code from being injected into your site.
7. Use HTTPS and SSL: Using HTTPS and SSL encrypts data transmitted between your site and visitors, protecting sensitive information from being intercepted.
8. Limit user permissions: Only give users the permissions they need to perform their tasks, and avoid giving admin access to anyone who doesn't need it.
9. Backup your site regularly: Backing up your site regularly ensures that you have a copy of your site in case of a security breach or other issue.
10. Use a reputable hosting provider: Choose a hosting provider that prioritizes security, offers regular backups, and has a good reputation for keeping sites secure.

## Hosting and Server-Level Security

- **Choose a reputable and secure web hosting provider:** Look for providers who offer features like firewalls, DDoS protection, regular backups, and intrusion detection systems.
- **Disable directory browsing:** This prevents attackers from seeing the files and folders on your server.
- **Consider a Web Application Firewall (WAF):** This acts as an additional layer of security at the server level, filtering out malicious traffic before it reaches your website.
## Backup Your Site Regularly

- **Recommendation:** Implement a reliable backup solution with **UpdraftPlus** or **BackupBuddy**. Store backups in a remote location like Google Drive or Dropbox.
- **Why it matters:** Regular backups ensure that you can quickly recover your site in the event of an attack or failure.
## Harden WordPress with Advanced Configurations

- **Recommendation:**
    - Disable file editing within the WordPress dashboard by adding `define('DISALLOW_FILE_EDIT', true);` to your `wp-config.php`.
    - Restrict access to your `wp-admin` directory via IP whitelisting.
    - Disable XML-RPC if not in use, as it's a common attack vector.
- **Why it matters:** Hardening WordPress reduces the potential entry points for attackers.

## WordPress Backups

* I also make sure to back everything up regularly, so I set up regular offsite backups to my pCloud with the All-in-One WP Migration plugin and rely on daily backups from [my hosting](https://eu.siteground.com/). For some sites, I also use SaaS BlogVault.
* https://www.reddit.com/r/Wordpress/comments/175i070/best_strategies_for_backing_up_your_wordpress/
* https://www.reddit.com/r/Wordpress/comments/1jex2bh/backup_of_wordpress_site/
* https://www.reddit.com/r/Wordpress/comments/1busy5p/what_are_the_best_practices_for_offline_backup_of/
* https://www.reddit.com/r/Wordpress/comments/14ddzut/whats_the_best_security_measure_to_avoid_hacking/

# Resources

- https://github.com/password123456/setup-wordpress-with-security-best-practice
- https://www.cloudflare.com/en-ca/sase/products/access/