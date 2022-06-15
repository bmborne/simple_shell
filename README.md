## Table of Contents
* [Description](#description)
* [File Structure](#file-structure)
* [Requirements](#requirements)
* [Installation](#installation)
* [Usage](#usage)
* [Example of Use](#example-of-use)
* [Bugs](#bugs)
* [Authors](#authors)
* [License](#license)

## Description
simple_shell is a command line interpreter, or shell, in the tradition of the first Unix shell written by Ken Thompson in 1971. This shell is intentionally minimalistic, yet includes the basic functionality of a traditional Unix-like command line user interface.
Standard functions and system calls employed in simple_shell include:
   `access, execve, exit, fork, free, fstat, getline, malloc, perror, signal, stat, wait, write.`

## File Structure
* [AUTHORS](AUTHORS) - List of contributors to this repository
* [man_1_simple_shell](man_1_simple_shell) - Manual page for the simple_shell
* [shell.h](shell.h) - program header file
* [builtins.c](builtins.c) - major builtin functions
  * `check_for_builtins` - checks to see if the user's command matches a builtin
  * `new_exit` - exits the shell with the option of a specified status
  * `_env` - prints the shell's environment variables to the standard output
  * `new_setenv` - initializes a new environment variable, or modifies an existing one
  * `new_unsetenv` - removes an environment variable
* [builtins2.c](builtins2.c) - helper functions for the builtins
  * `add_key` - creates a new environment variable
  * `find_key` - finds an environment variable in the environment array
  * `add_value` - creates a new environment variable string
  * `_atoi` - converts a string into a non-negative integer
* [environment.c](environment.c) - functions related to the environment
  * `make_env` - creates the shell's environment from the parent process
  * `free_env` - frees the shell's environment
* [errors.c](errors.c) - functions related to printing errors
  * `print_error` - prints an error message to the standard error
  * `_puts2` - prints a string to the standard error
  * `_uitoa` - converts an unsigned integer to a string
* [memory_allocation.c](memory_allocation.c) - memory allocation functions
  * `_realloc` - a custom realloc function for arrays of pointers
* [new_strtok.c](new_strtok.c) - custom strtok and helper functions
  * `check_match` - checks if a character matches any in a string
  * `new_strtok` - a custom strtok for the shell
* [path.c](path.c) - functions related to executing commands
  * `path_execute` - executes a command in the PATH
  * `find_path` - finds the PATH environment variable
  * `check_for_path` - checks if the command is in the PATH
  * `execute_cwd` - executes a command with an absolute path
  * `check_for_dir` - checks if the command contains an absolute path
* [simple_shell.c](simple_shell.c) - essential functions to the shell
  * `main` - the main function of the program
  * `sig_handler` - handles SIGINT
* [strfunc.c](strfunc.c) - functions related to string manipulation
  * `_puts` - writes a string to standart output
  * `_strdup` - duplicates a string
  * `_strcmpr` - compares two strings
  * `_strcat` - concatenates two strings with a `/` in the middle
  * `_strlen` - calculates the length of a string
* [tokenize.c](tokenize.c) - tokenizing function
  * `tokenize` - creates an array of tokens from a buffer with a specified delimiter

## Requirements

simple_shell is designed to run in the `20.04.4 LTS (Focal Fossa)` linux environment and to be compiled using the GNU compiler collection v. `gcc 9.4.0 ` with flags`-Wall, -Werror, -Wextra, and -pedantic.`

## Installation

   - Clone this repository: `git clone "https://github.com/bmborne/simple_shell.git"`
   - Change directories into the repository: `cd simple_shell`
   - Compile: `gcc -Wall -Werror -Wextra -pedantic *.c -o hsh`
   - Run the shell in interactive mode: `./hsh`
   - Or run the shell in non-interactive mode: example `echo "pwd" | ./hsh`

## Usage

The simple_shell is designed to execute commands in a similar manner to sh, however with more limited functionality. The development of this shell is ongoing. The below features will be checked as they become available (see man page for complete information on usage):

### Features
- [x] uses the PATH
- [x] implements builtins
- [x] handles command line arguments
- [x] custom strtok function
- [x] uses exit status
- [x] shell continues upon Crtl+C (**^C**)
- [x] handles comments (#)
- [x] handles **;**
- [ ] custom getline type function
- [ ] handles **&&** and **||**
- [ ] aliases
- [ ] variable replacement


### Builtins

- [x] exit
- [x] env
- [x] setenv
- [x] unsetenv
- [ ] cd
- [ ] help
- [ ] history

## Example of Use
Run the executable in your terminal after compiling:
```
root@44351281a413:/simple_shell# ./hsh
$ ls -alrth
total 96K
drwxr-xr-x 1 root root  147 Jun 13 13:50 ..
-rw------- 1 root root  148 Jun 14 09:36 .simple_shell_history
drwxr-xr-x 8 root root  220 Jun 14 09:41 .git
-rwxr--r-- 1 root root 1.3K Jun 14 09:50 new_strtok.c
-rwxr--r-- 1 root root 3.4K Jun 14 09:50 path.c
-rwxr--r-- 1 root root 1.8K Jun 14 09:50 shell.h
-rwxr--r-- 1 root root 1.5K Jun 14 09:50 simple_shell.c
-rwxr--r-- 1 root root  484 Jun 14 09:50 memory_allocation.c
-rw-r--r-- 1 root root 2.3K Jun 14 09:50 man_1_simple_shell
-rwxr--r-- 1 root root 1.2K Jun 14 09:50 errors.c
-rwxr--r-- 1 root root  710 Jun 14 09:50 environment.c
-rwxr--r-- 1 root root 2.1K Jun 14 09:50 strfunc.c
-rwxr--r-- 1 root root  719 Jun 14 09:50 tokenize.c
-rwxr--r-- 1 root root 2.8K Jun 14 09:50 builtins.c
-rw-r--r-- 1 root root 6.3K Jun 14 09:51 README.md
-rw-r--r-- 1 root root  110 Jun 14 09:52 AUTHORS
-rwxr--r-- 1 root root 2.4K Jun 14 10:00 builtins2.c
drwxr-xr-x 3 root root 4.0K Jun 14 10:07 .
-rwxr-xr-x 1 root root  27K Jun 14 10:07 hsh

```
## Bugs
At this time, there are no known bugs.

## Authors
Boniphace Mkindi | [GitHub](https://github.com/bmborne)


William Chipungu | [GitHub](https://github.com/prophet852)

## License
simple_shell is open source and therefore free to download and use without permission.
