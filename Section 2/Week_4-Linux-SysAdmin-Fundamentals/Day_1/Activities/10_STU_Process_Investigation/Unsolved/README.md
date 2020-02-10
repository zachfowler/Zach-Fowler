## Student Activity File — Process Investigation

In the last activity, we completed a basic audit of the system and found some malicious script files and a user that was not supposed to be on the system. Now we will investigate all the processes running on the system to see if there are any obvious processes that should not be running.

Your Senior Admin has asked that you record snapshots of processes as well as review the processes in real time for anything suspicious.

In this activity, we are going to look at the processes that are running on the system. You will investigate the current running processes to make sure nothing is amiss. If it is, you will want to kill that process and add what you found to your report.

## Instructions

Log into the lab environment with the following credentials: 
- username: sysadmin 
- password: cybersecurity

During the last activity, you found a script file in a strange location on the system. Take a look at the contents of this script file to get an idea of what commands you might be looking for.

Start by listing all the running processes in real time.

- Review the help menu for this command and get a few ideas for what you might want to investigate.

- Highlight the column that you are sorting by.

To get an idea for how the system is currently running, answer these questions:

- How many tasks have been started on the host?

- How many of these are sleeping?

- Which process uses the most memory?

Search all running processes for a specific user.

- Try looking at all the processes started by the root or sysadmin user.

- Sort by other users on the system that may be of interest.
  
  **Hint**: In the previous exercise, you found a user's home folder that should not be on this system. Is that user running processes?

Next, take a static "snapshot" of all currently running processes, and save it to your research directory with the name `currently_running_processes`.

Use the flag to list all processes that have a TTY terminal.

In the short list of output, do you notice any processes that look suspicious?

List the processes started by the sysadmin user.

List the processes started by any other users with directories in `/home`
- **Hint**: In the previous exercise, you found a user's home folder that should not be on this system. Is that user running processes?

Identify the ID of a suspicious process. Kill that process with the `kill` command.

**Bonus**: `Kill` all processes launched by the user who started the command you just killed. Use Google and/or the man pages to identify a command and flag that will let you kill all processes owned by a specific user.