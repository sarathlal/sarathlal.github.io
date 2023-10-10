---
title: Reset admin user password using SQL query - Magento
layout: post
tags:
  - Magento 2
  - Magento 1
---

The best method to reset admin user password is clicking forget password link on the login page. If so, Magento will ask for admin email & then one reset password link will send to that email address.

But in some situations like emails are not working due to server configuration etc, we have to look alternative options for quick fix.

## Reset password using SQL query

In Magento 1 and Magento 2, there is different encryption methods are used to save password.

### Magento 1

	UPDATE admin_user SET password = CONCAT(MD5('xxxxxxxxNewPassword'), ':xxxxxxxx') WHERE username = 'admin';

### Magento 2

	UPDATE admin_user SET password = CONCAT(SHA2('xxxxxxxxNewPassword', 256), ':xxxxxxxx:1') WHERE username = 'admin';


The `xxxxxxxx` character sequence is cryptographic salt. It can be anything (and any length), but make sure you use the same value in both parts of the SQL statement.

Also you want to update the user name in your query. It may be different.

If our Magento installation uses table prefixes, make sure we add it to the table name in our SQL command.

**Example**

If our table prefix is `n7g_`,

	UPDATE n7g_admin_user SET password = CONCAT(SHA2('xxxxxxxxNewPassword', 256), ':xxxxxxxx:1') WHERE username = 'admin';

