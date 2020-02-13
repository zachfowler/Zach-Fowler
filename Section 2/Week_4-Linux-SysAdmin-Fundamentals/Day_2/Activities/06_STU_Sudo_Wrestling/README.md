## Student Activity File - Sudo Wrestling

Up until now, we have been using administrator privileges as needed to stop processes, install software, copy sensitive files,run programs and edit configuration files.

Now that we know users had weak passwords, we want to make sure none of them have `sudo` access when they shouldn't. The next steps provided by your Senior Administrator all have to do with locking down access to this compromised system, including `sudo` access.

In this activity, you will explore the `sudo + less` exploit, shown in the previous demonstration, and check the compromised system in order to determine if it is vulnerable. You will also edit the `sudoers` file to remove `sudo` access. Being able to determine what users or processes have root access and why is a core skill for a system administrator.

- This activity will use the same lab environment that you have been using for the previous activities. Username: `sysadmin` Password: `cybersecurity`

#### Instructions

- Print the name of your current user to the terminal.

- Determine what `sudo` privileges the sysadmin user has.

- In a text document inside your research folder, record what sudo access each of the users on the system has.
    - Audit each user's files to look for anything suspicious.
    - Record the file paths of your findings.

- There is a user who has sudo access for the `less` command. Find that user and complete the following:
    - Switch to that user by using the password you found in the previous activity.
    - Verify a vulnerability by dropping out of `less` into a root shell.
    - Exit back to the command line.
    - Search this user's files for anything suspicious.
    - Exit that user.

- From the sysadmin user, switch to the root user.

- Read the "sudoers" file to see if there are any users listed there with sudo privileges.

- Edit the sudoers file so that only the administrator user has access.

- Verify that your changes to the sudoers file has worked.
