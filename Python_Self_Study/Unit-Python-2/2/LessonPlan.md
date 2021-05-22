## 4.2 Lesson Plan: Modules in Python 
 
### Overview

In this lesson, students will learn about Python's built-in modules, and will get practice importing and using several of them in their programs and applications. The second half of class will focus exclusively on the `os` module, and by the end of class, students will build their first malicious program. 
 
### Objectives

By the end of class, students will be able to:

* Import the `string`, `random`, and `hashlib` modules to access the functions within them. 
* Use the `csv` module to read and write data to external CSV files.
* Use the `secrets` module to generate random passwords.
* Use the `os` module to create file paths and check for specific files.
* Use the `os` module to navigate through a folder system and automate tasks.
* Use the `os` module to perform a simple attack on an operating system.

### Instructor Notes

* Today's class is fast paced and includes challenging activities.

* The second half of class will focus exclusively on the `os` module. Take time to make sure that your students understand the concepts being taught. The final activity is particularly difficult, but it will give students their first exposure to creating a malicious program. 

* Review and run all the activities before teaching class. When demonstrating concepts with the code files, walk students through the syntax before running the scripts. 

* If you see students struggling, take a pause between the demos (Direct Instruction) and the student activities, and have a simple drill practice to ensure that students understand the concepts being taught.

* The slides provided mostly contain the instructions for the activities. They also include the class objective slide. This slide list the student's goals for the day. At key points, these objectives are again shown and the ones that have just been covered will be shown with check marks. Use these slides to ask students if they have questions about anything that has been covered so far. You can also use this time to review the concepts, as well as to provide additional real-world examples of how the concepts are used. 

### Sample Class Video

* To view an example class lecture, visit: [Class Video](https://codingbootcamp.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=ecfa091b-2e46-417c-aba8-a9a5017cbcf2).


### Slideshow

- The lesson slides are available on Google Drive here: [Advanced Python Day 2 Slides](https://docs.google.com/presentation/d/1fiDTnaMOktZuhd94nZE03k0fyyP9m5rdU4WpNR7IoGU/).

- To add slides to the student-facing repository, download the slides as a PDF by navigating to File > "Download as" and choose "PDF document." Then, add the PDF file to your class repository along with other necessary files.

- **Note:** Editing access is not available for this document. If you or your students wish to modify the slides, please create a copy by navigating to File > "Make a copy...".

----

### 1. Direct Instruction: Introduction to Built-In Modules (0:15)

* Welcome the class back to their second day of advanced concepts in Python and let them know that today's lesson will be covering the wonderful world of built-in modules.

* Explain that a module is a file containing a set of definitions for functions, classes, and/or variables which can be imported and used in another programs and applications.

    * Python has many built-in modules for executing different tasks, for example:

        * The `csv` module allows users to more easily work with external CSV files.

        * The `os` module allows users to work with the operating system.

        * The `datetime` module contains functions for manipulating dates and times.

    * In order for a program or file to use the code contained within a module, the module file has to be added into the script using a process called importing.

    * Once the module has been imported, the functions and other attributes in the module can be referenced in the program to execute tasks.

* Open [IntroToModules.py](Activities/01-Ins_IntroToModules/IntroToModules.py) in VS Code and explain the following:

    * First, to make module accessible to a program, use the `import` statement followed by the name of the module.

    * Once a module has been imported, the functions, methods, and values that it contains can then be used anywhere in the program.

        * To access the code stored within a module, you will have to name the modules and then use dot notation in order to access the desired value or function.

        * For example, to use the `pow()` function stored within the `math` module, the programmer would have to type `math.pow()` into their script.

* A lot of the modules included in Python are quite large and contain a vast quantity of data and functions in them. Tell students to use the Python documentation for this. 

    * Slack out [The Python Standard library](https://docs.python.org/3/library/index.html) to the class and show them how many built-in modules this programming language has access to.

    * Emphasize that because there are many built-in modules with many useful feature. Students are not expected to memorize all the modules, but instead they should get comfortable using this documentation throughout their coding careers.

* Answer any questions the class may have before moving to the first activity for the day.

### 2. Guided Practice: Module Hunter (0:10)

* In this activity, students will be given a short worksheet that will ask them to import modules and then perform tasks using functions in that module. 

* Send students the following files and instructions over Slack:

    * **Files:** [ModuleHunter.py](Activities/02-Stu_ModuleHunter/Unsolved/ModuleHunter.py)

    * **Instructions:**
    
        * Using [The Python Standard library](https://docs.python.org/3/library/index.html) as a reference and the provided file as your guide, import all of modules requested and then complete the tasks listed within the comments.

        * To get you started, we've provided you with the first module that you will be importing.

    * **Hint:** If you get stuck on a problem, remember that there are other sources of information online that may help to clear up the confusion. 

### 3. Direct Instruction: Module Hunter Review (0:10)

* Open the [solved version](Activities/02-Stu_ModuleHunter/Solved/ModuleHunter.py) of the activity in VS Code and point out the following and if possible provide real-world examples of when you would use these modules:

    * The `string` module is used when the user wants to collect some common string constants or format a block of text. While not a commonly used module, the `string` module makes it easier to collect all the possible ASCII characters that an end-user could type.

    * The `random` module is used to add pseudo-random elements into a program. You will often want to use random numbers and values in your program. For example, a game application will need to shuffle a deck of cards at random. The `random` module is used fairly regularly. However, it isn't ideal for any sort of encryption tasks, which will we cover later. 

    * If students are thrown off by how `random.shuffle()` works, explain that the `random.shuffle()` function takes in a list, but instead of returning a new list that is shuffled, it actually modifies the original. This means that the shuffled list is always stored in the original variable.

    * The `hashlib` module is an important module for cybersecurity and allows us to more easily work with specific hash algorithms. We will be covering cryptography in next week's unit, but for now explain to the class that hashing is a common method to encrypt private information.

* Answer any questions the class may have before moving to the next activity.

### 4. Direct Instruction: The CSV Module (0:10)

* In the last class, we covered how to read and write data to CSV files. Now, we'll explain how the CSV module can simplify this process. 

* Open [CSVModule.py](Activities/03-Ins_CSVModule/CSVModule.py) in VS Code and explain the following:

    * As with all modules, the `csv` module must be imported into the script in order for its values, functions, or methods to become accessible.

    * The script also needs to make a connection to the external CSV file using the `open()` function. This was what we did in the last class with our CSV files, but instead of using `file.read()` to read the contents, we use the `csv.reader(file)` method.

        * The `csv.reader()` method automatically splits the contents of the external file into rows whenever there is a newline character and cells whenever there is a comma. This means that there is no need to manually split the file.

        * While this may not seem like much at the surface level, point out to the class how much more optimized this is because it eliminates one extra method (`string.split`)

        * As programmers, we are always looking for ways to make our code cleaner.

    * Answer any questions the class may have before moving to the next activity.

### 5. Guided Practice: User List Revisit (0:10)

* In this activity, students will be diving back into the code they wrote for the user list application from the last class and making modifications to it so that it uses the CSV module instead of having to manually split up the data themselves. They will also modify the file so that it writes the summary to an external text file instead of printing the information out to the terminal.

* Send the students the following files and instructions over Slack:

    * **Files:**
    
        * [UserList.csv](Activities/04-Stu_UserListRevisit/Unsolved/UserList.csv)
        
        * [UserListRevisit.py](Activities/04-Stu_UserListRevisit/Unsolved/UserListRevisit.py)

    * **Instructions:**

        * The provided script contains the original solution from the last class. You must modify it so that it uses the CSV module to read through and parse the external data instead of requiring manual splitting.

        * Modify the script so that, instead of printing out information to the screen, it instead pushes this information into a new text file called **PeopleToKeepEyesOn.txt**.

    * **Hint:** One manual split will be necessary in the completed application since the list of IP addresses is still contained within a single cell. 
    
### 6. Direct Instruction: User List Revisit Review (0:10)

* Open the [solved version](Activities/04-Stu_UserListRevisit/Solved/UserListRevisit.py) of the activity in VS Code and use it as a guide to cover the following:

    * Since the `csv.reader()` method automatically splits the dataset up into rows and cells, there is no need to manually split anything other than the IP list in the third column of each row. This one cell still needs to be split because it contains all of the common IP addresses that the user accesses.

    * In order to write the summary data into an external text file, make a connection to that file using the `open()` function with the mode set to write. Then, instead of using the `print()` function to push the data into the terminal, we use `file.write()`  to push the data into this new text file.

    * Of course, since spacing is not inherent to `file.write()`, newline characters has to be added onto the end of each new line passed. This ensures that the final text file is easy to read.

* Answer any questions the class may have before moving to the next activity.

### 7. Direct Instruction: Secrets Module (0:10)

* While students have already gotten a cursory introduction to randomness with the `random` module, cybersecurity developers are rarely ever going to use this method to generate randomness in their work due to how easily that module can be manipulated. 

    * Random is hardly ever random in the world of computing. This is due to the fact that computers work in concrete values and there is very little room for chaos in their programming. As such, almost every single *random* value generated by a computer was actually created using an algorithm that could, in theory, be replicated or cracked. If possible, provide a simple example of this to share with the class. 

    * Since `random` is not actually random, a preferred module is the `secrets` module. 

* Open [SecureRandomness.py](Activities/05-Ins_SecureRandomness/SecureRandomness.py) in VS code and cover the following:

    * The `secrets` module generates cryptographically strong pseudo-random values that would be suitable for managing data, including passwords, account authentication, and security tokens.

    * Below are some common functions contained in the `secrets` module: 

        * To collect a random integer between zero and a provided number, use the `secrets.randbelow()` method and pass in the provided number as a parameter.

        * To collect a random element from a list, use the `secrets.choice()` method and pass in the list as a parameter.

        * There is no function that allows users to select a number in a given range, for example 10–20 or 25–35, but we can achieve this by using  `secrets.choice()` and passing a `range()` into the method instead of a static list. 

* Answer any questions the class may have before moving to the next activity.

### 8. Guided Practice: Random Password List (0:20)

* In this activity, students will generate a list of 100 random passwords using the `secrets` module and push each individual element into an external file.

* This is a challenging activity, encourage students to work with partners or small groups. 

Send the students the following instructions over Slack:

- [Instructions](Activities/06-Stu_RandomPasswordList/Unsolved/ReadMe.md)


**Random Password Lists**

* In this activity, you will generate a list of 100 random passwords using the `secrets` module and push each individual element into an external file.

* This is a challenging activity, it is highly encouraged to work with partners or small groups. 


**Instructions:**
    
* Import both the `secrets` and `string` libraries into the application.

* Create a string that will hold all of the ASCII characters and digits inside of it.

* Create a connection to an external text file called **PasswordList.txt**.

* Create a loop that will run for 100 iterations and will push a new, 10 character password of random letters/numbers into the external file.

###  9. Direct Instruction: Random Password List Review (0:10)

* Open the [solved version](Activities/06-Stu_RandomPasswordList/Solved/RandomPasswordList.py) of the activity in VS Code and review the following:

    * The `secrets` module is brought into the application to create the random passwords based on the characters stored in the `string.ascii_letters` and `string.digits` variables. While these two variables are not entirely necessary, they do save us time because we will not have to manually type out every letter and digit on the keyboard.

    * The first loop is used to separate each password from one another while the second loop is the one being used to generate each random character that will be placed into the password. Once the second loop concludes, that is when the password is pushed into the external file.

    * Despite all appearances, these are actually rather poor passwords to use. It is easier brute-force passwords with random numbers and letters than passwords with actual words. We will talk more about cryptography in more detail next week.

* Answer any questions students may have before moving to the break.

-----

### 10. BREAK (0:15)

-----

### 11. Direct Instruction: Introduction to the OS Module (0:10)

* One of the most powerful modules in the cybersecurity toolbox is the OS module. The OS module allows the user to create scripts that are capable of looking into and working with the file or folder system of a computer regardless of its operating system.

* Open [IntroToOS.py](Activities/07-Ins_IntroToOS/IntroToOS.py) in VS Code and cover the following:

* A prime example of a difference between how a Mac and a Windows machine operate can be found in the ways their paths function. On Macs, the folder system is separated by forward slashes (/) while in Windows the folder system is separated by backslashes (\\).

    * While this might not seem significant, it can be a severe problem when creating code that is supposed to work across multiple systems.

    * If a mistake is made or something unexpected occurs, the code breaks without question. This means that while a forward slash in an `open()` function's file path may be fine on a Mac, that same exact code will break on a Windows machine.
    
    * As a solution, we can use the `os.path.join()` function when creating file paths. This method checks the computer's OS and inserts the forward slash or backslash based on the OS.
    
    * In the `os.path.join()` function, the parameters that you pass in to the function will be the folder and file names that the function will then modify to create the file path. You should enter in these folders and filenames in the order in which they should appear in the file path.
    
```python 
real_path = os.path.join("Resources", "CoolText.txt")
```

* We can also use the OS modules to check whether a specified file exists or not. 

    * If the file path exists, the value `True` will be returned. And if the file does not exist, the value `False` will be returned.

    * For example, this function can be used when you're creating command-line applications that modify a file system. If the file you want to modify does not exist, your application could break. Instead, it would be ideal if you could check first to see whether it exists and then have your application simply return the value `False` if it doesn’t.
    
* After explaining the code syntax, run the script to show the students what happens.

* Answer any questions the class may have before moving to the next activity.

### 12. Guided Practice: Terminal Library (0:15)

* In this activity, students have been given a **Books** folder that contains text files. They will need to create a program that prompts the user for a file name and then searches the **Books** folder for it.

* Send students the following files and instructions over Slack:

    * **Files:** [Books.zip](Activities/08-Stu_TerminalLibrary/Unsolved/Books.zip)

    * **Instructions:**
    
        * Unzip the **Books** folder.

        * Create an application that will ask the user for the name of a text file, and then checks to see if the file exists in the **Books** folder.

            * If the text file exists, then print the text inside of the file to the terminal.
            
            * If the text file does not exist, then print "Sorry! That book is not in our records! Please try again!"
            
        * **Hint:** When the user enters the file name, keep in mind that they will not use a file extension (.txt). Therefore, when you’re creating your file path, remember that you’ll need to have the file extension added to that user input.

### 13. Direct Instruction: Terminal Library Review (0:10)

* Open the [solved version](Activities/08-Stu_TerminalLibrary/Solved/TerminalLibrary.py) of the activity in VS Code and explain the following:

    * Since the text files are contained within the **Books** folder, the parameters passed into the `os.path.join()` function are **Books** and the name of the file the user entered.

    * Since it is doubtful users will add the **.txt** extension to their files, this particular version of the program will automatically add the file type on for them. If this did not happen, it is doubtful that the text file would actually be found.

    * The `os.path.isfile()` method is used as the conditional check within this application. This means that the program will only attempt to open up a file if that file is found. If the file is not found then an apology is printed to the terminal instead.

* Answer any questions the class may have before moving to the next activity.

### 14. Direct Instruction: Walking Through Folders and Files (0:10)

* Sometimes we don't want to connect to just one file but instead navigate through an entire directory or folder system to perform some tasks.

    * One way to do this would be to have a list or dictionary of all the individual folders and file names, and then loop through it to execute a task. To do it this way, however, is tedious and would take more and more time as folder systems get larger.

    * Thankfully the `os` library comes prepackaged with a function, `os.walk()`,  that speeds this process along considerably both in terms of processing power and time investment.

* Open [OSWalk.py](https://github.com/coding-boot-camp/Cybersecurity-Lesson-Plans/blob/UCLA/1-Lesson-Plans/Unit04-AdvancedPython/2/Activities/09-Ins_OSWalk/OSWalk.py) and explain the following:

    * The `os.walk()` method takes in as a parameter a file path. In the OsWalk.py file, we can see that we’re passing the folder path we created using the `os.path.join` function.
    
    *  The `os.walk()` method **ALWAYS** needs to be used alongside a `for` loop. This then will allow the application to loop through all the folders and files that branch from the file path that was provided as the parameter for `os.walk()`.
    
    * The following are three main fields that the `os.walk()` method can be used to loop through:

      * The first field returned is the root. The root variable lets the application know the current directory that `os.walk()` is moving through and the value stored within this variable will change to reflect the current position of the application.

      * The second field returned are the dirs. The dirs variable is a list of all the folders that are located within the current root. These are the folders that `os.walk()` will navigate into eventually.
      
      *  The third field returned are the files. The files variable is a list of all the files that are located within the current root. The `os.walk()` method will never open up these files manually but the user can create the path to these folders by looping through the list of files and then using `os.path.join()` to combine the value stored within root variable with the current file they want to view.
      
    * This function is EXTREMELY powerful in the hands of an experienced programmer, but it takes a lot of time and practice to get used to.

    * Let students know that this script will bring the values of the root, dirs, and files variables while using `os.walk()`. This will let us know where our application is going and what is available to work with.

* After explaining the code syntax, run the script to show the students what happens.

* Answer any questions the class may have before moving to the next activity.

### 15. Guided Practice: Get Wrekt! (0:20)

* In this activity, the students will be taking on the role of a hacker. Their task as the hacker is to overwrite the hard work of their victim with the phrase "GET WREKT!"

* The application the students are making is intentionally dangerous. If this program is run in a careless or malicious manner, it could cause serious damage to a person's computer. Students should make sure their application is walking through the correct paths BEFORE they add the `file.write()` function into their code.

Send the students the following files and instructions over Slack:

- [Instructions](Activities/10-Stu_GetWrekt/Unsolved/ReadMe.md)
- [Diaries.zip](Activities/10-Stu_GetWrekt/Unsolved/Diaries.zip)


**Important!**
    
* Do not run this application inside any important folders that you don't want to be overwritten. Overwriting the text within files like this is serious business. So make sure that your application only walks through the **Diaries** folder before adding the `file.write()` function in.

* Should you feel nervous about running this application, you can replace the `file.write()` function with `file.read()` instead. This way the program will only read in the data stored within the files instead of overwriting anything.

**Instructions:**

* Unzip the folder.

* Create an application that will check the **Diaries** folder that you just unzipped and automatically navigates through all of its subdirectories and files.
        
  * Have the application print out the current root that the application is walking through.
         
  * Have the application print out all the folders within the current root.
         
  * Have the application print out all the files within the current root.

  * Have your application automatically connect to each of the text files stored within this folder system and replace their text with the phrase "GET WREKT SKRUB!"

  * **Bonus:** Open your browser and locate and download an image. Then move the file into one of the folders within the **Diaries** folder. Run the application again and see what happens to the image file.

### 16. Direct Instruction: Get Wrekt Review/ So You've Created an Attack (0:15)

* Open the [solved version](Activities/10-Stu_GetWrekt/Solved/GetWrekt.py) of the activity in VS Code and explain the following:

    * The `os.walk()` function is told to start navigating from the **Diaries** folder. This means that it will only ever navigate through the folders or files stored within the **Diaries** directory.

    * This application prints out the current root directory as well as all the subfolders and files to the screen. This serves a dual purpose. First, it allows us to see where the application is going. Second, it lets us make sure our application is moving through the correct folder structure and not running wild through the user's computer.

    * Once there are some files within the root directory, the application then loops through all of the files and creates references to their complete path using `os.path.join()`. This allows the path to be used to connect to the file and modify their contents.

* Now that you have gone over the solution to the previous activity, take a moment to congratulate the class on creating their first-ever attack program! In fact, that less than 30 line application they just put together could do some serious damage to a person's computer.

    * In the bonus, students were asked to move an image file into one of the folders and then run the application once again. As they would likely have discovered by doing this, even the image file's content was modified to just say "GET WREKT SKRUB!"
    
    * This means that the application is not only capable of overwriting text, it is capable of corrupting other file types as well. The reason for this is because every single file type out there is pretty much the same. They are all composed of bits that are stored as text and then parsed in particular ways by the operating system.

    * Since every single file type is essentially text on the back end, applications that walk through the operating system and make changes without asking for explicit permission are oftentimes considered to be malicious.

* This is why programming, even if not a required part of a cybersecurity position, is such a helpful tool to know. By understanding how programs work behind the scenes, cybersecurity professionals are better able to spot potentially dangerous applications.

    * Take a few moments to explain some malicious programs that exist out there that could deal damage much like the application the students just made.

* Answer any questions the class may have before letting them out for the day.
