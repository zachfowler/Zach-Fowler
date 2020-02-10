## 4.2 Student Guide: Linux Access Controls
 
### Class Overview

In today's class, we will continue our introduction to Linux by covering one of the operating system's most important functions: access control. You wll complete a sequence of tasks that will expose you to many of the most fundamental aspects of Linux security: password strength, careful control of the `sudo` command, and file permissions. 

The skills and tools covered today will be essential for various professional roles, from systems administration to penetration testing.

### Class Objectives

By the end of class today, you will be able to:

- Audit passwords using `john`.

- Elevate privileges with `sudo` and `su`.

- Create and manage users and groups.

- Inspect and set file permissions for sensitive files on the system.

### Lab Environment

Today's lesson will use the **Ubuntu** lab environment. To access it: 

 - Log into the Azure Classroom Labs dashboard; find the card with the title **Ubuntu**.
 - Click the monitor icon in the bottom-right.
 - Select **Connect with RDP**. 
 
 The lab should already be started, so you should be able to connect immediately. 

Refer to the [lab setup instructions](https://cyberxsecurity.gitlab.io/documentation/using-classroom-labs/post/2019-01-09-first-access/) for details on setting up the RDP connection. 


### Slideshow 

The slides for today can be viewed on Google Drive here: [4.2 Slides](https://docs.google.com/presentation/d/1uqK4jfPMrZIaxAgBq1cVxJ8hxXhKAVmRp4wv3jr9F5U)

---

### 01. Welcome and Review

Welcome to the second class in on Linux. The topics of the previous class included:

- History and distributions of Linux.

- Navigating the Linux file structure using the command line.

- Managing processes with commands like `top`, `ps`, and `kill`.

- Installing packages using `apt`.

- Configuring text files using `nano`.

Today's class is focused on Linux's access control functions: passwords, file permissions, groups, and `sudo` access.

_Access control_ refers to regulating what actions users and programs are and are not allowed to take on a system.

Today will focus on users and the last day of the unit will focus on programs.

Today's class will expound on Day 1's topics by covering:

- Password auditing.

- Switching between users with `su`.

- Elevating privileges with `sudo`.

- File permissions and access controls.

- Managing users and groups.

 ### 02. Users and Passwords

Your activities throughout the week involve auditing a malfunctioning server. 

- In the previous class, we collected some important files, stopped a malicious process, and installed tools to facilitate the audit.

- Today, we will look at user access, starting with user passwords.

- In the previous class, we made a copy of `/etc/shadow`. This file contains every user's password on the system.

- The passwords are obscured with a hashing function, which means they are not stored in plain text.

#### A Brief Introduction to Hashes and Password Cracking

We have a whole unit later in the program dedicated to cryptography where will cover hashing in depth, but for now, here are a few basics:

- A hash is a cryptographic function that takes data as input and translates it to a string of different, random-looking data.

- A hash will always output the same string for the same input data. So, when a password is entered into the system, the system hashes it in the same way each time.

    - The same password will always produce the exact same hash.

- This hash is stored in the shadow file. When a user logs back in with the same password, the hash of the password they entered is compared with the hash stored for that user in the `/etc/shadow` file. If it matches, the user is logged in. If the hash doesn't match, the user is not logged in.

Note the following about password cracking tools:

- Password cracking tools do not reverse a password hash, but instead take a list of words and characters, and create a hash for each one.

- Each hash is then compared to the hash it is trying to crack, and if the two hashes match, the password has been found.

- This form of password cracking is known as a **brute force attack**.

- This is why the best passwords are long, with lots of random characters. The more random the password and the more characters it has, the longer it will take a cracking program to find a hash that matches it.

What makes a stronger password, it's complexity or it's length?

- Length and complexity work together to make a password strong.

- However, when it comes to brute force attacks, password length has more impact on the time it takes to crack it.

Whatis the current "industry standard" length that a password should be?

  - Currently, the industry standard for password length is eight characters.

  - We will soon find out that eight is only a minimum. It can still be cracked, though it takes some patience.

Navigate to [https://howsecureismypassword.net/](https://howsecureismypassword.net/).

To demonstrate the importance of length, we will repeat the same character in one long string.

- Enter `jjjjjjjj` (eight j's). Eight characters crack instantly.

- Enter `jjjjjjjjjjjj` (twelve j's). Twelve characters will take four weeks to crack.

- Enter `jjjjjjjjjjjjjjjj` (sixteen j's). This password takes 35 thousand years to crack.

- Enter `b4Ei@2!` (seven random characters). This password only takes seven minutes to crack.

- Enter `Jng0i$7w` (eight random characters). This password takes nine hours to crack.

- Enter `534Yc8@CmF` (ten random characters). This password takes 6 years to crack.

- Enter `*%uDiH2^T2n4` (twelve random characters). This password takes 34 thousand years to crack.

Takeaways of this section:

- If a system requires sixteen characters and nothing else, the password will remain relatively strong, even if words are embedded.

- Add in a few extra characters and it will get exponentially more secure.

- In contrast, if you use all random characters, you _still_ have to make the password at least 10 characters long for it to be very effective.

#### Managing Passwords as Administrators

As an administrator, we can do the following to control and secure user passwords:

- We may not be able to easily see what a user's password is, but we can see the last time they reset their password.

- We can cause the password to expire after some time so the user has to set a new password.

- We can also set length, number, and character requirements.


The only tools we need are `chage` (_change user password expiry information_) and `nano` to edit the settings inside the `/etc/security/pwquality.conf` file.

Note the following about `chage`:

- `chage` allows us to change the number of days between password changes for each user.

- The system uses this info to determine when a user must change their password.

- Below are some common options we can use with `chage`:

  - `chage -l` to show the account aging info.

  - `chage -M` to set the number of days between password expirations.

  - `chage -W` to set the number of warnings the user gets before the change must be made.

  - `chage -d 0` to force an immediate password change.

#### Administrating Passwords Demo

In the upcoming demo, we will update user Billy's password expiration information. We will also change the password strength requirements for the updated password. Specifically, we will:

- Change the maximum number of days between password changes to 90.

- Change the number of days of warning before a password expires to 10.

- Force Billy's current password to expire immediately.

- Ensure the new password differs from an old password by at least one character.

- Ensure the new password does not match common dictionary words.

- Set the minimum character length of new passwords to 12.

- Set the minimum character types in a password—such as uppercase letters, lowercase letters, numbers, and special characters—to two. 


Let's begin by looking at Billy's password expiration info.

- Run `chage -l billy`

- Our command output should be similar to the following:

  ```bash
  Last password change		                           : Dec 09, 2018
  Password expires		                           : never
  Password inactive		                           : never
  Account expires		                                   : never
  Minimum number of days between password change		   : 0
  Maximum number of days between password change		   : 99999
  Number of days of warning before password expires	   : 7
  ```

While the output is fairly self-explanatory, we will go over the main details:

- Billy’s password never expires and it has the highest value possible for the maximum number of days between password changes.

- Billy will get seven days of warning before his account forces a password change.

Now, we will change the number of days between expirations to 90 days.

- Run `sudo chage -M 90 billy` 

  - Syntax breakdown:
    - `sudo` is used because this change has to be completed by an administrator.
    - `chage` is the change password expiry information command.
    - `-M` stands for _maximum_.
    - `90` is the maximum number of days we are setting.
    - `billy` is the user for which we want to make changes.


- Running `chage -l` shows us that the maximum number of days between password change has been changed to `90` and the `Password expires` value has also been updated.

Now, we will set the `number of days of warning before password expires` to `10`.

- Run `sudo chage -W 10 billy`
  - Syntax breakdown:
    - `sudo` and `chage` stand for the same as the previous command.
    - `-W` stands for _warning_.
    - `10` is the number of days given to the warning setting.
    - `billy` is the user for which we want to make changes.

- Running `chage -l` shows us that the `Number of days of warning before password expires` has been updated.

Next, we will force a password to expire immediately.

- Run `sudo chage -d 0 billy` 

  - Syntax breakdown:
    - `-d` stands for _last day_. This sets the number of days since Jan 1st, 1970, when the password was last changed.
    - `0` is the number of days given to the last day setting. Essentially, this means, "This password has never been changed," which causes `chage` to require a password change.

To confirm our results:
 
 - Run `chage -l`
 
 - The fields `Last password change`, `Password expires` and `Password inactive` have all been changed to `Password must be changed`. 
 
 - Our output should look similar to this:

    ```bash
    Last password change		                         : password must be changed
    Password expires		                         : password must be changed
    Password inactive		                         : password must be changed
    Account expires		                                 : never
    Minimum number of days between password change		 : 0
    Maximum number of days between password change		 : 90
    Number of days of warning before password expires	 : 10
    ```

#### Updating Configuration Files

Now that we know how to force a password change, we can ensure that each user is required to create a strong password by editing the `/etc/security/pwquality.conf` file.

A brief review of Linux configuration files and the process of "commenting out":

- Configuration files will often have configurations written as comments.

- As you may know, comments in code begin with `#`. This symbol indicates to the system that these lines are not meant to be interpreted as a line of code, but rather intended to be read by the user as notes, tips, or additional information.

- Most configurations are written with a `#`, even though they are actually run-able processes. This way, admins can turn them on and off based on their preferences.

- To turn on these configurations, they simply delete the `#`. The system will then no longer read the line as a comment, but rather as the line of code that enables a configuration.

- The process of deleting the `#` and therefore enabling the configuration is called "commenting out."

For example: By default, this configuration will be commented out. It also includes an actual comment explaining what the configuration does.

  ```bash 
  # Number of characters in the new password that must not be present in the old password
  # difok = 1
  ```

If the admin wants to enable and edit this configuration, they simply delete the `#` in front of the configuration:

  ```bash
  # Number of characters in the new password that must not be present in the old password
  difok = 1
  ```

#### Updating `etc/security/pwquality.config` File

We will now make changes to the `/etc/security/pwquality.conf` configuration file to ensure the following:

- In order to keep users from "changing" their old password to the exact same password, we will change the number of characters that must be changed during password updates, using the `difok` configuration.

- To keep users from using crack-able dictionary words in their passwords, we will enable the `dictcheck` parameter.

- We will also set the minimum password length to 12 characters and the minimum number of different character types—letters, numbers, special characters, etc—to two.

Note: We can set other configurations as well, but these are outside the scope of this demonstration.

- Run `sudo nano /etc/security/pwquality.conf`

The output should resemble the following:

  ```bash
  # Configuration for system wide password quality limits
  # Defaults
  #
  # Number of characters in the new password that must not be present in the old password
  # difok = 1
  #
  ```

For each setting in this file, there is a clear comment, starting with `#`, that describes what the proceeding setting does. In this file, we can see that the settings have been commented out.

Move to the `difok` setting and note the following:

- The comment describes the setting: `Number of characters in the new password that must not be present in the old password.`

- `difok` is set with a value of `1`, which means that the user only needs to change their password by one character to differentiate it from the old password.


We will uncomment this line and change its value to `2`.

- Make the update to the file as shown below:

  ```bash
  # Configuration for system wide password quality limits
  # Defaults
  #
  # Number of characters in the new password that must not be present in the old password
  difok = 2
  #
  ```

  - This configuration is now changed.

Next, scroll down to the `dictcheck` configuration:

- Configuration looks like: 
  
  ```bash
  # Whether to check for the words from the cracklib dictionary.
  # The check is enabled if the value is not 0.
  # dictcheck = 1
  #
  ```

    - Again, a comment describes what the configuration does: `Whether to check for the words from the cracklib dictionary.`

    - There is also a line describing how to enable the configuration: `The check is enabled if the value is not 0.`

    - `dictcheck` has the current value of `1`, meaning it would be enabled if it were not commented out.

All we need to do is uncomment the `dictcheck` line to enable it.

- Make the update to the file as shown below:

  ```bash
  # Whether to check for the words from the cracklib dictionary.
  # The check is enabled if the value is not 0.
  dictcheck = 1
  #
  ```

Next, if we wanted to add minimum password length and character type requirements, we just add the following options to our file:

- `minlen = <minimum character length>`

- `minclass = <minimum number of character types>`

 Add the following lines to our file so that the minimum character length is 12, and the minimum number of character types is two.

- Run:
  
  `minlen = 12`  
  `minclass = 16`

Save the file. The next time someone changes their password, these new settings will be used for password requirements.

#### Summary

In this demonstration, we:

- Updated Billy's password expiration info, so that the maximum time between password updates is 90 days. Billy will now also get 10 days of warning before he has to update his password.

- Changed `difok` to require users to make a unique password.

- Enabled `dictcheck` to automatically check whether passwords use dictionary words.

- Set the minimum character length to 12 and the minimum number of character types to two.

We covered the following four commands:

- `chage -l` to show the account aging info.

- `chage -M` to set the number of days between password expirations.

- `chage -W` to set the number of warnings the user gets before the change must be made.

- `chage -d 0` to force an immediate password change.

This password strength file is located in `/etc/security/pwquality.conf`.


### 03: Activity: Let's Talk to John

- [Activity File: Let's Talk to John](Activities/03_STU_Talk_to_John/Unsolved/README.md)



### 04: Activity Review: Let's Talk to John 

- [Solution Guide: Let's Talk to John](Activities/03_STU_Talk_to_John/Solved/README.md)

### 05: Privileges, `root`, `sudo` and `su` Demo 

We've been using `sudo` for several commands over the last two days of class.

Why is `sudo` is needed for some commands and not others? Note the following about permissions: 

- Every file and program on a Linux system has permissions associated with it. These permissions tell the system what user can access that file or run that program.

- Additionally, administrators can place users in a group, and set file and program permissions to allow a specific group or groups to have access.

- For instance, a company can create a group for employees who work in Marketing and another group for employees who work in Accounting. The administrator can give these groups access to specific programs needed by their department. 

- The permissions for a given file or program apply to all the users on the system, except for the root user.

- The root user is the super user, or the highest administrator on the system. The root user has complete access to the system and can perform any action, access any file, and run any program.

During the last activity, we learned just how sensitive the `/etc/shadow` file is. Typically, **only** the root user has access to this file. This is an example of how permissions can protect parts of the system.

When an attacker is trying to gain access to a system, they are usually trying to gain `root access` or access to the root user, so they can do whatever they want to the system. Hackers can achieve this access by switching users. 


#### Switching Users and Elevating Privileges

The Linux system can access different users with `su`.

- `su` stands for _switch user_. If you have another user's password, you can log in as that user with `su <username>`.

- Switching users can be helpful for troubleshooting. You can see firsthand what the user has access to, and test their permissions. You can also see what they've been doing with the system from their perspective, with full access to their files.

- From a security perspective, switching users allows you to use the system with their permissions. This lets you run commands as that user, view files that only that user has access to, and otherwise imitate the user.

Linux systems secure root access with `sudo`.

- Properly secured Linux systems do not allow anyone to log in as the root user on the system. Instead, following the principle of least privilege, if a user needs access to something only the root user can do, they can use the `sudo` command to invoke the root user just for that one command.

- `sudo` stands for _superuser do_, and if a normal user is allowed to use `sudo`, they can run a root-privileged command. When the command is complete, the user is reverted to their normal access.

- `sudo` can also control which commands the user can run as root user. This way, the system has granular control over who can run root commands, and which ones. It also keeps a log of exactly which user runs which commands, which can be reviewed as needed.

To configure `sudo` access:

- `sudo` access is configured using a configuration file—the `sudoers` file.

- Inside that file, a `sudo` group is specified along with which commands `sudo` can be used with.

- The `sudo` group is typically given full system access to use `sudo`.

- Any user on the system that needs `sudo` access is then added as a member of the group. Any member of the group receives the same access and ability to use `sudo` for any command.

- Alternatively, a user can be kept out of the `sudo` group and added to the configuration file individually, along with a specification of which commands that user can use `sudo` for.

- Adding a user individually to the `sudo` configuration file is common when the sysadmin has a user that only needs `sudo` access for a few commands.

#### `su` vs. `sudo` Demonstration

In the next demo, we will attempt to update all of our existing software packages.
- If our privileges do not allow us to do so, we will first use `su` to switch directly to the root user.

- We'll then show the dangers of working directly as the root user. 
- We'll then do the same updates by using `sudo` instead and show why this is the more secure option.

We will use the following commands to do these tasks:
  - `whoami` to view your current user.
  
  - `su` to switch to another user, in this case, the root user.
  - `sudo` to invoke the root user for one command only.


When we run `apt update` in the terminal, this doesn't work.

- Only the  `root` user has the ability to use the `apt` program. Because we are not `root`, we received a `Permissions denied` error.

Running `whoami` shows that we are the `admin` user.

We will now log in as the root user with `su`.

- Run `su root` (password: `toor`)

Run `whoami` to show that we are now `root`.

- The prompt now also uses a `#`, indicating that we are the root user. A standard user's prompt will generally show a `$`.

Now that we’re the root user, we can install packages.

- Run `apt update`

  ```bash
  $ apt update
  Reading package lists... Done
  E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
  E: Unable to lock directory /var/lib/apt/lists/
  ```

- This command updates the package repositories so we can download the latest software.

- The `Permission denied` message indicates that we do not have permission to open a file (`/var/lib/apt/lists/lock`), and that we need to use `apt`.

Once you, or a process, is logged in as `root`, you can make any changes you want to the system, including changes or malicious actions that may harm the system.

Here is a quick example:

- Run `su root` (password `toor`) to log back in as `root`.

- Run `ls /home` to show the current home folders.

- Run `rm -r /home/john` to remove the home folder for `john`.

- Run `ls home` again to show that it is removed.

- Run `mkdir /home/john` to create a new empty directory.

At no time during this process were we asked for a password.
- That is because we are the root user and can perform any action we wish, without the system stopping us.

- Not only is this a problem if we want to make system and software changes, but it's also a problem if we were to make a mistake and remove the wrong files.

Once we are logged in as another user, we can log out by typing `exit`.

- Run `exit`  and this will log us out as the user.

A better alternative to making the same changes is to use `sudo`.

- `sudo` will always ask you for a password, and it will only allow you to complete the actions you have access to.

- `sudo` adds a layer of security because it forces the administrator to consciously run a command with privileges.

- `sudo` also saves a log for each time the command is used. Therefore, an administrator can audit the log to find out which user did what.

Run `sudo apt update` and note that we have to first enter our password to use `sudo`.

Now we will try to delete a directory like we did previously:

- Run `ls /home` to show the current home folders.

- Run `rm -r /home/john`

Our output should be similar to:

```bash
$ rm -r /home/john
rm: cannot rm directory ‘/home/john’: Permission denied
```

Restricting `sudo` use among users and only allowing access for specific commands reduces the risk of harm to the system.



#### Assigning `sudo` Access Demo

Note that in the previous demo, we didn't have to log in as `root` because we could just use the `sudo` command to use the `apt` command.

If we want to see exactly what `sudo` access we have, we can run `sudo -l`.

- Run `sudo -l`. Our output should contain the line:

```bash
  User instructor may run the following commands on localhost:
      (ALL) ALL: ALL
```

- We, the instructor user, have `ALL` access.

We can check the privileges of a user with the `-lU` options. We can check the privileges of a user, `sally`, with the following command.

- Run `sudo -lU sally`. Our output should be:

```bash
User sally is not allowed to run sudo on ubuntu-vm.
```

We can give `sally` full `sudo` access by adding her to the `sudo` group.

- Run `sudo usermod -aG sudo sally` to add Sally to the `sudo` group.


- Run `sudo -lU sally`. Our output should now read:

```bash
  User user may run the following commands on localhost:
      (ALL) ALL: ALL
```
- `sally` now has full access.

We can also give a user `sudo` access for just a single update. For example, we want to give our user `john`  `sudo` access for `apt` so he can run software updates.

Why can't we just add `john` to the `sudo` group?
- This will give him full access to run any command, which we don't want.


Remember, the `sudo` settings are configured in the `/etc/sudoers` file.

In order to update the `/etc/sudoers` file, you must use the command `visudo`, which opens the `etc/sudoers` file using Nano.
  - Using `visudo` to edit this file is necessary because `visudo` does a syntax check on the `sudoers` file before it is saved, to prevent corruption of the file.

  - Breaking this file can lock you out of the system entirely, so you want to be sure to always use `visudo` to edit the file.

Run `sudo visudo`

Scroll down to find the following lines at the bottom of the file:

  ```bash
  # User privilege specification
  root  ALL=(ALL:ALL) ALL

  # Members of the admin group may gain root privileges
  %admin  ALL=(ALL) ALL

  # Allow members of group sudo to execute any command
  %sudo  ALL=(ALL:ALL) ALL
  ```

Note the following: 

- `root  ALL=(ALL:ALL) ALL`: Allow the `root` user to run any command under any user or group on any system.

- `%admin  ALL=(ALL) ALL`: Allow all members of the `admin` group to run any command with `sudo` under any user on any system.

- `%sudo  ALL=(ALL) ALL`: Allow all members of the `sudo` group to run any command with `sudo` under any user on any system.

The general syntax of these lines are as follows:

- [`USER` or %`GROUP`]  `HOST`=(`USER`:`GROUP`) `COMMAND`

  - The `HOST` is normally set to `ALL` but can be changed if the administrator wants to limit which machines can use this file.
- For a group entry, the `GROUP` inside the parenthesis can be left out: %`GROUP` `HOST`=(`USER`) `COMMAND`
- To remove the password requirement, `NOPASSWD` is added: `USER` `HOST`=(`USER`) `NOPASSWD`: `COMMAND`

This means any user in the secondary group `sudo` _or_ `admin` can use `sudo` to run privileged commands with their password.

Add the line `john  ALL=(ALL:ALL) /usr/bin/apt-get`. 

- Syntax breakdown:

  - This allows the user `john` to run the `apt` command with `sudo` as the `root` user,  on any `host`, after entering his password.

  - `john` now has access to run the `apt` command and update software packages.

Save and exit.

Verify your new settings. 

- Run `sudo -lU john`

- Output should look like: 
  
    ```bash
     User john may run the following commands on localhost:
      ALL=(ALL:ALL) /usr/bin/apt-get
    ```

#### Attackers Gaining Root Access Demo

Even when `sudo` use is restricted to specific commands, depending on the command, a user can still gain access to `root`.

In this last demo, we will pretend we are an attacker and attempt to gain `root` access from an account that has `sudo` access to one of these commands.

There are several different commands for which this can be a problem, but today we will look at the `less` command.

Let's return to our example of `john`. In addition to allowing `john` the ability to install software, we may also want to allow him to read any of the sensitive files on the system using `less`.

- `less`, however, has a feature that allows you to run commands without exiting the `less` command, and those commands are run with the same privileges that `less` has.

  - In other words, if a user has `sudo` access for `less`, they can open `less` and then start running commands from inside `less` with `sudo` privileges.

To demonstrate this, we will use `sudo less` with the admin user and then move from `less` directly into a root shell with `!bash`.

- Run `visudo` and edit the entry for `john` to give him `sudo` access to `less`.

- Output should look like:
```
    john ALL=(ALL:ALL) /usr/bin/apt-get, /usr/bin/less
```
Save and exit.

Now we will run `sudo less` on any file that belongs to John:

- Run `su john` (password: `lakers`) to switch to John's user.

- Run `touch /home/john/my_file`

- Run `sudo less /home/john/my_file`

Because we ran `less` with the `sudo` command, when we are inside `less` we are no longer `john`. Instead, we are now `root`.

To run a command from inside `less`, we use `!` followed by the command.

You can run any command with `less`, but it makes the most sense to run `bash`. This command will launch another shell from inside `less` with your current `root` privileges.

- Type `!bash` and press `Enter` to drop into a root shell.

We now have a `#` at the prompt again, indicating we have `root` privileges.

- Run `whoami` to confirm that we are `root`.

Attackers often look for this kind of loophole to escalate their privileges on a system.

- This kind of exploit is called an **escape** exploit because you are _escaping_ the program `less` and getting full system access.

- It's important to restrict which commands users can use with `sudo` in `/etc/sudoers` and to always make sure there are no known vulnerabilities with the commands you _do_ allow.

#### Summary

We used the following commands in the demo:

- `whoami` to determine your current user.

- `su` to switch to another user, in this case the root user.

- `sudo` to invoke the root user for one command only.

- `sudo -l` to list the `sudo` privileges for a user.

- `visudo` to edit the `sudoers` file.


### 06: Activity: `Sudo` Wrestling

- [Activity File: `Sudo` Wrestling](Activities/06_STU_Sudo_Wrestling/Unsolved/README.md)


### 07. Activity Review: `Sudo` Wrestling

- [Solution Guide: `Sudo` Wrestling](Activities/06_STU_Sudo_Wrestling/Solved/README.md)

#### Activity Recap

- You must first look at your own user privileges before looking at the rest of the users.

- `sudo -l` is a great command to remember and is often useful in figuring out what you can do on a system.

- As with `less`, there are exploits for `vim`, `more`, `python`, `ruby` and `perl`, should a user have permission to run one of these with `sudo`.

- This exercise clarifies just one reason why securing `sudo` and `root` access is important. Being able to determine which users or processes have root access is a core skill of a system administrator.

- Admins will often ensure that users are not set up with any additional access to `sudo` or `root` than is necessary, following the principle of least privilege.

### 08. Break

### 09. Users and Groups

To recap:

- Linux is a multi-user OS and related users can be added to groups.

- We briefly discussed this when we spoke about the `sudo` and `admin` groups.

- In the case of `sudo`, all users added to the `sudo` or `admin` groups have full access to `sudo`.

Linux has the ability to create groups of users for other functions, like file or services sharing:

- If a company has different departments like Sales, Accounting, and Marketing, a Linux administrator can create a group for each department. Only the users in the group can access files owned by the group.

- Therefore, a system admin must know how to to add and remove users from a system, add and remove groups, and add and remove users from those groups.

Linux has a few easy commands that are used specifically for user and group management, which we will focus on in this section.

Before diving into these commands, we’ll cover how Linux identifies users and groups in the system using the `id` command. 

Note the following about the `id` command:

- Linux associates a specific number with each user for identification purposes. This number called a **user ID**, or **UID**.

- When Linux needs to identify a user, it doesn’t look at the username, it uses the UID number.

- System users, or automated users designed to complete system tasks, have UIDs assigned at numbers less than `1000`.

- Standard users, or users that are assigned to a real person, have UIDs assigned at numbers greater than `1000`.

- The root user always has the UID of `0`.

- Likewise, the **GID** is the **group ID** that is associated with a group.

Run `id`.

- Our UID is above `1000`, which indicates that we are a standard user.

We can also see the UID for each user in the `/etc/passwd file`.

- Run  `head /etc/passwd`

  - The system UIDs start with root at `0` and move up from there.

Remember, UIDs and GIDs are only a system number that Linux uses for identification.

If we want to see the groups that a user belongs to, we can use the command `groups`.

- Run `groups`

  - It prints our user's groups to the screen.

- Run `id`.

  - That this also shows us the groups along with the GID's assigned to them.

#### Users and Groups Demo

**Note:** Before beginning this demo please run the following command:
- `adduser mike`
- `sudo addgroup general`
- `usermod -aG general mike`


In the upcoming demo, we’ll dive into more actions around user and group management, using the following scenario:

- The company you work for recently had a change to its developer team. Mike, a lead developer, has left the company. Joseph has joined as a new junior developer.

- The company's Linux system has never been set up properly with a `developers` group. Instead, Mike was part of the `general` group.

- As the sysadmin for this system, you need to remove Mike from the `general` group, remove the `general` group, and delete Mike's user from the system. Then, you need to add Joseph to the system, create a `developers` group, and add Joseph to this group.

In order to accomplish these tasks, we will:

1. Get group info for Mike's user using the command `groups`.

2. Lock Mike's account to prevent him from logging in using the command `usermod`.

3. Remove the `mike` user from the `general` group with the command `usermod`.

4. Delete the `mike` user by using the command `deluser --remove-home`.

5. Delete the `general` group using the command `delgroup`.

6. Create a `joseph` user with the command `adduser`.

7. Create a `developer` group using the command `addgroup`.

8. Add the `joseph` user to the `developer` group using the command `usermod`.


First, we'll see what groups Mike belongs to.

- Run `groups mike` to print `mike`'s groups to the screen.

- Our output should be:

  ```bash
  $ groups mike
  mike general
  ```
- Each user is also a member of a group that shares the name of the user.

  - When a user is created, Linux by default creates a group for which that user becomes a member.


The `usermod` command has many different options and lets us do many things to user accounts, but we are going to look at the `-L` and `-G` options. The `L` option will lock the account and the `-G` option will specify the groups a user should belong to.

- Run `sudo usermod -L mike` to lock the account.

  - Syntax breakdown:

    - `sudo`: Only `root` can modify users and groups, so we will have to use `sudo` for all of our commands.
    - `usermod`: Allows us to make many modifications to users. In this case, we are using it to add and remove groups.
    - `-L`: `usermod` flag that locks an account so it cannot be logged into.
    - `mike`: The `usermod` command always ends with the user we are modifying.


- Run `sudo usermod -G mike mike` to remove `mike` from the `general` group. 

  - Syntax breakdown:

    - `sudo`: Only `root` can modify users and groups, so we will have to use `sudo` for all of our commands.
    - `usermod`: Allows us to make many modifications to users. In this case, we are using it to add and remove groups.
    - `-G`: This `usermod` flag specifies which groups the user should belong to. The groups  we specify following this command will be the _only_ groups that user belongs to after we run the command.
    - `mike`: Following the `-G` flag are the groups we wish the user to belong to. In this case, we want the user `mike` to be a member of the `mike` group only, effectively removing the `general` group.
    - `mike`: The `usermod` command always ends with the user you are modifying.

- Run `groups mike` to confirm the result.

  - Our output should be:

    ```bash
    $ groups mike
    mike
    ```

  - Mike has successfully been removed from the `general` group.

We can now remove the `mike` user from the system using the `deluser` command.

- Run `sudo deluser --remove-home mike` and break down the syntax:

  - `sudo`: Only `root` can modify users and groups, so we will have to use `sudo` for all of our commands.
  - `deluser`: Allows us to delete users from the system.
  - `--remove-home`: `deluser` flag that removes the user's home folder along with the user.
  - `mike`: The `deluser` command always ends with the user we wish to delete. 

If we use the `deluser` command without any flags, it will leave all of Mike's files intact including his home folder. In this case, we will remove the user _and_ remove all his home folder files.

- Run `ls /home` to confirm our results.

  - Mike's home folder has been deleted.

Remember how we can verify users or groups on the system:

- We can check for users in the `/etc/passwd` file with `less /etc/passwd`.

- We can check for groups in the `/etc/group` file with `less /etc/group`.

  - Run `less /etc/passwd` to verify that `mike` is deleted.

  - Run `less /etc/group`

  - The `general` group still exists. The line for the `general` group should look like this:

    ```bash
    general:x:32:
    ```

  - If this group had any members, they would be listed after the last `:`. In this case, there are no members left in this group.

We can now remove the `general` group with the `delgroup`.

- Run `sudo delgroup general`
 
  - Run `less /etc/group` to verify it is gone.

Now, we will create our new user, `joseph`.

- Run `sudo adduser joseph` and complete the prompts to give `joseph` a password and other info.

- Run `groups joseph` to display the `joseph` group.

   Our output should look like:

  ```bash
  $ groups joseph
  joseph
  ```

Remember, when a user is added to the system, by default, a group by the same name is added. Also, when a user is deleted, their group is also deleted, as long as no other users are members of that group.

Next, we will create a new `developer` group using the `addgroup` command. Then, we can add the user `joseph` to the group.

- Run `sudo addgroup developers`

We received a `Done` message, but we can also verify this group was added in the `/etc/group` file.

- Run `tail /etc/group`

  - We can now see both the new `joseph` group that was created when we added the user `joseph`, as well as the new `developers` group that we just created.

We are now ready to add `joseph` to the `developers` group using the `usermod` command.


- Run `sudo usermod -aG developers joseph` 

  - Syntax breakdown:

    - `sudo`: Only `root` can modify users and groups, so we will have to use `sudo` for all of our commands.
    - `usermod`: Allows us to make many modifications to users. In this case, we are using it to add and remove groups.
    - `-aG`: This `usermod` flag combination (_add group_) specifies what groups the user should be added to.
    - `developers`: Following the `-aG` flag are the groups we wish to add the user to. In this case, we want the user `joseph` to the `developers` group.
    - `joseph`: The `usermod` command always ends with the user we are modifying.


- Run `groups joseph`

  - Joseph is now part of the `developer` group, as a secondary group.

- Our output should be:

  ```bash
  $ groups joseph
  joseph developers
  ```
- We have now created the `joseph` user, created the `developers` group and added `joseph` to it.

A user always has a _primary_ group that is typically the same name as the user. The primary group can be changed to another group, but there isn't usually a reason to do so.

Groups that a user is added to beyond the primary group are known as _secondary_ groups. A user can be a member of unlimited secondary groups.

In this demo, we:

1. Received group info for the `mike` user with the command `groups`.

2. Used `usermod` to lock `mike`'s account to prevent him from logging into our system.

3. Removed the `mike` user from the `general` group using the command `usermod`.

4. Deleted the `mike` user with the command `deluser --remove-home`.

5. Deleted the `general` group with the command `delgroup`.

6. Created a `joseph` user with the command `adduser`.

7. Created a `developer` group with the command `addgroup`.

8. Added the `joseph` user to the `developer` group using the command `usermod`.


### 10. Activity: Users and Groups  

- [Activity File: Users and Groups](Activities/10_STU_Users_and_Groups/Unsolved/README.md)

### 11. Activity Review: Users and Groups

- [Solution Guide: Users and Groups](Activities/10_STU_Users_and_Groups/Solved/README.md)

### 12. Access Controls and Permissions 

How many of you have used Google Docs?

- Google Docs is a fantastic resource because we can choose who we share files with and what permissions they have when they receive the file—such as whether they can read, comment, or make edits to the file.

This function is an **access control**.  

- These controls determine which actions users are able to take on a file (edit, view, etc.).  

- **Permission** regulates who can take which actions. For example, Jane can read and write, but Ivan can only read.

Most of the day, we have been discussing why it's important to limit access on the system. Access controls and permissions also help us follow the principle of least privilege.

Linux has a very granular way of setting these permissions:

- Linux categorizes files, programs, and directories as items.

- Each item has permissions allowing or preventing access to **read**, **write**, and **execute**.  

- For each item, we specify the access that the **owner**, the **group**, and **others** have. 

  - The _owner_ is typically the user that created the item. However, this can be changed.

  - The _group_ is typically the primary group of the owner. However, this can also be changed.  

  - _Others_ includes everyone who is not the owner, and not in the group. 


#### Read, Write and Execute

For each of the three mentioned categories—owner, group, and other—we have three options we can manipulate: _read_, _write_ and _execute_.

- _Read_ determines if the item can be read.
- _Write_ determines if the item can be written to.
- _Execute_ determines if the item can be executed.

While _execute_ can be applied to a file, it really only has effect for items that can be _executed_, like a program or a directory.

For any given item, we can specify if the owner can _read_, _write_ or _execute_, if the group can _read_, _write_ or _execute_, and if others can _read_, _write_ or _execute_.

- This is called **Discretionary Access Control**, or **DAC**. It is called _discretionary_ because these permissions can be passed from one item to another. For instance, a directory may pass on its permissions to items inside it.

- We saw an example of an item passing its permissions to another item in our previous activity, when the program `less` passed on its root permissions to the `bash` shell that ran inside it.

This gives us nine options for any given item, and each option can either be allowed or not allowed in any combination.

- To keep things as concise as possible, when we view each of these options on the command line, they are abbreviated to one letter: `r` for _read_, `w` for _write_ and `x` for _execute_.

#### Permissions Demonstration Setup

In this demo we will create a file and a directory and look at the default permissions. Then, we will change these permissions to deny particular users and groups access.

 In order to read and manipulate these file permissions, we need the following commands:

- `ls -l` to show the permissions info.

- `chmod` to change the permissions info.

- `chown` to change the owner and group of a file.

The goal will not be how to use the commands, but rather learning the syntax of the permissions themselves and how to combine them with users and groups to create custom access controls.

#### Inspecting Permissions

We'll start by creating a file and inspecting its permissions.

Move into your Documents folder.

- Run `touch my_file` to create a file.

- Run `mkdir my_dir` to create a directory.

- Run `ls -l` to show these files and their permissions info. Our output should be similar to the following:

  ```
  drwxr-xr-x 2 Owner Group 4096 Month Day Time my_dir
  -rw-r--r-- 1 Owner Group 0 Month Day Time my_file
  ```

This list includes more information than just the file name. Let's use `my_file` as an example:

- File or directory permissions: `-rw-r--r--`

- Number of links to this file: `1`

- Username of file or directory owner: `owner`

- Group assigned to the file or directory: `group`

- Size (in bytes): `0`

- Date and time of last modification: This will be the date and time when the items were created.

- File or directory name: `my_file`

For this demo, we will focus only on the permissions, and cover the following:

- Permissions are always listed in the order of read, write and execute for the user, then group, then other.

Items that are directories will always be labeled `d`. Items that are files will always be labeled with a hyphen (`-`).

The next three characters will show the owner permissions:

- For the directory, the owner permissions is `rwx`, meaning the owner can read, write and execute for the directory.

- The execute permission allows a user to enter that directory with `cd` as opposed to just create files inside the directory (`w`) or list the files in the directory (`r`).

- For the file, permission is `rw-`, meaning the owner can read and write to the file. The `-` indicates the absence of permission for execute on the `my_file` file. The owner does not have permission to execute on the file. 

- This makes sense, because the file isn't something that can be executed. If we wrote code into this file, and we wanted the computer to run it as a program, we could then enable the execute permission so it could be executed.

The middle three characters show the group permissions.

- For the directory, the group permission is `r-x`. The hyphen `-` indicates an absence of write permission.

- The group does not have permission to create files inside the `my_dir` directory, but anyone from the group can enter the directory and view the files inside it.

- For the file, the groups permissions are `r--` . The group can read the file, but it does not have permission to write to or execute the file.

The last three characters show the permissions for all other users:

- For the directory, other permission is `r-x`. All other users can read and execute for the directory. They can only move inside the directory and list the files inside. They cannot create files or otherwise change the contents of the directory.

- For the file, the permission is `r--`. Everyone on the system who is not the owner and not in the group can only read the `my_file` file. They do not have permission to change the file or execute it.

In summary:
- `my_file` has read and write enabled for the owner and only read enabled for the group and others.

- `my_dir` has read, write, and execute enabled for the owner but only read and execute for the group and others.


#### Changing the Owner and Group

Now we will change the owner and the group by using `chown`.

The command `sudo chown owner:group <item>` can change the owner or the group of a file or directory. 

  - Syntax breakdown:

    - `sudo`: Only `root` can make ownership and group changes to an item, which is why we’re using `sudo`.
    - `chown`: Stands for _change owner_. This command can be used to change groups and owners of items.
    - `owner:`: The owner we are specifying for the item.
    - `group`: The group we are specifying for the item.
    - `<item>`: The item we want to change. It can be a file or a directory.

Next, we will change the owner and the group of `my_file` so that we are no longer the owner and we are no longer in the group.

- Run `sudo chown root:root my_file`

What effect will this change have on our permissions for the file?

- We are not the owner, and we are not in the group, so we now fall into the _other_ category.

  - Run `ls -l my_file` to verify the new permissions.

  - What permissions do we have now that we are in the other category?

    - Now we only have read permissions for `my_file`. We cannot write or make changes to it.

- Running `nano my_file` gives us a message from Nano stating we cannot make changes to the file.

- Running `rm my_file` demonstrates that we cannot delete the file either.

Because we have `sudo` access, we can still take any action we want _if_ we invoke those privileges. But without `sudo` access, we cannot edit this file.


#### Changing Permissions

We have the _nine_ options of _read_, _write_ and _execute_ for each of the _owner_, _group_ and _other_ categories.

These options can be changed using one of two notations:

- **Symbolic notation**: Uses the letters `r`, `w`, and `x` to set read, write, and execute permissions.

- **Octal notation**: Uses base-8 numbers to set file permissions. For example, `rwx` is `7` in octal. Octal notation will be covered in more depth momentarily.

If more comfortable, you can always use the symbolic notation when setting permissions yourself. But, octal notation will be relevant in your real-world job, so you should be familiar with it.

- Run `ls -l my_file`.

  - This file was created with the default permissions: `-rw-r--r--`.

We change permissions with the command `chmod`, which stands for _change mode_.

- Run `sudo chmod u=rw,g=rw,o=rw my_file`
  - Only `root` can make permissions changes, which is why we are using `sudo`.

  - The command reads: "Change permissions such that the user has read and write permissions; the group has read and write permissions; and 'others' have read and write permissions."

    - Confirm updated permissions by running `ls -l`.

- Run `nano my_file` and note that we can now edit the file again because we have given write access to the other category, which we are currently part of.

We can remove permissions by leaving out the `r`, `w`, or `x`, and can also remove them or add them for all three categories with a `-` or a `+`.

- Run `sudo chmod +x my_file`

- Run `ls -l my_file`

The `x` option has been set for each the owner, group _and_ other.

- Finally, run: `sudo chmod -x my_file`

  - Run: `ls -l`

  - We have removed the `x` permission from all three categories.

#### Octal Notation

Now, we will use octal notation to set permissions.

Permissions in octal notation are denoted by numbers. Just as `-`,`r`, `w`, and `x` represent specific permissions in symbolic; `0`,`1`,`2`, and `4` represent the same permissions in octal.

- `0` indicates that we have no permissions.

- `1` indicates that we can _execute_ the file.

- `2` indicates that we can _write_ to the file.

- `4` indicates that we can _read_ the file.

Unlike symbolic, in octal, we can add numbers. The sum of these numbers results in specific permission sets.

  - `4` indicates that we can only _read_ the file.

  - `6` indicates that we can _read_ and _write_. (_Read_ + _write_ = `4 + 2` = `6`)

  - `7` indicates that can _read_, _write_, and _execute_. (_Read_ + _write_ + _execute_ = `4 + 2 + 1` = `7`)

Run `sudo chmod 766 my_file`

- The numbers in `766` represent permissions for the owner, group, and world, respectively. In other words, the owner = 7, the group = 6, other = 6.

- Can you decipher the permission for the owner, group, and other?

  - The owner can read, write, and execute (`7`). The group can read and write (`6`). All others can read and write (`6`). 

- Run `ls -l`

  - The permissions now read: `-rwxrw-rw-`.  While this notation tells us the same information as `766`, it is much less compact.

Another example:

  - Run `sudo chmod 444 my_file`. This will give everyone only _read_ permissions.

What command should we run to give everyone _read_ and _write_ permissions?

- To add `2` to each `4`, we will run the following command:

  `sudo chmod 666 my_file`

What command should we run to give the user _read_, _write_ and _execute_ permissions; the group _read_ and _execute_ permissions; and the others _read_ permissions? 

- Run `chmod 754 my_file`


#### Summary

In this demo we created a file and a directory and looked at all the permissions users had by default. Then, we changed the permissions to deny particular users and groups access to this directory and file.

You can use the more intuitive symbolic notation but you should become familiar with octal notation, as it is very commonly used by system administrators.

We used the following commands:

- `ls -l` to show the permissions info.

- `chown user:group` to change the owner and group of a file.

- `chmod` to change the permissions info.

### 13. Activity: Access Controls and Permissions


- [Activity File: Permissions](Activities/13_STU_Permissions/Unsolved/README.md)


### 14. Activity Review: Access Controls and Permissions


- [Solution Guide: Permissions](Activities/13_STU_Permissions/Solved/README.md)


---

© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
