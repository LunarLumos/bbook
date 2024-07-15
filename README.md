
### Basics of Bash Scripting

#### Variables and Data Types

Bash variables are loosely typed and primarily store strings. Here's how you can declare and use variables:

```bash
#!/bin/bash

# Variable assignment
name="John"
age=30
pi=3.14159

# Printing variables
echo "Name: $name"
echo "Age: $age"
echo "Pi: $pi"
```

**Output:**
```
Name: John
Age: 30
Pi: 3.14159
```

#### Input and Output Handling

Bash uses `read` for input and `echo` for output. Here’s an example:

```bash
#!/bin/bash

# Reading input from user
echo "Enter your name:"
read username

# Outputting a message
echo "Hello, $username!"
```

**Output:**
```
Enter your name:
John
Hello, John!
```

#### Control Structures (if-else, loops)

Bash supports `if-else` statements and various loops (`for`, `while`, `until`):

```bash
#!/bin/bash

# if-else statement
echo "Enter a number:"
read num

if [ $num -gt 0 ]; then
    echo "$num is positive."
elif [ $num -lt 0 ]; then
    echo "$num is negative."
else
    echo "$num is zero."
fi

# for loop example
echo "Counting to 5:"
for i in {1..5}; do
    echo $i
done

# while loop example
echo "Counting down from 3:"
count=3
while [ $count -gt 0 ]; do
    echo $count
    ((count--))
done
```

**Output:**
```
Enter a number:
7
7 is positive.
Counting to 5:
1
2
3
4
5
Counting down from 3:
3
2
1
```

#### Functions

Functions allow you to encapsulate reusable code:

```bash
#!/bin/bash

# Function definition
say_hello() {
    local name=$1
    echo "Hello, $name!"
}

# Calling the function
say_hello "Alice"
say_hello "Bob"
```

**Output:**
```
Hello, Alice!
Hello, Bob!
```

#### File Operations

Bash can manipulate files: reading, writing, and checking file properties:

```bash
#!/bin/bash

# Reading from a file
echo "Contents of file:"
cat file.txt

# Appending to a file
echo "New line" >> file.txt

# Checking if a file exists
if [ -f file.txt ]; then
    echo "file.txt exists."
fi
```

### Advanced Topics in Bash Scripting

#### Advanced String Manipulation (Regular Expressions, Pattern Matching)

Bash supports pattern matching and regex through globbing and parameter expansion:

```bash
#!/bin/bash

# Pattern matching with globbing
echo "Files starting with 'file':"
for file in file*; do
    echo $file
done

# Using regex with [[ ]]
string="Hello, world!"
if [[ $string =~ [aeiou] ]]; then
    echo "String contains a vowel."
fi
```

**Output:**
```
Files starting with 'file':
file1
file2
file3
String contains a vowel.
```

#### Advanced File Operations (Recursive Directories, File Locking)

Bash can recursively process directories and implement file locking:

```bash
#!/bin/bash

# Recursive directory traversal
function traverse_directory {
    local directory="$1"
    for file in "$directory"/*; do
        if [ -d "$file" ]; then
            echo "Directory: $file"
            traverse_directory "$file"
        elif [ -f "$file" ]; then
            echo "File: $file"
        fi
    done
}

echo "Files and directories:"
traverse_directory "."

# File locking example
lockfile="file.lock"
exec 200>$lockfile  # Create a lockfile descriptor
flock -n 200 || { echo "Another process is holding the lock."; exit 1; }
echo "Lock acquired. Performing operations..."
sleep 5  # Simulating operations
echo "Operations complete. Releasing lock."
flock -u 200
```

**Output:**
```
Files and directories:
Directory: ./subdir1
File: ./file1.txt
File: ./file2.txt
Lock acquired. Performing operations...
Operations complete. Releasing lock.
```

#### Advanced Control Structures (Select Loop, Extended Test Conditions)

Bash offers `select` for creating interactive menus and extended test conditions:

```bash
#!/bin/bash

# Select loop for interactive menu
PS3="Select an option: "
options=("Option 1" "Option 2" "Option 3" "Quit")
select opt in "${options[@]}"; do
    case $opt in
        "Option 1")
            echo "You chose Option 1"
            ;;
        "Option 2")
            echo "You chose Option 2"
            ;;
        "Option 3")
            echo "You chose Option 3"
            ;;
        "Quit")
            break
            ;;
        *) echo "Invalid option";;
    esac
done
```

**Output:**
```
1) Option 1
2) Option 2
3) Option 3
4) Quit
Select an option:
```
(The actual output depends on user input.)

#### Process Management (Background/Foreground Processes, Signal Handling)

Bash manages processes, supports background/foreground tasks, and handles signals:

```bash
#!/bin/bash

# Running a process in the background
echo "Starting background process..."
sleep 10 &
bg_process_pid=$!
echo "Background process PID: $bg_process_pid"

# Handling signals
trap 'echo "Ctrl+C pressed. Exiting..."; exit' SIGINT

echo "Waiting for background process to complete..."
wait $bg_process_pid
echo "Background process completed."

# Foreground process example
echo "Running foreground process..."
sleep 5
echo "Foreground process completed."
```

**Output:**
```
Starting background process...
Background process PID: 12345
Waiting for background process to complete...
^C
Ctrl+C pressed. Exiting...
Background process completed.
Running foreground process...
Foreground process completed.
```

#### Networking and Interprocess Communication (Socket Programming, SSH)

Bash can interact with networks and processes using sockets and SSH:

```bash
#!/bin/bash

# Socket programming (echo server example)
port=12345
echo "Starting echo server on port $port..."
nc -l -p $port -e /bin/cat
```

### Conclusion

These examples cover a broad range of basic and advanced topics in Bash scripting. Each topic demonstrates fundamental concepts and more sophisticated techniques, empowering you to automate tasks efficiently and effectively in a Unix-like environment. If you have any specific questions or need further clarification on any topic, feel free to ask!
