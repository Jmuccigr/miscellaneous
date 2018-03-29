---
title: local servers
date: 25 May 2017
---

## MAMP, Apache, & php

- [Use files without php extension](http://wettone.com/code/clean-urls) (= clean URIs) via Apache's `mod_rewrite` in `.htaccess`:
	1. Add regex rewrite rules according to link above:  
  
    	```
    	RewriteEngine On  
    	Options FollowSymLinks  
    	RewriteRule "^([a-z0-9_\-]+)$" "$1.php" [L]  
    	RewriteRule "^([a-z]+)/([a-z\-]+)$" "$1/$2.php" [L]  
    	```
    	
	1. Make sure that in /Applications/MAMP/conf/apache/httpd.conf, find:
	
		```
		<Directory />
		    Options Indexes FollowSymLinks
		    AllowOverride ~None~ All
		</Directory>
		```
- Change log to usual place, which will show up in console.app
	- `ErrorLog "/Users/john_muccigrosso/Library/Logs/apache_error.log"`

## Mail
- Set up postfix to use maildir system (1 file per message)
	- /etc/postfix/main.cf: `home_mailbox = Maildir/`
		- It would be nice to be able to have this in `/var/mail/<username>/`, but I didn't find an easy solution to that.
- Set up dovecot to look in that folder (installed via brew)
	- /usr/local/etc/dovecot/local.conf: `mail_location = maildir:/Users/%u/Maildir`
	- startup: `sudo brew services start dovecot`
	- Some commands (but use brew): `dovecot`, `dovecot reload`, `dovecot stop`
- Resources
    - Helpful (to a point): <https://xdeb.org/node/1607>
    - Explained mailbox types: <http://unix.stackexchange.com/questions/132654/how-to-make-postfix-create-maildir>
    - Check console for errors
        - If already running on certain PID and exits "with abnormal code 89", master.pid file may have wrong permissions so it can't be refreshed. Kill the service with the ID listed in `/usr/local/var/run/dovecot/master.pid` 
            - This often happens after upgrade.
