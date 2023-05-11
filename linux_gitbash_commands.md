# **Fundamental Linux and GitBash Commands**

### **File Permission**

Change directory file read, write and executable permissions using `chmod`.

There are three groups all together in the order: `u` (Owner) , `g` (Group) and `o` (Everyone) (When applying a command to all groups, `a` can be used).

A group can have 3 permission types: `r` : Read, `w` : Write and `x` : Execute.

The operators `-` (Removes permission), `+` (Grants permission) and `=` (Sets permission and removes others) can be used to command what change is needed.

When changing a permission use the format:

    chmod <group><operator><permission_type> <file>

Example below shows the group of `everyone` has the execute (`x`) permission added.

![Permission types](Capture.PNG)

_Note: Add `sudo` to grant privileged commands._

Alternatively, a specific number can be entered in place of `<group><operator><permission_type>` to perform the same command; this can be found in the [chmod calculator](https://chmod-calculator.com/).

To create a new file with no content use:

    touch <File>

### **File Management**

To remove a file or directory use:

    rm -rf

_Note: In the case of removing a directory use -rf to forcefully remove it._

To list the contents of a directory use:

    ls -a -l

_Note: Use the long hand -all to view more information about the directory. The wildcard command `*` can also be used after a keyword to filter the content, for example `ls my*` will output `myPhotos` only._

To move files or directories use:

    mv <File/Directory> <Directory>

### **File Editor**

To access and edit a file using Nano use:
    
    nano <File>

_Note: Use ctrl+x to save, rename and return to the terminal._

### **Directory Utilities**

To create a directory use:

    mkdir <directory>

_Note: To make a directory hidden include a `.` before the directory name._

To remove a directory use:

    rmdir <directory>

### **Directory Utilities**

To reads and output contents of a file use:

    cat <file>

Return first lines of a file (default is first 10):

    head <file>

Return last lines of a file (default is first 10):

    tail <file>

Returns file contents line in alphabetical order:

    sort <file>

Return number of lines:

    nl <file>

Return file information (number of lines, bytes, filename):

    wc <file>

Combine commands together using `|` (pipe); for example, to list the first three files:

    ls | head -3

### **Process Management**

Returns all processes that are running and resources (press `q` to exit):

    top

Returns processes being run by the user (takes a snapshot, does not lock the terminal):

    ps aux

Delay calling process of next command:

    <process> <duration> <&: bg operator>

_Note: For example to send a process to the background for 5 seconds, use `sleep 5 &`. Without `&`, process are sent to the foreground._

Stops the specific process using PID; `-9` immediately terminate:

    kill <priority> <PID>

_Note: A priority of `-9` will immediately terminate the process._

### **Other**

To change the working directory use:

    cd /folder

_Note: Use .. (instead of /folder) to return to the parent directory._

To print the current working directory use:

    pwd

Using `ctrl+z` will stop processes if the terminal is locked.
