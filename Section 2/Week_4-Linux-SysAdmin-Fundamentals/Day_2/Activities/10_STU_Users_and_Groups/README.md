## Student Activity File - Users and Groups

In our previous activity, we tightened down the use of sudo access across the system by editing the sudoers file. The administrator has asked that we audit all the users and groups on the system, create a new group for the standard users and remove users from the sudo group. In our previous activities we have found some malicious users and we will want to remove them from the system altogether.

Now we want adhere to the principle of least access to make sure that the users on the system only have the access we want them to have. Despite the changes we have made so far, there are still unauthorized users in groups who have access to sensitive data. Your senior systems administrator has asked you to audit these groups and remove both unauthorized users as well as suspicious groups.

Along these lines, your senior administrator has asked that you do the following:

- Check every user's UID and group ID.
- Make sure that only the Admin and Student accounts belong to the `sudoers` group.
- If you find a user that is part of the sudoers group, remove them from that group and document your findings.
- Remove any users from the system that should not be there.
- Verify that all non-admin users are part of the group `developers`. If the `developers` group doesn't exist, create it and add the users. We can use this group later to configure file sharing among these users.
- The users `adam`, `billy`, `sally` and `max` should only be members of the managed group and their own group. If you find any groups other than this, document the group and remove it.

This activity will use the same lab environment that you have been using for the previous activities. Username: admin Password: cybersecurity

### Instructions

Begin in the command line inside your lab environment.

Display your ID info.
  - What command does this?

Use the same command to display the ID info for each user on the system.
  - In case you forgot, where can you find out what these usernames are?
  - Record the output from this series of commands to a new file in your research folder.

Print the groups you and the other users belong to.
  - Record the output from this series of commands to a new file in your research folder.

Keep an eye out for anything suspicious that you find with any of the users and document your findings in your research folder.

Make sure you have a copy of the home folder of any rouge users and then remove any users from the system that should not be there. Make sure to remove their home folders as well.
  - Hint: Remember from the first activity, the only standard users that should be on the system are: `admin`, `adam`, `billy`, `sally` and `max`.

Verify that all non-admin users are part of the group `developers`. If the `developers` group doesn't exist, create it and add the users.

The users `adam`, `billy`, `sally` and `max` should _only_ be members of the `developers` group and their own group. If you find any groups other than this, document the group and remove it.
