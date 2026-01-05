# Terminal Shortcuts

Initially you will feel a little inefficient when using the shell. However, to improve your efficiency when using the terminal, note down some of the shortcuts to improve your speed.

## Shell Cursor Manipulation (Also works in text editors)

The following shortcuts will improve moving the text cursor quickly in the shell and a text editor.

* `CTRL+A` - This will reset the text cursor to the beginning of the line.

* `CTRL+E` - This will set the text cursor to the end of the line.

* `CTRL+RIGHT_ARROW` Will move to the start of the next word

* `CTRL+LEFT_ARROW` - Will move to the start of the previous word

To get access to some previously executed commands, you can use `UP_ARROW` which will go to the previous command. While traversing this list, you can use `DOWN_ARROW` to go to the next command.


## Shell Editing Shortcuts (Should also work in text editors)

When using the following shortcuts, you should be able to edit text quickly.

* `CTRL+W` - Deletes the previous word

* `ALT+D` - Deletes the next word

* `CTRL+U` - Deletes the line

* `CTRL+SHIFT+V` - Pastes what is currently in the copy-clipboard.

* `CTRL+K` - Cuts the text (to the clipboard) until the end of the start


## Process Control Shortcuts

You will likely encounter an infinite loop when programming or you want to stop inputting text into your process. These shortcuts provide a quick solution to some of these issues.

* `CTRL+C` - Interrupts the process.

* `CTRL+D` - When a process is executing, it may await for input from the user however by using this shortcut it will close `stdin`.

* `CTRL+L` - It will clear the screen.

* `CTRL+Z` - It will suspend the process and send it to the background.

## Shell History

You can access to the shell history by doing either.

* `history` command within the shell

* `CTRL+R` which will prompt a history search
