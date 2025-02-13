### Solution Guide: `sed` Activity

- The first step is to navigate into the `learning_sed` directory. To do this, run the following commands:
 
       cd student_day3
       cd learning_sed
       
- View the two admin log files inside by running `ls`. This will display:   

       Admin_logA.txt 
       Admin_logB.txt 

- Next we will combine the two files together into a file called `Combined_Access_logs.txt` with the following command:

       cat Admin_logA.txt Admin_logB.txt > Combined_Access_logs.txt 
       
- We will preview the file by using the `cat` command to see the different failed login descriptions, which are titled "ACCESS_DENIED" and "INCORRECT_PASSWORD." 

       cat Combined_Access_logs.txt
           
- Next we will write a `sed` command to replace  "INCORRECT_PASSWORD" with "ACCESS_DENIED" so the data is consistent:    

        cat Combined_Access_logs.txt | sed s/INCORRECT_PASSWORD/ACCESS_DENIED/ 
          
- This command makes the replacement, but we also need to move the data into a new file called `Update1_Combined_Access_logs.txt/`. To do so, run the following command:


         cat Combined_Access_logs.txt |  sed s/INCORRECT_PASSWORD/ACCESS_DENIED/ > Update1_Combined_Access_logs.txt
