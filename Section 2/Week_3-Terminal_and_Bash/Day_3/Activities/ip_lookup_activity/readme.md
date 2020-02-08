### Building an IP Lookup Tool  
  
- You continue to be security analyts at Wonka Corp.
- Wonka has been experiencing more attacks on their network
- Your manager needs to know what country these attacks are coming from as Wonka Corp has the ability to block a country from accessing their network.
- You manager is impressed with the great work you did on the last script, and she would like you to design a script that can look up the the country from several IP Addresses they pulled from the logs.

#### Instructions:

Using only the command line, complete the following tasks from within the `/student_day3/IP_Lookup_Tool` folder in your Ubuntu VM:
  
  - You have been provided with the following new command to lookup details on an IP Address:
     - For example, To look up information on the IP of 104.223.95.86, run the following:
       - curl -s http://ipinfo.io/104.223.95.86
     - *Hint - read the man pages of the curl command to get aquantied with its capabilities*
  - Using  `pipes`, `grep`, and `awk`, modify the curl command to display only the Country
    - *Hint - Use grep to only display the line that contains the country*
    - *Hint - Use awk to parse out the Country from that line*
  - Place the command into a new shell script called: `IP_lookup.sh`
  - Modify the script so the IPAddress is an argument that can be passed into the script
  - Run your new  `IP_lookup.sh` with the below IP Addresses as arguments to determine their countries, as they are the IP Addresses found from Wonka's log files
       - IP 1: 133.18.55.255
       - IP 2: 41.34.55.255
       - IP 3: 187.54.23.8
