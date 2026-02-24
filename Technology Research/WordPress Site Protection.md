# General Practices

## DONT's

- Don't install random plugins/themes
- Don't copy and paste code from un-trusted sources
## DO's

- **User Protection & Authentication**
	- Make sure your user isn't named Admin and disable listing usernames
	- Change your WordPress Login Page: Set up a custom login url, instead of default wp-admin
	- Strengthen passwords: Use a combination of upper and lowercase letters, numbers, and special characters, and avoid using common words or phrases
	- Limit login attempts: Use a plugin or security tool to limit the number of login attempts to prevent brute force attacks
	- Block IP ranges from countries you have no intention of doing business with (e.g. China, Iran, etc.) through your the hosting service - this will significantly reduce the amount of probing that occurs
	- Limit user permissions: Only give users the permissions they need to perform their tasks, and avoid giving admin access to anyone who doesn't need it
	- Enable two-factor authentication (2FA) with a plugin like **WP 2FA** for an extra layer on logins
	- Limit the ways a user can interact with the site (e.g. limit files for uploading, disable comments, etc.)
- **Routine Checks**
	- Stay on top of WordPress, Plugin and Theme updates: updates often contain security patches that address vulnerabilities and protect against known attacks
	- Disable the built in theme file editor, as anyone who breaks in will be able to insert malicious code into your website. Alternatively, uninstall after every use.
	- Backup your site regularly: Backing up your site regularly ensures that you have a copy of your site in case of a security breach or other issue
	- Disable PHP warnings and notices on your live server, as well as resolve any runtime browser errors, as they can reveal code vulnerabilities to an attacker.
- **Security Plugins**
	- Use a plugin like [Wordfence](https://www.wordfence.com/), [MalCare](https://www.malcare.com/), or [Sucuri](https://en-ca.wordpress.org/plugins/sucuri-scanner/) for proactive malware scanning and one-click cleanup if something slips through
	- [Solid Security](https://en-ca.wordpress.org/plugins/better-wp-security/) has a great list of security measures to check. You can use the plugin just to check and give suggestions, and then remove the plugin and apply the changes manually if you don’t want to use the plugin.
- **Hosting and Server-Level Security** 
	- Disable directory browsing: This prevents attackers from seeing the files and folders on your server.
	- Consider a Web Application Firewall (WAF): This acts as an additional layer of security at the server level, filtering out malicious traffic before it reaches your website.
- **Advanced Configurations**
	- Disable file editing within the WordPress dashboard by adding `define('DISALLOW_FILE_EDIT', true);` to your `wp-config.php`. By default, WordPress allows you to edit theme and plugin files from within the admin panel. Disabling this feature can help prevent malicious code from being injected into your site.
	- Make sure SSL is forced across the site (FORCE_SSL_ADMIN in wp-config) to encrypt data transmitted between your site and visitors, protecting sensitive information from being intercepted
	-  VPS and dedicated servers: use [fail2ban](https://github.com/fail2ban/fail2ban); a highly recommended security measure to protect against brute-force attacks on SSH, FTP, and web services; integrates seamlessly with Hetzner’s standard Linux distributions (Ubuntu, Debian, etc.) by managing local firewall rules (iptables or UFW) to block malicious IPs.
	- Change your MySQL database table prefix to something other than wp_ to make it harder for sql injection attacks or malicious scripts to do anything to your db.
	- Restrict access to your `wp-admin` directory via IP whitelisting
	- Disable [XML-RPC](https://www.hostinger.com/tutorials/xmlrpc-wordpress) if not in use, as it's a common attack vector
	- Configure security headers (like X-Content-Type-Options or Content-Security-Policy) in .htaccess or server config to block XSS and other threats

# WordPress Backup Practices

* **Via Plugins**
	* [UpdraftPlus](https://teamupdraft.com/), [WPTimeCapsule](https://wptimecapsule.com/), or [BackWPUp](https://en-ca.wordpress.org/plugins/backwpup/) for automatic regular file and database backups to external services (such as **Dropbox**, **S3**, **FTP**, **Google Drive**, **OneDrive** and more)
	* Manual backup and migration with [All-in-One WP Migration and Backup](https://en-ca.wordpress.org/plugins/all-in-one-wp-migration/); Backup cloud storage options: [pCloud](https://www.pcloud.com/), [DreamObjects](https://www.dreamhost.com/cloud/storage/)
* Via a Custom Setup
	* Automated backups via mysqldump and rsync
	* [Rclone automation scripts](https://github.com/bomsn/rclone-automated-backups-for-wordpress)

# Resources

- https://github.com/password123456/setup-wordpress-with-security-best-practice
- https://developer.wordpress.org/advanced-administration/security/hardening/