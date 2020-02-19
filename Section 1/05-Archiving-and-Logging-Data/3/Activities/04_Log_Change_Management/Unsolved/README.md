## Activity File: Log Change Management

In this activity, you are a junior administrator at Rezifp Pharma Inc. The company maintains a large database of files associated with patients, doctors, and their treatments. These files are maintained on a local server.

- You’ve audited the `/var/log/auth.log` file and discovered several modified and deleted files.

- Your CISO asked you to implement a system that generates alerts whenever logs are modified.

### Instructions

A Tripwire check compares the current file system state against a known baseline and alerts on any changes it detects. The baseline and check behavior are controlled by a policy file, which specifies which files or directories to monitor, and which attributes to monitor, such as hashes, file permissions, and ownership.

You need to set up and configure Tripwire to audit activity. These audits will provide critical insights into an attacker's tactics, techniques, and procedures (TTPs).

- Use man pages to help you work through this activity, if needed.

In your Ubuntu VM, launch a terminal and complete following tasks:

1.   Verify and document the version of Tripwire that's installed, for version control purposes.

2.   Initialize Tripwire and enter your local passphrase.

3.   Run a system integrity check using Tripwire.

4.   Test Tripwire configuration by adding a new user called `attacker` to the system.

5.  Run another system integrity check and observe the output.


---