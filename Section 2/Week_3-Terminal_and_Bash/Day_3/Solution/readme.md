### Warmup Solution


- Explain that the first step is to navigate into the "/student_day3/warmup" folder on your VM
- To complete this, run the following commands
 
       cd student_day3
       cd warmup
       
- Begin with creating a folder called "subpoena_request"  

       mkdir subpoena_request
       
- Next, find the files dated 0719

     Run the following command:   `find -type f -iname *0719*`
     
     This will return the following 2 files:
     
       ./WEBACCESS/0719Apache
       ./WEBACCESS/IIS_0719

- Explain that next, we will Move the files into the subpoena_request folder, using a wildcard

       mv ./WEBACCESS/*0719* ./subpoena_request/
            
 - Explain that next we will get the phone records that show calls made to Slugworth's number:  454-555-3894, and place them in a file called: Calls_to_Slugworth
 
   Run the following command: `grep 454-555-3894 ./PHONE_LOGS/* > Calls_to_Slugworth`
   
- Explain that for the last step, we will Move the file into the subpoena_request folder

       mv ./PHONE_LOGS/Calls_to_Slugworth ./subpoena_request/   

        
## Bonus

- Explain that in the file we created called: "Calls_to_Slugworth", are the following 3 "From" phone numbers
  - 212-555-2732
  - 212-555-2733
  - 212-555-2734

- Explain that to look up the owners of these three phone numbers, we will run the following to look up all three phone numbers:

      `grep '212-555-2732\|212-555-2733\|212-555-2734' ./DIRECTORIES/*`
      
- Point out the results show the the following:

        212-555-2734    Mr GoodBar
        212-555-2732    Ruth
        212-555-2733    Henry
       
- Explain that it looks like Mr. Goodbar has also been in contact with Slugworth       


