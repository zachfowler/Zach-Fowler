## Solution Guide: Service Users

In the previous activity, we stopped and removed a few old services from the system. In this activity, we removed those users from the system and added a new service user for `tripwire`.

To complete this activity, we needed to: 
- Use the `deluser` command to remove four lingering users.

- Use the `adduser` command with the correct flags to create a new `tripwire` user.

- Edit the `sudoers` file to allow the `tripwire` user to run `tripwire` with `sudo`.

- Change the `tripwire` permissions to only allow the owner of `tripwire` to run the service.

**Note:** These steps are not always needed, as most services create their own user when the package is installed.


The first step is to remove any service users associated with the services that we removed in the previous activity. The services we removed were: `FTP`, `Apache2`, `Telnet` and `dovecot`.

- To remove the service users, run `sudo deluser --remove-all-files <username>` for each service. 

    - For example, `sudo deluser --remove-all-files dovecot`

We will create a `tripwire` user that will be dedicated to running Tripwire:

- Run `sudo adduser --system --no-create-home tripwire`

- Run `id tripwire` and verify that the `UID` is less than 1000.

- Run `ls /home` to verify there is no `tripwire` home folder.

Remember, we can see password entries in the `/etc/shadow` file.

- Run `sudo tail /etc/shadow`

The `*` in the password field for the Tripwire user means the user is locked without a password.

- Run `sudo tail /etc/passwd`

Note that `usr/sbin/nologin` is at the end of the Tripwire line.

We will add a line to the `sudoers` file in order to allow this user to run only `tripwire` using `sudo` privileges.

- Run `sudo visudo`

- Add `tripwire ALL= NOPASSWD: /usr/bin/tripwire` to the user section of the file and save it.

- The section should read:

    ```bash
    # User privilege specification
    root ALL=(ALL:ALL) ALL
    tripwire ALL= NOPASSWD: /usr/bin/tripwire
    ```

We will change the permission of the `tripwire` program to only allow the `owner` to execute it.

- Run `which tripwire` to locate the `tripwire` package.

- Run `sudo chmod 700 /usr/bin/tripwire`

- Run `ls -l /usr/bin/tripwire` to verify.
