## Terminal Homework: ♣♦♠♥ A High Stakes Investigation ♣♦♠♥!

### Scenario

You have just been hired by Lucky Duck Casino as a security analyst.
 
 - Lucky Duck has been experiencing a significant loss of money on the roulette tables over the last month.
 
 - More specifically, the largest losses occurred on March 10th, 12th, and the 15th.

 - Your manager believes there is a player working with a Lucky Duck dealer to cheat at roulette.
 
 - The casino contains a vast database containing data on wins and losses, player analysis and dealer schedules.
 
You are tasked with navigating, modifying, and analyzing these data files in order to provide evidence that can implicate the fraudulent player and dealer.
 
 - You will prepare several evidence files to assist with prosecution of the casino player and the rogue dealer.
 
 - You must work quickly as Lucky Duck can't afford any more losses!


### Files Required 

Lucky Duck Casino has provided you with the following files:

  - [Win/loss player data from the roulette tables during the week of March 10th](Resources/Roulette_Player_WinLoss_0310.zip)
  - [Employee Dealer schedule during the week of March 10th](Resources/Dealer_Schedules_0310.zip)


### Your Objective 

Utilize your command line skills to determine who is the Casino Cheat and Rogue Roulette Dealer colluding to scam Lucky Duck out of thousands of dollars!

After your investigation you will provide the following:

- A summary of your findings for each step.
- A conclusion of your findings to provide to the authorities.

### Topics Covered in This Assignment

- Making directories
- Previewing files
- Making and editing files with touch and nano
- Counting data with wc
- Navigating Through Directories
- Using grep to search through files
- Using awk to isolate out data
- Redirecting and appending data into files
- Designing a Shell Script
- Using Arguments in a Shell Script

Let's get started!

---

## Lucky Duck Security Investigation Instructions

### Step 1: Investigation Preparation

Your first task is to set up directories to prepare for your investigation.

- Begin by making a single directory titled `Lucky_Duck_Investigations`.

- Next, within this directory of `Lucky_Duck_Investigation`, create a directory for this specific investigation titled `Roulette_loss_Investigation`.

- Within `Roulette_loss_Investigation`, create the following directories:

  - `Player_Analysis` to investigate the Casino Player.
  - `Dealer_Analysis` to investigate the Dealers.
  - `Player_Dealer_Correlation` to summarize your findings of the collusion.

- Create empty files called `Notes_<Directory Name>`  under each of those subdirectories to be used later to add in any investigation notes.

  - For example: `Notes_Player_Analysis`, 


### Step 2: Gathering Evidence

Your next task is to move evidence from the specific days Lucky Duck experienced heavy losses at the roulette tables. 

 - The following [files and directories](resources/Roulette_Player_WinLoss_0310.zip) contain the win/loss player data from the roulette tables during the week of March 10th.
  
   - Since the losses occurred on March 10th, 12th, and 15th, move those files into the directory `Player_Analysis`.
 
 - The following [files and directories](resources/Dealer_Schedules_0310.zip) contain the employee schedules for all of Lucky Duck's tables during the week of March 10th.
 
   - Since the losses occurred on March 10th, 12th, and 15th, move the schedules for those days into the directory `Dealer_Analysis`


### Step 3: Correlating the Evidence

Your next task is to correlate the large losses from the roulette tables to the dealer schedule in order to determine the dealer and player that are likely colluding to steal money from Lucky Duck.

 - *Note: Any winnings for Luck Duck Casino are indicated with a positive number and any losses are a negative number.*

Complete the following tasks:

#### Player Analysis

- Navigate into the `Player_Analysis` directory.

- Use `grep` to isolate out all the `losses` that occurred on March 10th, 12th, and 15th.

- Place those results into a file called `Roulette_Losses`.

- Preview your file `Roulette_Losses` and analyze the data.

- Then, document in the `Notes_Player_Analysis` file:

  - The Times the losses occurred on each day.
  - If there is a certain player that was playing during each of those times.
  - Total count of times this player was playing.
    - Hint: Use the `wc` command for this value.
   
     
#### Dealer Analysis   

- Navigate into the `Dealer_Analysis` directory.

- This file contains the Dealer schedules for the various Lucky Duck casino games: `Blackjack`, `Roulette`, and `Texas Hold 'Em`.

- Preview the schedule to view the format and how the data is separated.

- Using your findings from the Player Analysis, create a **separate script to look at each day and each time** that you determined  losses occurred. Use `awk`, `pipes`, and `grep` tp isolates out the following four fields:
  - Time
  - AM/PM
  - First Name of Roulette Dealer
  - Last Name of Roulette Dealer

- For example, if there was a loss that occurred on `March 10th at 2 PM`, you would write one script that found the Roulette Dealer that was working at that specific day and time. 
  - *Hint: you will have many scripts, but only a small change is needed in each script.*


- Run all of the scripts and append those results into a file called `Dealers_working_during_losses`.

- Preview your file `Dealers_working_during_losses` and analyze the data.

- Document in the `Notes_Dealer_Analysis` file: 

  - The primary dealer that was working the times the losses occurred.

  - How many times the dealer worked when major losses occurred.

#### Player/Employee Correlation

  - In notes file of the `Player_Dealer_Correlation` directory, add your summary of the player and dealer you believe are colluding to scam Lucky Duck. 
  
  - Make sure to document your specific reasons for this finding.

 
### Step 4: Scripting your Tasks


You manager is impressed with the work you have done so far on the investigation.  

  - Your manager has tasked you with building a shell script that can easily analyze future employee schedules. Therefore, we can determine who was the employee working at a specific time in case losses occur again.

  - This shell script can be provided to anyone in the security department to easily do the same analysis.

Complete the following tasks:

   - Remain in the  `Dealer_Analysis` directory.

   - Develop a shell script called `roulette_dealer_finder_by_time.sh` that can analyze the employee schedule to easily find the Roulette Dealer at a specific time.

      - *Hint: You will be using a script similar to the one you created for "Dealer Analysis", except do not output the results into a file.*

   - Design the shell script to accept the following two arguments:
     - One for the date (Four Digits)
     - One for the time
    
     Note: The argument should be able to accept AM or PM.
   
   - Test your script on the schedules to confirm it outputs the correct dealer at the time specified. 

**Bonus:**  In case there is future fraud on the other Lucky Duck Games, create a shell script called `roulette_dealer_finder_by_time_and_game.sh` that has the three following arguments:

   - One for the the specific time
   - One for the specific date
   - One for the casino game being played
    
     *Hint: The argument does not need to name the specific casino game.*

 
### Your Submission

#### Guidelines for your Submission:
  
Move the following to the `Player_Dealer_Correlation` directory:
  - All of your note files
  - Your Evidence Files:
    - `Roulette_Losses`
    - `Dealers_working_during_losses`
  - Your Shell script(s)


Submit your findings!

Homework Complete, Great Job!

---

© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.

