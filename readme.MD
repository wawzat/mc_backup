# Three bash scripts for backing up minecraft worlds on Linux based servers. 
# The other bash scripts were used to test code that was used in the main script but may have some utility.
# The scripts are all stand-alone and do not depend on one another.
  
# backup_mc_daily
 
## Bash script used to backup minecraft world files.

### Notes:
 
- Modify the configuration variables in config.yml according to your needs and directory structure.
- The script is designed to be run as a cron job.
- Set USE_RCLONE="False" if you don't want to use rclone to also copy the files to a cloud storage provider. To use rclone you must first have it installed and configured.
- Use the -f command line argument to force a backup even if the most recent backup is newer than the most recent player play session.
- Server world folders need to be prefixed with "world" (i.e. world, world_nether, world_the_end, etc.) otherwise the script will not find them.
- Requires the use of "screen" to run the minecraft server. Screen must be named "mc" for the script to work.
-  Sample steps to start screen and launch minecraft server (modify the java command as required for your server):
1. > screen -S mc
2. > cd /home/mcserver/minecraft/
3. > java -Xms12288M -Xmx12288M -XX:+UseG1GC -jar spigot-1.20.jar nogui
- The script searches the log files and determines which players have joined the game at least minimum_plays number of times and when they last joined.
- It compares the last time a player left the game to the dates of the backup files and if the backup is less recent it backs up the world files.
- Sample cron entry: 0 10 * * * /home/mcserver/minecraft/mc_backup/backup_mc_daily runs the script at 10:00 AM every day. 
  
 
# backup_mc_1st and backup_mc_15th
  
## Bash scripts that backup on the 1st and 15th of the month
  
### Notes:

- These scripts are used to backup the minecraft world files on the 1st and 15th of the month.
- They copy one of the daily backup files to a monthly backup file.
- Sample cron entries:
- 0 9 1 * * /home/mcserver/minecraft/mc_backup/backup_mc_1st runs the script at 9 am on the 1st of the month.
- 0 9 15 * * /home/mcserver/minecraft/mc_backup/backup_mc_15th runs the script at 9 am on the 15th of the month. 


# extract_player_minimums

## Bash script that extracts the names of players from the logs that have joined the game at least minimum_plays number of times.  

### Notes:  

- This is an intermediate script that was used to test code that was used in backup_mc_daily.
  
  
# extract_player_names
  
## Bash script that extracts the names of all players from the logs along with the number of times they've joined.
  
### Notes:
  
- This is an intermediate script that was used to test code that was used in backup_mc_daily.  
  