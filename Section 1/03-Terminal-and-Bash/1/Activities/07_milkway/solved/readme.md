### Solution Guide: Finding your Milky Way

- First, navigate into the `students` folder on your VM using an absolute path. To do so, run the following command:

         cd /root/student/take_5


- Create an additional folder called      `Internal_Investigation_Employee_B`:
    
          mkdir Internal_Investigation_Employee_B
    
-  To confirm the folder was created, run:
    
          ls
          
- Move the file `email_evidence` from `Internal_Investigation_Employee_A` to `Internal_Investigation_Employee_B` using absolute paths:

      mv /root/student/take_5/Internal_Investigation_Employee_A/email_evidence /root/student/take_5/Internal_Investigation_Employee_B/

- Copy the file `log_evidence` from `Internal_Investigation_Employee_A` to `Internal_Investigation_Employee_B`:
   
      cp /root/student/take_5/Internal_Investigation_Employee_A/log_evidence /root/student/take_5/Internal_Investigation_Employee_B/
    
- Navigate to the directories to confirm the files have been copied and moved correctly.

  - To check the `Employee_A` directory, run: 

        cd /root/student/take_5/Internal_Investigation_Employee_A/
        ls
        
    Since we moved the `email_evidence` file, the only file that should remain is `log_evidence`. 
           
  - To check the `Employee_B` directory, run: 

        cd /root/student/take_5/Internal_Investigation_Employee_B/
        ls
        
    The existing files should be `log_evidence` and `email_evidence`.
