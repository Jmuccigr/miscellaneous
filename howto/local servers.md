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
		    AllowOverride ~~None~~ All
		</Directory>
		```

- Change log to usual place, which will show up in console.app
	- `ErrorLog "/Users/john_muccigrosso/Library/Logs/apache_error.log"`

- Icons
    - MAMP will use its own /icons directory unless the following line is commented out in the http.conf file:

        ```
        #       Alias /icons/ "/Applications/MAMP/Library/icons/"
        ```
    1. Upgrades to WordPress may wipe out the rewrite rules on the server.

- Set up MAMP to handle https via instructions [here](https://davescripts.com/set-up-ssl-on-a-virtual-host-on-mamp).
    - cert password: same as computer login
    - challenge password: M..........2 (deleted as part of the set-up, I believe)

- Set `output_buffering` to `Off` (the default) in php.ini or the `Clear` button won't result in a map update


## Local Mail with Dovecot & postfix

- Set up postfix to use maildir system (1 file per message)
	- /etc/postfix/main.cf: `home_mailbox = Maildir/`
		- It would be nice to be able to have this in `/var/mail/<username>/`, but I didn't find an easy solution to that.
		- This can get overwritten by system updates. Check if local mail isn't showing up in Mail.app.
- Stop postfix from respawning every 10 seconds (in launchd.log)
    - /etc/postfix/main.cf: `inet_interfaces = 127.0.0.1`
    - See <https://serverfault.com/questions/646284/postfix-not-working-on-macos-yosemite>
- Set up dovecot to look in that folder (installed via brew)
	- /usr/local/etc/dovecot/local.conf: `mail_location = maildir:/Users/%u/Maildir`
	- /opt/homebrew/etc/dovecot/local.conf in the new version 2.4
	- startup: `sudo brew services start dovecot`
	- Some commands (but use brew): `dovecot`, `dovecot reload`, `dovecot stop`
- Resources
    - Helpful (to a point): <https://xdeb.org/node/1607>
    - Explained mailbox types: <http://unix.stackexchange.com/questions/132654/how-to-make-postfix-create-maildir>
    - Check Console for errors
        - system.log: If already running on certain PID and exits "with abnormal code 89", master.pid file may have wrong permissions so it can't be refreshed. Kill the service with the ID listed in `/usr/local/var/run/dovecot/master.pid` 
            - This often happens after upgrade.
    - run `sudo dovecot -F` to get errors, if all else fails
- Set dovecot to delete trashed mail
    - <https://notes.sagredo.eu/en/qmail-notes-185/expunging-expired-junk-and-trash-emails-with-dovecot-124.html>
    - Add this to the 15-maildirs.conf file under `mailbox Trash {`
    
        ```
        auto = subscribe
        autoexpunge = 60d
        ```
