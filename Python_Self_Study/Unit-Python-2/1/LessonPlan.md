## 4.1 Lesson Plan: Reading and Writing to Files

### Overview 

In today's class students will start using Python on a more advanced scale, and will use it to write and read data to and from files. The goal is for students to feel comfortable in their ability to create simple applications that navigate through text files and perform a combination of the above actions. 

### Objectives 

By the end of class, students will be able to:

* Open and read text files using the the built-in `open()` function and `file.read()` method. 

* Use the `string.split()` method to break a string into smaller strings based upon specific string value parameters.

* Use `string.find()` method to determine if a string parameter can be found within a text.

* Create a command line application that searches for user-inputted words within a text file

* Read and search through CSV files for specific information

* Use the `open()` function with "w" parameter to write text to external files

* Use the “a” parameter within the `open()` function to append text to external files

### Instructor Notes

* This is a very fast paced class and the activities require that students use the concepts that they learned last week, including functions, loops, and conditionals.

* Review the activities before teaching the class. In many cases, the comments in the python script files provided for students will guide them through the code that they will have to write. Nevertheless, you may find that these exercises will still be challenging for students. 

* If you see students struggling, take a pause between the Direct Instruction and the Student Activities, and have simple drill practice to ensure that students understand the concepts being taught. 

* The slides provided mostly contain the Activity instruction. However, the slides also include a checklist of the day’s objectives. At key points, these objectives are displayed again with each objective that has been covered up to that point checked off. During these moments, ask students if they have any questions and use this time for review if needed. 

### Sample Class Video

* To view an example class lecture, visit: [Class Video](https://codingbootcamp.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=8122d12a-3282-4486-85d3-a99e0184f788).

### Slideshow

- The lesson slides are available on Google Drive here: [Advanced Python Day 1 Slides](https://docs.google.com/presentation/d/1a2ldowb88I-CZ2c_Lsg0m3sUKc79T_WBjnQHKRxtMuw/).

- To add slides to the student-facing repository, download the slides as a PDF by navigating to File > "Download as" and choose "PDF document." Then, add the PDF file to your class repository along with other necessary files.

- **Note:** Editing access is not available for this document. If you or your students wish to modify the slides, please create a copy by navigating to File > "Make a copy...".

----

### 01. Direct Instruction: Welcome Class (0:05)

* Welcome the class back to their second week of Python and do a quick recap of the building blocks that they covered last week: variables, operators, data types including lists and dictionaries, loops, conditionals, and functions. 

* Explain that today's focus will be on using Python to read and write data to and from files. At the end of today's class they will create a simple application that automatically navigates through text files and creates small reports based upon the information in them.

* Explain that the next two days will then introduce the class to some built-in Python modules: namely the System, OS, and ZipFile modules. The focus of these lessons will be upon navigating through and collecting metadata on the file system itself. Explain why this can be important in the context of cybersecurity 

* Let the class know that the skills they learn this week will be an excellent feather in their caps but that there is no shame in struggling with the concepts being taught. This material is hard - especially for new programmers. Let them know that it isn't necessarily a requirement for many entry-level cybersecurity positions, but it will certainly give them a leg up. 


### 02. Direct Instruction: Reading Text Files (0:10)

* Up until now, we've used the  `input()` function to get external data into our Python applications. This is a useful function when we need to collect only small amounts of data, but it can be difficult and unwieldy using it for scripts and programs where large collections of data would need to be entered into the command line. 

* To solve this problem, we can have scripts that were made to read through pre-existing external files in order to collect the desired information. This saves us lots of time and makes our applications more robust. 

* Open up both [Diary.txt](Activities/01-Ins_ReadingFiles/Diary.txt) and [ReadingTextFiles.py](Activities/01-Ins_ReadingFiles/ReadingTextFiles.py) within Visual Studio code so as to explain how a Python script is able to read data in from an external file.

  * The file, ReadingTextFiles.py, is the script file that we will use to read our Diary.txt file. In order to do this we will neeed to create a connection between the script file and the external file. 
  
  * We create that connection by using the built-in `open()` function in our script file. In the `open()` function  the relative or absolute path to the file is provided as a parameter.
   
   ```python 
   diary_txt_file = open("Diary.txt","r")
   ``` 

   * the ```"r"``` indicates that we will be reading the file.  Explain that the `open()` function always defaults to having an "r" for its second parameter if none is entered. This means that it isn't necessary that we include this when we want to open files to just read them. 
   
  * It is critical that we provide very precise directions on what path to follow in order to reach the desired file. Relative paths, therefore, have to be carefully constructed as navigation will start from the location of the script and must navigate to the file from there.

  * The `open()` function returns a file object we can save to a variable for use later on in the application. Attempting to print out this variable will only return some object data and will not provide any hints into what the file contains.

  * We then use the `file.read()` method to read through the text file and return a string version of its contents.
   
    ```python
    diaryText = diary_txt_file.read()
    print(diaryText)
    ```

  * While not always necessary, the connection to a file can be closed at any time using the `file.close()` method. Python gets tired running around opening files and reading them all the time, so try to give it a break and close the file to end the connection whenever you can. It is always good practice to close files and your computer's memory will thank you.
  
   ```python
   diary_txt_file.close()
   ```

* Answer any questions the class may have before moving onto the next activity.

### 03. Guided Practice: Reading Rainbow (0:15)

* In this activity, students will create a command line application that asks the user for a color. If this color has an associated file then the script will open up the file and print out all that it contains to the terminal.

* Send students the following files and instructions over Slack:

* **Files:**

  * [Unsolved](Activities/02-Stu_ReadingRainbow/Unsolved/Starter.zip)

* **Instructions:**

  * Extract the contents of `Starter.zip` to some location on your computer and do your work within the `ReadingRainbow.py` file that was included. Use the comments in `ReadingRainbow.py` to help guide your work.

  * Ask the user for a color and save their response to a variable.

  * Check to make sure that the color the user has entered has an associated file.
    
    * If there is a matching file, then create a connection to this file, read through its contents, and print them out to the terminal before closing the connection.

    * If there is no matching file, then simply print "No file associated with that color"

* **Hints:**

  * Look through the `Colors/` subfolder before creating your conditional so as to figure out what values you should be checking for.

  * Create one connection to one specific file/folder path before diving in and attempting to create a connection string that is different depending upon the value the user entered. i.e. your connection should be to the `Colors/` subfolder and not multiple connections to the individual files.


### 04. Direct Instruction: Reading Rainbow Review (0:05)

* Open up the [solved version](Activities/02-Stu_ReadingRainbow/Solved/ReadingRainbow.py) of the previous activity within Visual Studio Code and run through the solution whilst making certain to cover the following points.

  * There are a few different ways in which the conditional could be set up. The first is to create one large `if` statement which checks if the color entered matches any of the files using `or` operators. Another method would be to check each color individually using `if`, `elif`, and `else`. Neither is technically better than another but the first method is more concise.

  * The path to the file is constructed automatically by referencing the "Colors/" subfolder, adding the color inputted by the user and then appending ".txt" onto the end of the newly constructed path.

* Answer any questions the class may have before moving onto the next activity.


### 05. Direct Instruction: String Functions (0:10)

* Large blocks of text are not easy to work with. Due to their size, it is relatively difficult to uncover what is located where while also making it more challenging to extract pieces of information. This is where the `string.split()` method comes into play.

* Open up [StringMethods.py](Activities/03-Ins_StringMethods/StringMethods.py) within Visual Studio Code as a means to cover how strings can be split up and searched through.

 * Explain that we will continue to use the Diary.txt file but now we will introduce string methods to break down our text into smaller chunks. 

 * In our StringMethods.py we can see that we've opened the Diary.txt file and have used the `read` function to stringify the text. 
 
 * The `string.split()` function takes the original string provided and breaks it down into smaller chunks based upon whatever string value is passed into it as a paramether. These chunks are then placed into a list so that they can be more easily navigated through.

    * For example, `string.split(". ")` will return a list of strings where each new element was originally separated by a period followed up with a space.
  
  * While the `string.split()` method could theoretically be used in order to uncover whether or not a specific word or value could be found within a string, the `string.find()` method is much more adept at this.

    * The `string.find()` determines if the substring passed into it as a parameter occurs anywhere within the text the method is being run on.
    
    * If the substring is found within the original text, then it will return the index of the first occurence of that substring. The value of the index returned will be the character location where the substring began.

    * If the substring is not found within the original string, then a value of negative one (-1) is returned instead.

* Answer any questions the class may have before moving onto the next activity.

### 06. Guided Practice: Word Search (0:15)

* In this activity, students will create a command line application that looks into a specific file and then asks the user to enter a word. The application will then search through the file, find any instances of the word, and then print out how many times the word was found.

* Send students the following files and instructions over Slack.

* **Files:**

  * [Unsolved Files](Activities/04-Stu_WordSearch/Unsolved) 

* **Instructions:**

  * You are given a text file, and in your WordSearch.py file, create a function called `wordSearch()` which will take in a string as a parameter and will carry out the following tasks.

    * Opens up and reads the text contained within "Monologue.txt"

    * Searches through the text in order to uncover whether the string passed into `wordSearch()` can be found.

    * Prints out how many times the string passed can be found within the original text.

* **Hints:**

  * Whenever `string.split()` is used to discover how many instances of a string appear within a block of text, the length of the list returned by the method is always one greater than it should be.

  * Remember that you have to call a function in order to use it. Defining a function is never enough. 
  
  * The script file where you will write your solution has comments that guide you step by step through the code you will need to write. 

### 07. Direct Instruction: Word Search Review (0:05)

* Open up the [solved version](Activities/04-Stu_WordSearch/Solved/) of the previous activity within VS Code and run through the solution, making certain to cover the following points.

  * The "Monoglogue.txt" file is opened within the `wordSearch()` function. This means that any references to the file must be made from within the function or else they will be considered out of scope.

  * Point out that `string.find()` is not always perfect. This is because it is incapable of determining whether the substring the user is looking for is an independent word or just a couple of characters hidden within a word. This means that searching for "he" in the string "hello" would come back as true.

  * To deal with this, our code has added spaces before and after the word the user enters. While this ensures the word is on its own, it does come with some major drawbacks. For example, the first word in the monologue has no space before it and thus would not be findable. Also, words at the ends of sentences have periods after them and would not be found either. While this solution is not perfect, it will do for now and does prevent false-positives at the least.

  * In order to count how many times a word appeared within the original text, the string is split on the word that the user entered into the application. The length of the list is then collected and one is subtracted from it. This is because a split will always create two parts for the first match it finds and then one more for each after that. This means the length minus one will always give the program the correct number.

* Answer any questions the class may have before moving onto the next section.

### 08. Direct Instruction: Reading CSV Files (0:10)

* While plain text files can contain a decent collection of information within them, they can really become a hassle to work with due to how disorganized they tend to get. Thankfully there is a file type called a CSV that is far more organized and easier to work with using the methods we have covered thus far.

* Open up both [WWE-Data-2016.csv](Activities/05-Ins_ReadingCSV/WWE-Data-2016.csv) and [ReadingCSV.py](Activities/05-Ins_ReadingCSV/ReadingCSV.py) within VS Code to cover the following points.

  * First display the [WWE-Data-2016.csv](Activities/05-Ins_ReadingCSV/WWE-Data-2016.csv) file and explain that a CSV is essentially a text-formatted table. This means that each piece of data is stored within a specific column and row. In this particular case, each column is separated by a comma while each row has been placed on a new line.
  
  * Now switch to the [ReadingCSV.py](Activities/05-Ins_ReadingCSV/ReadingCSV.py) file. CSV files can be opened in exactly the same way text files can. The programmer simply needs to pass the path to the CSV into the `open()` function and save the file object returned to a variable. They can then read the file object in order to work with the contents of the file.

  ```python
  wrestling_csv = open("WWE-Data-2016.csv", "r")
  wrestling_text = wrestling_csv.read()
  ``` 
  * Since CSVs are separated into rows and columns through the use of unique characters, the programmer can use the `string.split()` function to break the data down into more manageable chunks. 

  * If there is an empty line at the end of the CSV file and you have used `.split(\n)` on a new line, point out that there will be a row at the end that is empty. In this case, we'll need to use the Python `.pop()` function which removes the last object from the list of rows. This will remove the last empty row from our list of wrestlers.

   * The first split is to break the original text into individual string versions of each new row by splitting on each new line.
   
   ```python
   wrestling_rows = wrestling_text.split("\n")
   wrestling_rows.pop()
   print(wrestling_rows[0])
   print(wrestling_rows[1])
   print(wrestling_rows[2])
   print(wrestling_rows[3])
   print("-----------")
  ```

   * Then they will split the contents of each row on each comma to get individual string versions of each column of each row.

    ```python
    wrestling_cells = wrestling_rows[0].split(",")
    print(wrestling_cells[0])
    print(wrestling_cells[1])
    print(wrestling_cells[2])
    print(wrestling_cells[3])
   ```

* Answer any questions the class may have before moving onto the next activity.

### 09. Guided Practice: The User List (0:20)

* In this activity, students are given a CSV file with usernames, passwords, and a list of IP addresses that the users are regulary connected to. They must read in the CSV, break it apart into parts, and then create a Python dictionary version of the CSV which can then be searched for specific user information.

* Send to students the following files and instructions to the class over Slack. 

* **Files:**

  * [UserList files](Activities/06-Stu_TheUserList/Unsolved/)

* **Instructions:**

  * In this activity, you have been given a CSV file with usernames, passwords, and a list of IP addresses that these users are regularly connecting to. Your job is to identify the users who are connecting to your company's private server and print out their information to the terminal. You will code your solution in the ReadUserList.py file. 

    * The company's private server is `229.62.232.190`

    * The user's information should be printed out in the following format:

      ```sh
      COMPANY PRIVATE SERVER FOUND
      USER: Ryan
      PASSWORD: QLeyzpdW
      HOURS ONLINE: 292
      COMMON IPs:
      248.150.250.24
      223.229.166.82
      229.62.232.190
      198.1.152.204
      215.252.4.108
      117.59.161.190
      169.59.2.142
      144.91.68.253
      27.127.60.188
      182.151.186.176
      ----------
      COMPANY PRIVATE SERVER FOUND
      USER: Clark
      PASSWORD: uUd2p3VH
      HOURS ONLINE: 282
      COMMON IPs:
      248.150.250.24
      223.229.166.82
      229.62.232.190
      198.1.152.204
      215.252.4.108
      117.59.161.190
      169.59.2.142
      144.91.68.253
      27.127.60.188
      182.151.186.176
      ----------
      ```

* **Hints:**

  * You will only need to split up the data once in order to uncover when a user has connected to the company's server but will have to perform two more splits when printing out the offending user's information to the screen.

  * Pay close attention to how each row and column is being kept separate within the original CSV file. This will give you a great idea on how you might go about splitting up the data using Python.
  
  * The comments in the script file will walk you step by step through the code you will need to write. 
  
### 10. Direct Instruction: The User List Review (0:05)

* Open up the [solved version](Activities/06-Stu_TheUserList/Solved\ReadUserList.py) of the previous activity within VS Code and run through the solution whilst making certain to cover the following points.

  * The original text is first broken into rows by splitting on each newline.

  * Each row is then looped through and a `string.find()` function is used to uncover whether or not the private server's IP address is located anywhere within the current row.

  * If the IP address is found, then the current row is broken into individual cells by splitting on each comma.

  * Since the fourth column in the CSV always contains a collection of IP addresses separated by semicolons, another split can be used in order to once again break the string apart into a list of individual IP addresses which can then be looped through and printed to the screen.

* Answer any questions the class may have before moving onto break.

-----

### 11. BREAK (0:15)

-----

### 12. Direct Instruction: Writing Files (0:10)

* Reading files is only half the battle since creating reports based upon on what was uncovered during an investigation is another major part of cybersecurity. This is when the process of writing files with Python becomes helpful.

* Open up [WritingFiles.py](Activities/07-Ins_WritingFiles/). Explain that we have an empty [text file](Activities/07-Ins_WritingFiles/MyPersonalDiary.txt) that we will be writing text to. Open up [WritingFiles.py](Activities/07-Ins_WritingFiles/WritingFiles.py) within VS Code and use the code to explain the following.

* Just as was the case with reading files, the `open()` function is used once again in order to write to files. This time, however, there is one striking difference in the inclusion of the "w" parameter after the file path.

  * This "w" stands for "write" and essentially lets the application know that the purpose of the file object being made will be to write new data into a file.

  * Remind students that the `open()` function always defaults to having an "r" for its second parameter if none is entered. 

  * It is critical to note that this method of writing files is somewhat dangerous, as the "w" mode for `open()` will cause any new lines passed to overwrite the original text that was inside of the file before the application opened it.

* In order to write some text into the file referenced, the `file.write()` function is used. Whatever string is then passed into the method as a parameter will be what is written to the external file.

  * When writing text into a file using the `file.write()` method, it is important to note how specific the programmer has to be in their syntax. If a newline is to be added to the file, then the programmer must use the `\n` newline character within their string.

  * There is no spacing added by default between multiple `file.write()` commands. If the user does want to add spacing between lines they would either have to program this functionality into the application themselves.

* Answer any questions the class may have before moving onto the next activity.

### 13. Guided Practice: Terrible Word Application (0:15)

* In this activity, students will create a command line application that allows them to write lines of text into an external file.

* Send the following file and instructions over Slack. 

* **[File](Activities/08-Stu_TerribleWordApp/Unsolved/TerribleWordApp.py)**

* **Instructions:**

  * You will need to create a text file called "Notes.txt." Then use the .py file provided to code your solution. 
  
  * Establish a connection to the external text file called "Notes.txt" and ensure that the mode of the connection is set to write.

  * Check if the user would like to add a new line of text into the external file that they connected to. You will need to use a `while` loop to accomplish this. 

  * Allow the user to write some text to the terminal using the `input()` function before writing this text into the external file the application is connected to.
  
* **Hint**

  * Use the script file comments to guide you step by step through the code you will need to write. 
  


### 14. Direct Instruction: Terrible Word Application Review (0:05)

* Open up the [solved version](Activities/06-Stu_TheUserList/Solved/ReadUserList.py) of the previous activity within VS Code and run through the solution whilst answering any questions the class may have.

### 15. Direct Instruction: The Append Mode (0:10)

* Remind students again that the write mode for `open()` overwrites whatever was originally stored within the connected text file. This is not exactly ideal when the application should simply be adding new information onto the end of the file. For this we can use the append mode. 

* Open up [AppendingText.py](Activities/09-Ins_OtherOpenModes/AppendingText.py) and take some time to go over the code contained with the class.

* The append mode is activated whenever the parameter "a" is passed into the `open()` function  which allows the application to add new text onto the end of an existing file, and essentially acts as a less destructive version of the write mode.

```python
notesFile = open("Notes.txt", "a")
```
  * Append does not overwrite the preexisting content. Instead it adds the new text being passed to the end of the original content.

  * As is the case with `file.write()`, spacing is not added between the preexisting content and the new content that is being added. As such, the programmer will have to manually add in the spacing desired if they want to style the external file.
  
```python
notesFile.write("\nThis is a completely new line of text created by the APPEND mode.")
```

* Through a combination of reading, writing, and appending, Python programmers can create complex applications that automatically take in data from one source and create reports in another. This allows them to automate a lot of processes that may otherwise take hours.

* Answer any questions the class may have before moving onto the final activity for the day.

### 16. Guided Practice: The Watchlist (0:20)

* In this activity, students will be creating a command line application that allows them to read through and update a company's watchlist of "dangerous" individuals from the terminal.

* Send students the following files and instructions over Slack.

* **[Files](Activities/10-Stu_TheWatchlist/Unsolved/)**

* **Instructions:**

  * You will create a command line application that allows its users to read through and add to a private company's watchlist of "dangerous" individuals.
  
  * The CSV file you have been given has four column categories: Name, Birth Year, Reason to Watch, Threat Level. You can see that there are two entries in there so far. 

  * Your application should accomplish all of the following.

    * Have a function that asks the user whether they would like to read the watchlist, write to the watchlist, or quit out of the application altogether.

    * Have another function that allows users to write new individuals into the watchlist. Each entry should have a name, a birth year, a reason for being on the list, and a threat level.

    * Have a third function that reads in each row from the watchlist and prints the data out one at a time to the terminal.

    * Loops until the user decides to quit out of the application.

* **Hints:**

  * This is not an easy activity, so feel free to work with some of the people around you to find a solution.

  * The script file comments provide the high level outline of how you should write your code solution. 
  
### 17. Direct Instruction: The Watchlist Review (0:10)

* Open up the [solved version](Activities/10-Stu_TheWatchlist/Solved/TheWatchlist.py) of the previous activity within Visual Studio Code and run through the solution whilst answering whatever questions the class may have.
