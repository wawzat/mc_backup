# A collection of bash scripts for backing up minecraft worlds and reviewing logs. The scripts are all stand-alone and do not depend on one another.
  
# backup_mc_daily
 
## Bash script used to backup minecraft world files.

### Notes:
 
- Modify the configuration variables at the top of the script according to your needs and direectory structure.
- The script seraches the log files and determines players who have joined the game at least num_plays number of times and when they last joined.
- It compares the most recent join to the date of the backup file and if the backup is less recent it backs up the world files.
- Sample cron entry: 0 10 * * * /home/mcserver/minecraft/mc_backup/backup_mc_daily runs the script at 10:00 AM every day. 
  
 
# backup_mc_1st and backup_mc_15th
  
## Bash scripts that backup on the 1st and 15th of the month
  
### Notes:

- These scripts are used to backup the minecraft world files on the 1st and 15th of the month.
- They copy one of the daily backup files to a monthly backup file.
- Sample cron entries:
- 0 9 1 * * /home/mcserver/minecraft/mc_backup/backup_mc_1st runs the script at 9 am on the 1st of the month.
- 0 9 15 * * /home/mcserver/minecraft/mc_backup/backup_mc_15th runs the script at 9 am on the 15th of the month. 


# extraact_player_minimums

## Bash script that extracts the names of players from the logs that have joined the game at least num_plays number of times.  

### Notes:  

- This is an intermediate script that was used to test code that was used in backup_mc_daily.
  
  
# extract_player_names
  
## Bash script that extracts the names of all players from the logs along with the number of times they'be joined.
  
### Notes:
  
- This is an intermediate script that was used to test code that was used in backup_mc_daily.  
  