## Solution Guide: Managing Services

 This activity was an audit of the services running on this server. To complete this activity, you needed to:

- Identify four services in the list that are installed and running on the machine.

- Stop each service.

- Disable each service.

- Uninstall each service.

Run `systemctl -t service --all` to see which services are running.  The following services from the list are listed as present on the server:

- vsftpd.service (FTP)

- apache2.service (HTTP)

- xinetd.service (Telnet)

- dovecot.service (IMAP or POP3)

These services can help attackers gain access to the server, and none of them are necessary for the server to function properly.

- To stop a service:

  - Run `sudo systemctl stop <service_name>`


- To verify the service is stopped:

  - Run `sudo systemctl status <service_name>`


- To disable the service:

  - Run `sudo systemctl disable <service_name>`


- To remove the service from the system:

  - Run `sudo apt remove <service_name>`
