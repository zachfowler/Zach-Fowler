### Solution Guide: Using `awk`

- The first step is to navigate into the `awk_activity directory`. To do this, run the following commands:
 
       cd student_day3
       cd awk_activity

- Move over the `Update1_Combined_Access_logs.txt` into the directory `/student_day3/learning_awk`:
     
       mv /root/student_day3/learning_sed/Update1_Combined_Access_logs.txt .

    -  the  `.` will place the file in your current directory.
    
- Next we will write an `awk` script to isolate out the fields for Time and Username from this file.

  Open the file to see how the fields are separated and the field numbers for Time and Username. Run: 
  
      cat Update1_Combined_Access_logs.txt
     
  - The fields are separated by spaces, and Time is in field four, and Username is in field six.

- To isolate those fields, we will use the following:

      cat Update1_Combined_Access_logs.txt | awk -F" " '{print $4, $6}'

- Lastly, we need to place these results into a file called `Update2_Combined_Access_logs.txt`:

      cat Update1_Combined_Access_logs.txt | awk -F" " '{print $4, $6}' > Update2_Combined_Access_logs.txt

