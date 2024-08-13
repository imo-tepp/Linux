# Using Vi

## Part 1: Avengers
1) Open a new file named avengers in your home directory in your editor and paste in the following text:
Use `touch avengers` & `vi avengers` first
```
Six stones, three teams, one shot. Five years ago, we lost. All of us. We lost friends. We lost family. We lost a part of ourselves. Today, we have a chance to take it all back. You know your teams. You know your missions. Get the stones. Get them back. One round trip each. No mistakes. No do-overs. Most of us are going somewhere we know. that doesn't mean we should know what to expect. Be careful. Look out for each other. This is the fight of our lives, and we're gonna win. Whatever it takes. Good luck.
```
2) Exit and save the file
- `:x!` or `:wq`

3) Run a word count on the file
- `wc -w avengers`

4) Edit the file to add a blank line and type in "word count" followed by the value you just got.
- `vi avengers` then paste the value

5) Now use search and replace within the editor to replace every instance of the word the with THE. Ensure that you only catch the word the and not words that contain the letters the (like them).
- `:%s/\<the\>/THE/g` to replace the words

6) Copy the first line of the file and paste it after your word count entry at the bottom of the file.
- Make sure you're in command mode first. press `ESC` if you see *INSERT* at the bottom of the terminal
- Use `Ctrl + v` to enter block mode and highlight the first line. Press *Y* to copy the line.
- Position the cursor at the bottom of the file, press *P* to paste before or press *p* to paste after the cursor

7) Delete the first line of the file.
- `Ctrl + v` to highlight the line
- `dd` or `D` to delete the line

8) Undo that deletion.
- press `u` to undo the deletion

9) Insert at the top of the file the text "Captain America – Endgame" followed by an empty line.
- Enter Insert mode by pressing `i`
- Navigate to the top of the file, then type it out.

10) Save the changes and exit the editor
- `:x!` to quit and save the changes

11) Find out the number of lines in the file now
- `wc -l avenger` : check the number of lines (Remember the original paragraph pasted count as one line)

12) Write the number of lines into the file one line above the word count with the text "line count" plus the value.
- `vi avenger` and type the value in using insert mode.

13) Delete "Good luck" wherever it occurs in the file.
- `:%s/Good luck//g` to delete Good luck.

14) Save and exit the file.
- `:x!`


## Part 2: Log Files

### Pre-Requisite
Run the fixGenerator.sh script again from your home directory using the following commands:

```
cd ~
./fixGenerator.sh &
```

### Exercise
1) Run a search for all new order singles in the fix log output and put the output of that search into a file named newOrders.log in your home directory.
- `grep -n "35=D" <fixlogfilename> > newOrders.log`

2) Open newOrders.log in your editor
- `vi newOrders.log`

3) Duplicate the first line and fifth line in the file
- *Ctrl + v* (block mode), highlight the line then press *y* to copy it
- Enter Insert mode *i* to create a new line underneath , exit *ESC* the insert mode
- press *p* to paste the line

4) Find and replace every instance of MTHREE with M3.
- `:%s/MTHREE/M3/g`

5) Find and replace every ; (semicolon) with a , (comma) and ensure there is no space after the commas.
- `%s/;/,/g` (eplace semicolon with comma)
- `%s/\s\+//g` (remove the space after the comma)

6) Save and exit the file
- `:x!`

7) Rename your file to *.log* and save it in the directory specified by the instructor
Run the following command on the local computer with git bash.
- `scp -i "Keypair.pem" ubuntu@ec2-16-171-129-65.eu-north-1.compute.amazonaws.com:/home/ubuntu/newOrders.log .`