### sed Activity   
  
- You continue to be security analyts at Wonka Corp.
- Your manager believes there is a new cybercriminal trying, but failing to login to several administrative websites owned by Wonka.
- Your manager wants to find out information about this cybercriminal before they end up getting any unauthorized access.
- Your manager has provided you with the access logs for two different administrative websites.
- You are first tasked with combining the 2 different access logs into a single file, and then using text processing to make the "failed login" data consistent.

#### Instructions:

Using only the command line, complete the following tasks from within the `/student_day3/learning_sed` folder in your Ubuntu VM:
  
  - Within this directory are two log files from different administrative websites
  - Combine the 2 log files into a single log file called "Combined_Access_logs.txt"
  - Failed logins, may be titled as "ACCESS_DENIED", "INCORRECT_PASSWORD" 
  - Using sed, replace "INCORRECT_PASSWORD" with "ACCESS_DENIED" so the data is consistent
  - Save the results into a new file called: "Update1_Combined_Access_logs.txt"
