## Pre-Requisite
Need to install cron on the EC2 instance before doing the exercise.

```
sudo apt update
sudo apt install cronie
sudo systemctl start cronie
sudo systemctl enable cronie
sudo systemctl status cronie
```

Ensure the fixGenerator.sh script is installed in your home directory.
## Scheduling Exercise
1) Set up the script to run Monday–Friday at 6am.
- `0 6 * * 1-5 ~/fixGenerator.sh`
2) Set up the script to run at 6pm every Friday.
- `0 18 * * 5 ~/fixGenerator.sh`
3) Set up the script to run every half hour from 9–4 on Monday, Wednesday, and Friday.
- `*/30 9-16 * * 1,3,5 ~/fixGenerator.sh`
4) Set up the script to run every other hour every day.
- `0 */2 * * * ~/fixGenerator.sh`
5) Set up the script to run on May 4th at midday.
- `0 12 4 5 * ~/fixGenerator.sh`
6) Set up the script to run on the 1st of every month at 6:25am.
- `25 6 1 * * ~/fixGenerator.sh`
7) Set up the script to run every 20 minutes every Tuesday between 10am and 2pm.
- `*/20 10-14 * * 2 ~/fixGenerator.sh`
8) Set up the script to run the 1st of every other month on the hour.
- `0 * 1 */2 * ~/fixGenerator.sh`
9) Set up the script to run at 6am and 8am on Saturday and Sunday.
- `0 6,8 * * 6,7 ~/fixGenerator.sh`
10) Copy the contents of your crontab into a file and save it to a folder named "scripts" in your home directory.
- `:w schedule.txt` then move the file to the scripts folder by `mv schedule.txt scripts/`