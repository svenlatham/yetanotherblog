---
layout: post
title: "Hack Attempt"
date: 2006-04-21 11:28:05 +0000
permalink: /2006/04/21/hack-attempt/
author: "sven"
categories: ["server", "sysadmin", "hacking"]
---

Just noticed an attempt to find unprotected admin/phpMyAdmin interfaces on one of our servers. The script appears to try common URLs (below) for PMA, presumably in the hope that the admin has left it wide open. As ever, keep those doors locked and secured!  
/phpmyadmin/main.php  
/PMA/main.php  
/mysql/main.php  
/admin/main.php  
/db/main.php  
/dbadmin/main.php  
/web/phpMyAdmin/main.php  
/admin/pma/main.php  
/admin/phpmyadmin/main.php  
/admin/mysql/main.php  
/phpmyadmin2/main.php  
/mysqladmin/main.php  
/mysql-admin/main.php  
/main.php  
/phpMyAdmin-2.5.6/main.php  
/phpMyAdmin-2.5.4/main.php  
/phpMyAdmin-2.5.1/main.php  
/phpMyAdmin-2.2.3/main.php  
/phpMyAdmin-2.2.6/main.php  
/myadmin/main.php  
/phpMyAdmin-2.6.0/main.php  
/phpMyAdmin-2.6.0-pl1/main.php  
/phpMyAdmin-2.6.3-pl1/main.php  
/phpMyAdmin-2.6.3/main.php  
/phpMyAdmin-2.6.3-rc1/main.php  
/phpMyAdmin-2.6.2-rc1/main.php
