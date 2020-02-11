## Solution Guide: Process Investigation

Start by logging into the lab environment with:
  - Username: `admin` 
  - Password: `cybersecurity`

Look at the contents of the `str.sh` script files you found in order to get an idea of what you might be looking for.

The `str.sh` script shows two commands:
- `stress-ng --matrix 0 --times`
- `yes`

We will look to see if `str.sh`, `yes` and `stress-ng` are running on the system.
- These commands intentionally stress the system and consume resources which could result in a Denial of Service from the server.

List processes happening in real time using `top`.

- Press the `x` key to highlight the CPU column that it's sorting by.

Answer the following questions (Note: These answers will vary depending on the machine):

1. How many tasks have been started on the host?

2. How many of these are sleeping?

3. Which process uses the most memory?

Press `u` to get a prompt to search all running processes for a specific user.
- If you sort by the user we found earlier named `jack`, you will see the `yes` and `stress-ng` processes that we saw in those scripts.

- Press `q` to close `top`.

Next we'll show only processes with a TTY terminal.

- Run `ps a`. We can see the `yes` and `stress-ng` processes here, too.

Identify the ID of the `yes` command and kill that process with the `kill` command.

- Run `kill <PID for yes>`.

**Bonus**

To kill all processes launched by the malicious user Jack, run:

`sudo killall -u jack`.


-------

© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.

