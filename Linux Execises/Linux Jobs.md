## Foreground
This command will run a job in the foreground.
- `sleep 60`

## Background
Append & to a command to execute it in the background.
- `sleep 200 &`

Use the jobs command to view all the jobs running in the background.
- `jobs`

After 200 seconds, the job above this job will no longer be in the running status.
You can send a running job from the foreground to the background with **Ctrl+z**.
- `sleep 50`
# now enter Ctrl+z

Then view the jobs.
- `jobs`

Notice that the status for the sleep 50 job is stopped. This is like pause.
There is a summary of the job status definitions at the end of this file.

To start the last job in the background, use the bg command.
- `bg`

If you have more than one job, you can use the job number with bg to start a job.

``` sleep 100
# now enter Ctrl+z

sleep 200
# now enter Ctrl+z

sleep 300
# now enter Ctrl+z `
```
jobs
# prints something similar to
#[1]   Stopped                 sleep 100
#[2]-  Stopped                 sleep 200
#[3]+  Stopped                 sleep 300

# The numbers in brackets are the job number. For instance, job number 2 is the sleep 200 command.

To start job number 2, run the command below.

bg 2

Note that on some shells you may need to use %2. You should always use % with the bg and fg commands when referring to job numbers.

To start jobs 1 and 3, use the following:

bg 1 3

A job can be terminated if it is stopped or running. To terminate a job, use the kill %(job number) command:

# kill job number 1
kill %1

# kill job number 2 and 3. 
kill %2 %3

A job can be brought back to the foreground if it is stopped or running. Use the fg command and job number.

sleep 200 &
# [1] 190885 # This is job number 1
fg 1

Screen

screen is a terminal multiplexer that allows you to run multiple terminal sessions within a single terminal window or SSH session. You can run commands in screen sessions, log out, and then enter the sessions again, unlike jobs. There are other tools, such as nohub or tmux, but screen is widely available.

Use the screen command to start a screen session.

screen

Next, run the command below, then press Ctrl+a and d to exit the screen.

while true; do echo "screen 1..."; sleep 5; done
# To exit this screen press Ctrl+a, then d

Do it again with another screen session, and exit.

screen
while true; do echo "screen 2..."; sleep 5; done
# To exit this screen press Ctrl+a, then d

Now list your screen sessions.

screen -list
# There are screens on:
        # 221271.pts-0.ip-172-31-24-77    (Detached)
        # 193073.pts-1.ip-172-31-24-77    (Detached)

In this example, we want to enter the second screen we created above, 193073.

exit
# log back, make sure the numbers match the results of screen -list
screen -r 193073
# Ctrl+a, d
screen -r 221271
#Ctrl+a, d

To close out a screen session, use the -X flag to run the quit command.

# do this for your screen sessions.
screen -X -S 193073 quit

Conclusion

In this activity, we looked at scheduling in Linux. Jobs can be sent to the background so that the foreground can still be used.

If you are worried about a job taking a long time to execute, consider putting the job in its own screen so you can safely log out and check on that job later.
Job Statuses

    Running: This status indicates that a job is currently actively running in the foreground or background.
    Stopped: A job might be stopped if it was suspended, usually by pressing Ctrl+Z. A stopped job is one that has been paused and is not currently executing.
    Exited: When a job completes its execution, it will have an "Exited" status. This means that the process associated with the job has finished running.
    Terminated: A job might have a "Terminated" status if it was forcefully terminated, usually by sending a termination signal (like Ctrl+C).
    Background: This status indicates that a job is running in the background and not currently in the foreground.
    Foreground: While not always explicitly mentioned as a status, a job in the foreground is actively running and has control over the terminal.
