# 0x16. C - Simple Shell

# Tasks

# Pseudocode

```
WHILE TRUE
	show_prompt()
	cmd = read_user_input()
	IF cmd == "exit"
		exit() //system call
	ELSE
		tokens = tokenize_user_input(cmd)
	IF check_builtin_cmd(tokens)
		path = check_executable_file(cmd[0])
		IF path == null
			perror("Command not found")
		ELSE
			p_id = fork() //system call
			IF p_id == 0
				run_cmd(path,tokens)
			ELSE
				pp_id = p_id
				wait(pp_id) //system call
```

# Flowchart
![simple shell (1)](https://github.com/globalsmile/simple_shell/assets/106287208/58949738-eb02-44d9-839c-6335973578aa)


## 0. Betty would be proud

* Write a beautiful code that passes the Betty checks.

**Solution:** [simple_shell](https://github.com/globalsmile/simple_shell)

## 1. Simple shell 0.1

* Write a UNIX command line interpreter.

	- Usage: simple_shell

* Your Shell should:
	- Display a prompt and wait for the user to type a command. A command line always ends with 	- a new line.
	- The prompt is displayed again each time a command has been executed.
	- The command lines are simple, no semicolons, no pipes, no redirections or any other advanced 		features.
	- The command lines are made only of one word. No arguments will be passed to programs.
	- If an executable cannot be found, print an error message and display the prompt again.
		Handle errors.
	- You have to handle the “end of file” condition `(Ctrl+D)`

* You don’t have to:
	- use the PATH
	- implement built-ins
	- handle special characters : ", ', ,,\ *, &, #
	- be able to move the cursor
	- handle commands with arguments

`execve` will be the core part of your Shell, don’t forget to pass the environ to it…

**Solution:** [simple_shell](https://github.com/globalsmile/simple_shell)

## 2. Simple shell 0.2

* Simple shell 0.1 +

	- Handle command lines with arguments

**Solution:** [simple_shell](https://github.com/globalsmile/simple_shell)

## 3. Simple shell 0.3

* Simple shell 0.2 +

	- Handle the PATH
	- fork must not be called if the command doesn’t exist

**Solution:** [simple_shell](https://github.com/globalsmile/simple_shell)

## 4. Simple shell 0.4

* Simple shell 0.3 +

	- Implement the exit built-in, that exits the shell
	- Usage: `exit`
	- You don’t have to handle any argument to the built-in exit

**Solution:** [simple_shell](https://github.com/globalsmile/simple_shell)

## 5. Simple shell 1.0

* Simple shell 0.4 +

	- Implement the env built-in, that prints the current environment

**Solution:** [simple_shell](https://github.com/globalsmile/simple_shell)

## 6. Simple shell 0.1.1

* Simple shell 0.1 +

	- Write your own `getline` function
	- Use a buffer to read many chars at once and call the least possible the `read` system call
	- You will need to use `static` variables
	- You are not allowed to use `getline`
*You don’t have to:
	- be able to move the cursor

**Solution:** [simple_shell](https://github.com/globalsmile/shell)

## 7. Simple shell 0.2.1

* Simple shell 0.2 +

	- You are not allowed to use `strtok`

**Solution:** [simple_shell](https://github.com/globalsmile/simple_shell)

## 8. Simple shell 0.4.1

*  Simple shell 0.4 +

	- handle arguments for the built-in `exit`
	- Usage: `exit status`, where `status` is an integer used to exit the shell

**Solution:** [simple shell](https://github.com/globalsmile/simple_shell)

## 9. setenv, unsetenv

* Simple shell 1.0 +

* Implement the `setenv` and `unsetenv` builtin commands
	- `setenv`
		- Initialize a new environment variable, or modify an existing one
		- Command syntax: `setenv VARIABLE VALUE`
		- Should print something on stderr on failure
	- unsetenv
		- Remove an environment variable
		- Command syntax: `unsetenv VARIABLE`
		- Should print something on `stderr` on failure

**Solution:** [simple_shell](https://github.com/globalsmile/simple_shell)

## 10. cd

* Simple shell 1.0 +

* Implement the builtin command `cd`:

	- Changes the current directory of the process.
	- Command syntax: `cd [DIRECTORY]`
	- If no argument is given to `cd` the command must be interpreted like `cd $HOME`
	- You have to handle the command `cd -`
	- You have to update the environment variable `PWD` when you change directory
* `man chdir`, `man getcwd`

**Solution:** [simple_shell](https://github.com/globalsmile/simple_shell)

## 11. ;

* Simple shell 1.0 +

	- Handle the commands separator `;`

**Solution:** [simple_shell](https://github.com/globalsmile/simple_shell)

## 12. && and ||

* Simple shell 1.0 +

	- Handle the `&&` and `||` shell logical operators

**Solution:** [simple_shell](https://github.com/globalsmile/simple_shell)

## 13. alias

* Simple shell 1.0 +

- Implement the `alias` builtin command
- Usage: `alias [name[='value'] ...]`
	- `alias`: Prints a list of all aliases, one per line, in the form name='value'
	-  `alias name [name2 ...]`: Prints the aliases `name`, `name2`, etc 1 per line, in the form 				`name='value'`
	- `alias name='value' [...]`: Defines an alias for each `name` whose `value` is given. If `name` is already an alias, replaces its value with `value`

**Solution:** [simple_shell](https://github.com/globalsmile/simple_shell)

## 14. Variables

* Simple shell 1.0 +

	- Handle variables replacement
	- Handle the `$?` variable
	- Handle the `$$` variable

**Solution:** [simple_shell](https://github.com/globalsmile/simple_shell)

## 15. Comments

* Simple shell 1.0 +

	- Handle comments (#)

**Solution:** [simple_shell](https://github.com/globalsmile/simple_shell)

## 16. File as input

* Simple shell 1.0 +

	- Usage: `simple_shell [filename]`
	- Your shell can take a file as a command line argument
	- The file contains all the commands that your shell should run before exiting
	- The file should contain one command per line
	- In this mode, the shell should not print a prompt and should not read from `stdin`

**Solution:** [simple_shell](https://github.com/globalsmile/simple_shell)
