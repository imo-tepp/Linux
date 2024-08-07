# Pre-requsite
Get the FixGenerator script from the repo

`wget https://github.com/TheAcademy/pss-orderbook-deploy/blob/main/src/linux_activities/fixGenerator.sh`

`chmod +x fixGenerator.sh`

`./fixGenerator.sh &` (Runs the script and creates a logfile) 

# Exercise
1) Create a directory named logs.

`mkdir logs`
2) Move the log output from the fixGenerator script into the logs directory. (Be sure the script has finished before doing this.)

`mv <logfilename> logs`
3) From the command line, replace all instances of WILEYEDGE in the file with EDGE and put the output into a new file named fixlog2.log in the logs directory.

`sed -i 's/MTHREE/EDGE/g' fixlog2.log`
4) Run a command to pull all fill messages from fixlog2.log and put the output into a new logfile named fills.log. (You may need to look up how to tell if a message is a fill.)

`grep -n "35=8" fixlog20240806124758.log > fills.log`
5) Run a command to pull all cancel acknowledgement messages (39=4) from fixlog2.log into a new log named cancels.**log in the same directory.

`grep -n "39=4" fixlog20240806124758.log > cancels.log`
6) Run a command to create a new log file named partialFills.**log and add the partial fills from fills.log to the new file.

`grep -n "150=1" fills.log > partialFills.log`
7) Use awk to create a new file out of the partial fill log.
- The new file should include only the following tags: Symbol (55); orderID (11); side(54); fill price (31); fill quantity (32); execution id (17).
- Name the file parsedPartialFills.log and make sure you print the columns in the order listed here.

`awk '{print $7, $9, $13, $10, $15, $16}' partialFills.log > parsedPartialFills.log`
8) Use an editor to remove the first part of every fix tag (so you are left with the value only) and turn the file into a comma-separated list with no spaces. This is how you might have to get a file ready to send to a trader.

`vi parsedPartialFills.log` (Open the Vi editor)

`:%s/<fix tag>//g` (Remove all fix tag)

`:%s/\s//g` (Remove all white space)
9) In the file, add a row of column headers separated by commas. The headers should be Symbol, OrderID, Side, Price, Qty, and ExecID.

`vi parsedPartialFills.log` (Manually added the column headers in vi editior)
10) Save the file as .module10.csv in your home directory.

`mv parsedPartialFills.log ~/.module10.csv`
11) Make a copy of the cancels file and name it cancels2.log.

`cp cancels.log cancels2.log`
12) Open the cancels2.log file in an editor. Find the first symbol (tag 55) in the first line and add the letter A to the beginning of the value. For example, if the symbol was originally 55=GOOG, it will become 55=AGOOG.

`vi cancels2.log` (Open cancels log in vi editior)

`:%s/55=/55=A/g` (Replace all occurance of 55= with 55=A, effectively adding an A in front)
13) Run a difference between the original cancels file and the new file you just edited.

`diff -y cancels.log cancels2.log`
14) Now run the history command and put it into an output file named name.YYMMDD.module10 in your home directory.

`history > Imran.240806.module10`

`mv Imran.240806.module10 ~/`