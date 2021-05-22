## 4.3 Lesson Plan: More with Python Modules

### Overview

This lesson continues exploring more functions within the `os` module including those that return and parse a file's metadata. We'll quickly touch on how to remove files from a file system, and then move on the `zipfile` module. Class will culminate in student's building a random password generator application. 


### Objectives

By the end of class, students will be able to:

   * Return a file's metadata using the `os.stat()` function 
   
   * Use functions to get file size, when it was last accessed, and when it was last modifed
   
   * Convert dates and times from one format to another using the the `datetime` module.
   
   * Remove files from a system using the `os.remove()` function.
   
   * Extract zip files using the `zipfile` module.

### Instructor Notes

* Today's class is very activity focused and the activities are fairly challenging. Though we don't cover too many new concepts, students may find them difficult. Take your time with each concept, do some drill activities if you can, and even provide some of the code for the activities as a way to get struggling students started.

* If you feel that the class needs review, then feel free to skip the last activity to focus on that. Send the activity to students as a supplemental activity, or for those who will struggle with homework, let them know that they can submit this one instead. 

### Sample Class Video

* To view an example class lecture, visit: [Class Video](https://codingbootcamp.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=846a192f-ae17-44b8-ad09-a9a701814cfc).

### Slideshow

- The lesson slides are available on Google Drive here: [Advanced Python Day 3 Slides](https://docs.google.com/presentation/d/1raSF5LaRG-3pe1qH3iu4f5SF-GaZqB4pCQYV4NTMTcU/)

- To add slides to the student-facing repository, download the slides as a PDF by navigating to File > "Download as" and choose "PDF document." Then, add the PDF file to your class repository along with other necessary files.

- **Note:** Editing access is not available for this document. If you or your students wish to modify the slides, please create a copy by navigating to File > "Make a copy...". 

---

### 1. Direct Instruction: Welcome the Class (0:05)

* Take a few moments before class begins to remind students how much they have accomplished. Two weeks ago, most of them had no idea how to run a Python script. And now students have the skills to create and run small programs that speed up and automate some of the processes cybersecurity professionals might face. 

* Let students know what the goal of these past two weeks is:

    * While knowing Python is a huge advantage in the cybersecurity world, simply being able to recognize and understand conceptually what's happening in your programs and code is sufficient. Remind students that they won't be expected to code as a cybersecurity professional and we don't expect anyone to emerge from this program knowing how to code Python, but we do include these coding exercises as a way to get you familiar with Python's language and syntax and its uses.  To understand how to protect others against malicious code, one first has to understand how code works.

* Let students know that today will conclude their in-depth work with Python. We'll spend the first part of the day looking at some more features of the `os` module. We will work on small programs to help us practice everything we've learned so far. And lastly, we'll explore the `zipfile` module and build an application that ties in a lot of things we've learned together. 

* Let's start with a warm-up activity to get everyone back into the programming mindset.

### 2. Guided Practice: Walking the Maze (0:15)

* In this activity, students will create a script that automatically navigates through a complex web of folders to discover the files that it contains before printing those files to the screen.

* Send students the following files and instructions over Slack:

    * **Files:** 
        * [TheMaze.zip](Activities/01-Stu_WalkingTheMaze/Unsolved/TheMaze.zip)
        
        * [Script File](Activities/01-Stu_WalkingTheMaze/Unsolved/WalkingTheMaze.py) 
        
    * **Instructions:** 
    
        * Unzip TheMaze.zip.
        
        * Create a Python application that automatically navigates through **TheMaze** folder that you have been given.
        
        * When you find a file within TheMaze folder, print the location of this file to the screen alongside the contents of that file.
        
        * We've provided a lot of the solution code for you in the solution file, and the comments should guide you the rest of the way.

### 3. Direct Instruction: Walking the Maze Review (0:05)

* Open the [solved version](Activities/01-Stu_WalkingTheMaze/Solved/WalkingTheMaze.py) of the activity in VS Code. Explain the following points:

    * Students have likely discovered how similarly `os.walk()` works inside of any application. In fact, the code could easily be copied and pasted with only minor modifications to make here and there.
    
    * The `os.walk()` function will only open files that it finds. This means that we don’t need to use the  `os.path.isfile()` function we learned about previously to check if a file exists, because `os.walk()  `essentially does that for us by only opening files that do exist in the directory.

* Answer any questions the class may have before moving to the next activity.

### 4. Direct Instruction: File Statistics (0:08)

* One of the most critical aspects of working with files comes in the form of their metadata. Metadata contains information, including file type, file size, file source, and even information such as when the file was last accessed.

    * When investigating potential security issues, file metadata is important because it can provide clues about suspicious activity.
    
    * For example, if a single file out of hundreds is significantly larger than the rest, it could potentially contain malicious code that could harm the computer or actively spy on the network.
    
    * During investigations for ransomware, you may look for certain file types (e.g. `.sam`, `.enc`, etc.) or identify a large number of files modified soon after.

* Open [FileStats.py](Activities/02-Ins_FileStats/FileStats.py) in VS Code. 

    * Review the top portion of the code as students should be comfortable with it already.
    
    ```python
    import os

    file_path = os.path.join("Resources", "SomeCoolStuff.txt")
    ```

    * The `os.stat()` function takes in a file as a parameter and returns an object that contains metadata on that file. In the example, we're saving this object into a variable. `statInfo`
    
      ```statInfo = os.stat(file_path)```
    
    
    * Once we have all of the metadata, we’ll want to get more specific information and for this we’ll use dot notation. 

        * For example, if we wanted to know the file size in bytes, we would use `file.st_size`.
        
        ```statInfo.st_size```
       

        * If we wanted to know when the file was last accessed or opened, we use `file.st_atime`.
        
        ```statInfo.st_atime```

        * If we wanted to know the time when the file was last modified, we use `file.st_mtime`.

    * You might notice that time values are being returned in a format known as Unix Epoch time. This format is based on a counter that has been going up by one every second since 00:00:00 Coordinated Universal Time (UTC), Thursday, January 1, 1970.

        * While that is an interesting way to note time, it is difficult for the average user to understand. Thankfully we can use the `datetime` module to convert dates and times from one format to another. 
        
        * For this class, we will only focus on the `datetime.datetime.fromtimestamp(TIMESTAMP).strftime('%c')` function that takes in Unix Epoch time and converts it into a readable date. 
        
        * This formatted date will include the day of the week, the month, the day of the month, the time in military format, and the year. **Example:** Thu Oct  4 15:01:36 2018
        
* Answer any questions the class may have before moving to the next activity.

### 5. Direct Instruction: Working with the OS (0:02)

* Continue with the file from above [FileStats.py](Activities/02-Ins_FileStats/FileStats.py)

* If you want to run operating system commands from within your Python script, you can use the `os.system()`:

    ```os.system("dir")```
    
    * The os module provides a way to check for your read/write access to files.

    ```
    # Do I have read access?
    os.access("FileStats.py", os.R_OK)

    # Do I have write access?
    os.access("FileStats.py", os.W_OK)
    ```

* Answer any questions the class may have before moving to the next activity.

### 6. Guided Practice: Searching the Red Flag Sea (0:25)

* In this activity, students are going to write a script that searches a folder for any files that seem out of place.

* Send students the following files and instructions over Slack:

    * **Files:** 
      * [Text.zip](Activities/03-Stu_SearchRedFlagSea/Unsolved/Text.zip) 
      * [Script file](Activities/03-Stu_SearchRedFlagSea/Unsolved/RedFlagSea.py) 

    * **Instructions:**

       * Unzip **Text.zip**.

       * In this activity, you're going to write a script that searches a folder for any files that seem out of place. All of the files should be the same size and have been modified around the same time, but some may have had some additional changes made to them and they should stand out. 

       * Write a Python script that reads through all of the files in the `Text` folder. The script should print out a line that looks like the following for each file:

           * `File Path (folder\name), File Size in Bytes, Last Modified Date.`.
            
           * **Example:** `Text\zrJ1cdXhuZOB, 100, Sun Jul 29 10:55:57 2018`
      
         * We've provided a lot of the solution code for you in the solution file, and the comments should guide you the rest of the way.

### 7. Direct Instruction: Searching the Red Flag Sea Review (0:05)

* Open the [solved version](Activities/03-Stu_SearchRedFlagSea/Solved/RedFlagSea.py) of the previous activity in VS Code and use it as a guide to cover the following points.

    * Since there are so many files within the **Text** folder, it makes more sense to use an `os.walk()` to loop through the files than it does to manually collect all of the file paths.

    * The `os.stat()` function is used to collect all of the metadata on the current file and save it to a variable.

    * The time modified data is stored within the `file.st_mtime` value but must be converted from the unix epoch timestamp in order to become readable. This reformatting of the stamp can be done using the `datetime.datetime.fromtimestamp(timeModified).strftime('%c')` code.

    * The size of the file in bytes is stored within the `file.st_size` value and is returned as an integer. This means that it must be converted into a string in order for the string to be concatenated and printed out to the screen.

* Answer any questions the class may have regarding this activity before moving to the next activity.

### 8. Guided Practice: Red Flag CSV (0:10)

* In this follow up activity, students will go into the code they just wrote and modify it so that the application creates a new CSV with the file metadata inside of it instead of printing the information to the screen.

* Send students the following files and instructions:

    * **Files:** [RedFlagSea.zip](Activities/04-Stu_RedFlagCSV/Unsolved/RedFlagSea.zip)

    * **Instructions:**

        * Using the previous activity as a jumping off point, modify the application so that instead of printing out all of the file metadata to the screen, it will instead create a CSV file that holds all of the information instead.
        
        * You only need to add and modify two lines of your original code. We provided the script file for you with where this needs to happen. 

### 9. Direct Instruction: Red Flag CSV Review (0:05)

* Open the [solved version](Activities/04-Stu_RedFlagCSV/Solved/RedFlagCSV.py) of the activity in VS Code. Explain the following minor changes that were made to the application:

    * Only three lines of code were modified in this application in order to make it print the data to a CSV file instead of to the screen.

    * The first change was in adding the connection the external CSV file through using `open()` in write mode.

    * The second change was in modifying the print statement to now be a `file.write()` function instead. The syntax had to be changed slightly, spaces were removed after the commas and a newline character was added onto the end of the string, but nothing much was altered from the original.

* Answer any questions students may have before moving to the break.

-----

### 10. BREAK (0:45)

-----

### 11. Direct Instruction: The Zip File Module (0:15)

* Zip files have been commonly used throughout this week of lessons and they will also be a critical aspect of this week's homework so, before moving onto some review materials, take some time to go over how the `zipfile` module works in Python.

    * Start out by explaining that the zip file format is a common archive and compression standard. It essentially takes large files or collections of files and compresses them into a form that is more easily sent and received.

    * The `zipfile` module provides its users with the ability to read, write, append, and list a zip file. However, we will only be focusing today on extracting files. 
    
* Open [ZipFiles.py](Activities/05-Ins_ZipfileModule/ZipFiles.py) in VS Code and explain the following points:

* When working with a zip file, you need to create a connection to it. This works in much the same way that the `open()` function does as the function `zipfile.ZipFile()` is called and the path to the file is passed as a parameter. 

    * The `zipfile.ZipFile()` function returns a zip file object. In the example, we've stored the returned object into a variable. 
    
    ```zipfileReference = zipfile.ZipFile("Text.zip")```
    
    * We save that object into a variable, and then we run the `.extractall()` function on the variable.

* Sometimes, a zip file is password protected. In order to extract, you will need to know the password and will then need to store the password as a variable. 

    * A specific parameter must be passed into the `.extractall()` function. You have to pass the parameter of `pwd=PASSWORD_STRING.encode('cp850','replace')` into the function.
    
        * `.encod()` function converts a string into bytes

    * If you don't pass the password with the correct encoding, cp850, the `.extractall()` function will not be able to enter in a recognizable passkey and you won't be able to extract the files. `zipfile.extractall()` expects bytes, not strings.
    
    ```lockedZip = zipfile.ZipFile("Books.zip")

      password = "password"

      lockedZip.extractall(pwd=password.encode())
      ```
     

* Answer any questions the students may have before moving to the next activity.

### 12. Guided Practice: Zip-A-Dee-Doo-Dah (0:10)

* In this activity, students are given a password-protected zip file filled with music sheets and will have to unpack the file using Python's `zipfile` module.

* Send students the following files and instructions:

    * **File:** [MusicSheets.zip](Activities/06-Stu_ZipADeeDooDah/Unsolved/MusicSheets.zip)
                 
                  [ScriptFile](Activities/06-Stu_ZipADeeDooDah/Unsolved/ZipADeeDooDah.py) 
    

    * **Instructions:**
    
        * Create a Python application that takes the **MusicSheets** file and unzips it.

        * The zip file **IS** password protected! ComicSans is the password.
        
        * The script file will walk you step-by-step through the solution code you will need to write.

### 13. Direct Instruction: Zip-a-Dee-Doo-Dah (0:10)

* Open the [solved version](Activities/06-Stu_ZipADeeDooDah/Solved/ZipADeeDooDah.py) of the activity in VS Code and explain the following:

    * The code for this activity is fairly straightforward. First, the zip file is connected to using the `zipfile.ZipFile()` method.
    
    * We stored the password "ComicSans" as a variable called password and then passed it into the `lockedZip.extractall()` function. 
    
    * The key to this part of the code is the encoding, because without this aspect of the code then the zip file would remain locked and would not get extracted.

* Answer whatever other questions the class may have before moving onto the next activity.

### 14. Guided Practice: XKCD Passwords (0:40)

* Now is the time to bring everything that students have learned these past two weeks together into one application based on a [popular XKCD comic](https://xkcd.com/936/).

* In this application, students will create a robust random-password generator by taking two text files full of common nouns in the English language, combining them together into a single list, and then selecting four random words from within it to create a new string.

* Send students the following files and instructions over Slack:

    * **File:** [WordList.zip](Activities/07-Stu_XKCDPassword/Unsolved/WordList.zip)

    * **Instructions:** [Script File](Activities/07-Stu_XKCDPassword/Unsolved/XKCDPassword.py) 
    
        * In this application, you will create a robust random-password generator by taking two text files full of common nouns in the English language, combining them together into a single list, and then selecting four random words from within it to create a new string.

        * This application will require the `secrets`, `os`, and `zipfile` modules.

        * The following are three definitive parts to this application:

            * The first part connects to the zip file provided and extracts all of its contents

            * The second part builds a complete word list by looping through the text files that were originally stored within the zip file

            * The third part randomly selects four words from the complete word list, puts them together into a single string, and then prints the result to the terminal.

    * **Hints:**

        * This is a challenging activity, and will likely take quite some time to finish. Feel free to work in groups!
        
        * Remember to test your application often to ensure it is working properly. Do not try and write the entire program in one go.
        * Parts of this code are similar to activities you have done previously. Feel free to look back at your previous code for ideas on how you could potentially solve this problem.

### 15. Direct Instruction: XKCD Passwords Review (0:10)

* Open the [solved version](Activities/07-Stu_XKCDPassword/Solved/XKCDPassword.py) of the activity within VS Code. Explain the following points:

    * The first part of this application is similar to the other `zipfile` examples the class had covered earlier on. All we need to do is create a connection to the original zip file and then extract all the contents. There is no password, so the process is only two lines long.

    * In order to create the complete word list, a variable storing an empty list first has to be created.

    * From there, the program has to loop through all the files in the **WordList** folder and split the text within each on new lines, which will then return a list of words from that file. 

    * The program then loops through this list of words one at a time and pushes each individual word into the complete word list from earlier.

    * To create the final password, a variable containing an empty string is made.

    * The program then loops four times, finding a new random word from the complete word list using the `secrets.choice()` function and concatenating the word into a string.

    * We include the `capitalize()` function here to capitalize the first letter of each word. Though using this function isn't necessary, it makes the final string a little easier to read.
    
* Answer any questions the class may have and remind students to complete their homework before congratulating the students and briefly recapping the past two weeks.

### 16. Direct Instruction: Installs for Next Class (0:01)

* Remind students that they need to install Virtual Box with a Kali Linux set up (details in slides) and if they should struggle, run into issues or want help, they should come to office hours before next class to troubleshoot.