## Activity File: Service Users

- In the previous activity, we stopped and removed a few old services from the system.

- In this activity, you will continue auditing the same server for your senior administrator.

- The senior administrator would like you to remove any old service users from the system and create a new user that will be dedicated to running the Tripwire program.

- To complete this activity, you will use the `adduser` and `deluser` commands with the correct flags to clean up the system and create this new Tripwire user. 
    - Tripwire can only be run as `root`, so you will also need to add a line to the `sudoers` file to allow this.

### Instructions

- Remove any service users associated with the services that you removed in the previous activity.

   

- Create a `tripwire` user that will be dedicated to running Tripwire.

    - Verify that this user is a service user.

    - Verify that this user does not have a home folder.

    - Verify that this user is locked without a password.

    - Verify that this user does not have a login shell.

- Add a line to the `sudoers` file to allow this user to run only `tripwire` using `sudo` privileges.

- Change the permission of the `tripwire` program to only allow the `owner` to execute.