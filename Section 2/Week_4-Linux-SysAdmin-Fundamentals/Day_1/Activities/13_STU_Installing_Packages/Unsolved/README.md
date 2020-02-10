## Student Activity File - Installing Packages

Now that we have stopped a malicious service from running and we have completed a basic audit, we want to set some monitoring services up, so we will be notified if something changes in the future. To do this, we will use a utility called Tripwire.

Tripwire monitors files that you specify and emails you a notification when a file has been modified. This is called `File Integrity Monitoring` and Tripwire does this by creating a database of file hashes. This class will discuss hashes in greater detail later in the course, but hashes are a way for Tripwire to quickly check if an entire file has changed without having to read every line.

Once you have a database of file hashes for files that should not change, you can periodically have Tripwire run a new set of hashes and compare them with the old set. If there is a change, Tripwire will tell you what files have been modified.

In addition to Tripwire, we will also install `chkrootkit`, `john` and `Lynis` for later use. `chkrootkit` is a program that checks the system for root kits, and `Lynis` is a security auditing tool that audits the entire Linux environment and provides suggestions for hardening.


### Instructions:
Install the packages: `Tripwire`, `chkrootkit`, `john`  and `Lynis`.

You will need to use the command that you have learned from the installing packages lecture in order to complete this activity.

### Tripwire - Additional Installation Screens
Tripwire requires some non-standard installation screens, so start with it first.

- When Tripwire installs you will be presented with a screen that asks you to set a password for site and local keys. For the purposes of this activity we will use the password `tripwire`. In a real-world setting you would enter a more secure password.
  - The site key is used to secure the configuration files and ensure they are not modified. If you were setting up Tripwire on several servers, you could copy the configuration files and this key across servers.
  - The local key ensures that the tripwire program itself has not been modified.

-  Follow the Tripwire Installation prompts to complete the installation.
  - Configure the mail system with "internet site".
  - When asked to select passphrases, rebuild the configuration and policy files, select `YES`.
  - Create both site and local authentication keys (use `tripwire` for both)

### Bonuses
Each time you install a package, `apt` will ask for permission to acquire the disk space needed to install the package.
- **Bonus 1**: Use the man pages to find a flag that lets you automatically answer yes to any prompts that may come up when installing a package.
- **Bonus 2**: Install multiple packages with a single command.