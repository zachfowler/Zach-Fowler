## Activity File: Securing `root` 

- In the previous activity, we cleaned up the service users on the system and created a `tripwire` user that we can use to run the `tripwire` program.

- In this activity, we will continue to make changes to the same system as a junior administrator.

- The senior administrator has asked that you now secure the root account to prevent attackers from logging in as `root`.

- To complete this task, you will need to: 
    - Lock the root account.

    - Ensure that it doesn't have a login shell.
    - Ensure that it cannot be assigned a `tty` terminal.
    - Ensure that a user cannot log in directly as `root` by restarting the system in single user mode.

### Instructions 

Take the following steps to ensure that the root account is secure:

1. Change the root password to `1RuT3ZLg05`.

2. Lock the root account.

3. Change the login shell for the root account so it cannot log in.

4. Change the `tty` configuration so the root user is not allowed a `tty` terminal.

5. Verify that you cannot log in as root.

6. Add the password `2XuTeZig0$` to `GRUB` to ensure that single user mode cannot be easily used.

**Bonus**
- Create a hash of `2XuTeZig0$` and use the hash instead of the plain text password.
