### 1. **Intro to Bash**
   - **Description:** Bash (Bourne Again SHell) is a command-line interface and scripting language used in Unix-like operating systems, such as Linux and macOS. It allows users to interact with the system, run programs, and automate tasks.
   - **Example:** 
     ```bash
     echo "Hello, World!"
     ```
     This command prints "Hello, World!" to the terminal.

### How to Access Bash Shell from Different Operating Systems:

#### a. **Linux:**
   - **Default:** On most Linux distributions, Bash is the default shell. You can open it using:
     - **Terminal:** Search for "Terminal" in the applications menu or press `Ctrl + Alt + T`.
     - Once the terminal opens, you will be in Bash by default.

#### b. **macOS:**
   - **Default:** In older versions of macOS, Bash was the default shell. In newer versions (from Catalina onward), it was replaced by Zsh, but Bash is still available.
     - **Terminal:** Search for "Terminal" using Spotlight (`Cmd + Space`, then type "Terminal" and press Enter).
     - Once the terminal opens, you can start a Bash session by typing:
       ```bash
       bash
       ```

#### c. **Windows:**
   - **Windows 10 and Windows 11:**
     - **Windows Subsystem for Linux (WSL):** If you have WSL installed, you can access Bash by:
       - Searching for "Ubuntu" or any other Linux distribution you installed from the Start menu, or typing "bash" in the Command Prompt (`cmd`).
       - Once opened, a terminal window with Bash will be ready to use.
     - **Git Bash:** Another alternative is using Git Bash, which comes with Git for Windows.
       - Download and install [Git for Windows](https://gitforwindows.org/).
       - After installation, search for "Git Bash" in the Start menu.
   - **PowerShell or Command Prompt:** You can install Bash through WSL:
     - Open PowerShell as an administrator (`Run as administrator`).
     - Run the following command to install Ubuntu:
       ```powershell
       wsl --install
       ```
     - After installation and a restart, you can search for "Ubuntu" and open it from the Start menu.

### 2. **Basic Bash Commands**
   - **Description:** Bash provides basic commands to navigate the filesystem and manage files.
   - **Examples:**

     ```bash
      # List directory contents
     
      ls        # Lists files and directories in the current directory
      ls -l     # Lists in long format with detailed information
      ls -a     # Lists all files, including hidden files
  
      # Change directory
     
      cd /path/to/directory  # Changes the current directory
      cd ..     # Moves up one directory level
      cd ~      # Changes to the home directory
      
      # Print Working Directory

      pwd       # Prints the full path of the current directory
      
      # Create, Move, and Delete Files/Directories
     
      touch filename.txt  # Creates an empty file named filename.txt
      mkdir my_directory  # Creates a new directory named my_directory
      mv filename.txt /path/to/destination/  # Moves or renames a file
      cp filename.txt /path/to/destination/  # Copies a file
      rm filename.txt    # Deletes a file
      rm -r my_directory # Deletes a directory and its contents
      
      # Display File Content
     
      cat filename.txt   # Displays the content of a file
      less filename.txt  # Displays the content of a file one page at a time
      head filename.txt  # Shows the first 10 lines of a file
      tail filename.txt  # Shows the last 10 lines of a file
      
      # Search and Find
     
      grep "pattern" filename.txt  # Searches for a pattern in a file
      find /path/to/search -name "filename"  # Finds files in a directory hierarchy
      
      # Permissions
     
      chmod 755 filename.txt  # Changes file permissions
     ```

### 3. **Manipulate Files using Wildcards**
   - **Description:** Wildcards are special characters that allow you to specify patterns to match filenames. They are useful for manipulating multiple files at once.
   - **Wildcards:**
     - `*`: Matches any number of characters, including none.
     - `?`: Matches exactly one character.
     - `[]`: Matches any one of the enclosed characters.
     - `[!char]` or `[^char]`: Matches any character not enclosed in the brackets.
   - **Examples:**
     ```bash
     # Using the '*' wildcard
     ls *.txt       # Lists all files ending with .txt
     rm file*       # Deletes all files starting with 'file'
     mv *.jpg /images/  # Moves all .jpg files to the images directory

     # Using the '?' wildcard
     ls ?.txt       # Lists files with a single character name followed by .txt (e.g., a.txt, b.txt)
     cp file?.txt /backup/  # Copies files named 'file1.txt', 'file2.txt', etc., to the backup directory

     # Using '[]' wildcard
     ls file[123].txt   # Lists files named file1.txt, file2.txt, and file3.txt
     mv report[0-9].pdf /reports/  # Moves report0.pdf, report1.pdf, ..., report9.pdf to the reports directory

     # Using '[!char]' or '[^char]' wildcard
     ls [!abc]*.txt   # Lists all .txt files not starting with 'a', 'b', or 'c'
     rm [^0-9]*.log   # Deletes all .log files not starting with a digit

     # Combining wildcards
     ls *.t?          # Lists files with extensions like .txt, .tar, etc.
     mv file[1-5]?.* /destination/  # Moves files like file1a.txt, file2b.pdf, file3c.doc, etc.
     ```

### 4. **Pipelines**
   - **Description:** Pipelines use the `|` character to pass the output of one command as the input to another.
   - **Example:**
     ```bash
     ls -l | grep ".txt"  # Lists all .txt files with detailed information
     ```
     Here, `ls -l` lists files in detail, and `grep ".txt"` filters the results to show only `.txt` files.

### 5. **Background Jobs**
   - **Description:** Run processes in the background so the terminal remains available for other commands.
   - **Examples:**
     ```bash
     long_running_command &
     ```
     The `&` at the end runs the command in the background.

### 6. **Aliases**
   - **Description:** Aliases are shortcuts for longer commands.
   - **Examples:**
     ```bash
     alias ll='ls -la'  # Creates an alias 'll' for 'ls -la'
     alias rm='rm -i'   # Prompts before deleting files
     ```
     Use `unalias` to remove an alias:
     ```bash
     unalias ll
     ```

### 7. **Bash Variables**
   - **Create Shell Variables:**
     - **Description:** Store data for later use.
     - **Example:**
       ```bash
       greeting="Hello, World!"
       echo $greeting
       ```
   - **Variables Quoting and Backslash Escaping:**
     - **Description:** Use quotes to handle spaces or special characters in variables.
     - **Examples:**
       ```bash
       message="This is a message with spaces"
       echo "$message"
       
       special_chars="Special\$Char!"
       echo "$special_chars"
       ```
   - **Built-In Variables:**
     - **Description:** Bash has several built-in variables like `$HOME` (user's home directory) and `$PWD` (current directory).
     - **Example:**
       ```bash
       echo $HOME  # Prints the home directory
       echo $PWD   # Prints the current directory
       printenv    # Prints all the environment variables
       ```

### 8. **Special Files**
   - **Concept of Special Files:**
     - **Description:** Special files, like `.bashrc`, configure the shell environment.
   - **Creating `.bashrc`:**
     - **Example:**
       ```bash
       echo 'alias ll="ls -la"' >> ~/.bashrc  # Adds an alias to .bashrc
       source ~/.bashrc                       # Applies changes
       ```

### 9. **Bash Script File Format**
   - **Description:** Bash scripts are text files containing a series of commands. They start with a "shebang" (`#!`) line.
   - **Example:**
     ```bash
     #!/bin/bash
     echo "This is a Bash script."
     ```

### 10. **Run Script**
   - **Description:** To run a Bash script, make it executable and run it.
   - **Example:**
     ```bash
     chmod +x script.sh  # Makes the script executable
     ./script.sh         # Runs the script
     ```

### 11. **PATH Variable**
   - **View PATH Variable’s Value:**
     - **Description:** The `PATH` variable lists directories where the system looks for executable files.
     - **Example:**
       ```bash
       echo $PATH
       ```
   - **Changing PATH Value and Run Script:**
     - **Example:**
       ```bash
       export PATH=$PATH:/path/to/directory  # Temporarily adds a directory to PATH
       ```

### 12. **Positional Parameters**
   - **Description:** Positional parameters in Bash are used to pass arguments to a script or function. `$1`, `$2`, etc., represent the first, second, and subsequent arguments passed to the script. `$0` represents the script's name, and `$@` or `$*` represents all the arguments.
   - **Example:**
     ```bash
     #!/bin/bash

     echo "Script name: $0"
     echo "First argument: $1"
     echo "Second argument: $2"
     echo "All arguments: $@"

     # Run this script with: ./script.sh arg1 arg2
     ```
   This script prints the script's name and the arguments passed to it when executed.


### 13. **Functions within Bash Script**
   - **Description:** Functions are reusable blocks of code.
   - **Example:**
     ```bash
     function greet() {
       echo "Hello, $1"
     }
     greet "Alice"  # Outputs: Hello, Alice
     ```

### 14. **Bash Conditions**
   - **Description:** Use `if`, `then`, `else`, and `fi` for conditional statements.
   - **Example:**
     ```bash
     if [ -f "file.txt" ]; then
       echo "File exists."
     else
       echo "File does not exist."
     fi
     ```

### 15. **Bash Loop**
   - **Description:** Loops iterate over a series of items.
   - **Examples:**
     ```bash
     # For loop
     for i in 1 2 3; do
       echo "Number: $i"
     done

     # While loop
     count=1
     while [ $count -le 3 ]; do
       echo "Count: $count"
       ((count++))
     done
     ```

### 16. **Bash Case**
   - **Description:** `case` statements handle multiple conditions.
   - **Example:**
     ```bash
     case "$1" in
       start)
         echo "Starting..."
         ;;
       stop)
         echo "Stopping..."
         ;;
       *)
         echo "Usage: $0 {start|stop}"
         ;;
     esac
     ```
This script takes a command-line argument and matches it to `start` or `stop`. If neither matches, it shows a usage message.
