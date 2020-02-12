## Student Activity File - Permissions

During the last activity, we cleaned up the system groups and users and removed all the malicious users from the system. We also removed users from the sudo group and found a rouge group that we removed.

Your senior system administrator now wants you to lock down a few choice files and directories. Recall that during our scavenger hunt yesterday, we talked about the sensitive files on the system that contain all the users (`/etc/passwd`), the passwords (`/etc/shadow`) and the groups (`/etc/group`).

This activity will give you an opportunity to practice inspecting and setting file permissions on these sensitive files. Use the checklist provided by your senior administrator in the Instructions section for specifics on which files you'll inspect and modify permissions on.

You'll use the same lab environment you used in the previous exercises:
- Username: `admin` Password: `cybersecurity`

### Instructions

**Checklist**

Your Senior Administrator has asked you to complete the following:

- Set permissions on /etc/shadow to allow only `root` read and write access.

- Set permissions on /etc/gshadow to allow only `root` read and write access.

- Set permissions on /etc/group to allow `root` read and write access, and allow everyone else `read` access only.

- Set permissions on /etc/passwd to allow `root` read and write access, and allow everyone else `read` access only.

- Verify all accounts have passwords.

- Recall that if any user has the UID of `0`, the system thinks they are `root`. Verify that no users have UID of '0' besides root. If you find one that does, change it's UID to any value > 1000.

- Provide a list of each permissions change you have made in a text file in your research directory.

Attempt to complete this list on your own, and if you need help, refer to the walkthrough below.

---

### Walkthrough

- Start by inspecting the file permissions on each of the files listed, and determine if they are already set correctly or if you need to change the permissions.

- You can use [this Resource](https://askubuntu.com/questions/518259/understanding-chmod-symbolic-notation-and-use-of-octal) if you get stuck.

- Verify that all accounts have passwords. If you get stuck, google how to determine if an account has a password on a Linux system.

- Verify that only the root user has a UID of 0. 
  
  - Hint: This is similar to verifying the password.

- Write all of your findings into a file using `nano`. Keep that file in your research directory.