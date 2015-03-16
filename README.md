# Why use wIDE?

You might be interested in *wIDE*, the *Wombat Integrated Development Environment*, if:

1. You want an ultra-lightweight IDE.

2. You use an Xwindow manager that automatically lays out your applications. (I use Xmonad, but you should be able to use wIDE with any Xwindow manager.)

3. You want to edit files using the editor and terminal of your choice.

4. You don't need an IDE to find function, variable and class definitions for you. (I might add ctags support later, but for now, wIDE is probably best suited for one-person projects.)

5. You're familiar with Unix shell scripts. (wIDE is a small shell script, so it's easy to customise and extend.)


# Prerequisites

1. Required: *dmenu*, *xsel*, the editor of your choice
1. Optional but recommended: A lightweight browser like [http://surf.suckless.org/ surf]

# Installation

  * Download and extract.

  * The file *wombat* is a shell script. Make it executable and place it somewhere on your path. If you want to use an editor other than kwrite, modify the script accordingly. (Look for the word "CUSTOMISE" to find things you might want to change.)

# More customisation (Optional)

  * You might want to add the following to your .bashrc or .bash_aliases file: *`alias wls="wombat ls"`*

  * If you use Xmonad, you can modify your *`xmonad.hs`* file to map a key to the *`wombat edit`* command. Here's an example which maps it to the *Windows+w* combination.

{{{
main =
   xmonad $ desktopConfig
    {
      -- ...other stuff...
    }`additionalKeys`
        [
        -- ...other stuff...
        , ((mod4Mask,               xK_w        ), spawn "wombat edit" )
        -- ...other stuff...
        ]
}}}

# Using wIDE

Open a terminal or console.

The command *`wombat dir`* tells wIDE to associate the current directory with the current desktop. This choice will be remembered until you change it. If you're working with multiple projects, associate the main directory for each one with a different desktop.

The command *`wombat edit`* invokes the editor. If the current selection is a filename, it will be opened. Otherwise, you will be prompted for a file to edit. The selection can include line and column information, e.g., *`myprog.c:8:15:`*; the cursor will be set to that location. _You'll be using this command frequently, so you'll probably want to create a keyboard mapping for it._

The command *`wombat ls`* (or *`wls`* if you set up the alias) lists all the "interesting" files in this directory and below. In this case, "interesting" refers to files that you're likely to want to edit. You can update the "interesting" filter by modifying the script.
