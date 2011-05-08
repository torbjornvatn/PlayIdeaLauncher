#![Play logo](https://github.com/downloads/torbjornvatn/PlayIdeaLauncher/play_logo.png) _"Open file from errors pages"_ launcher for IntelliJ
            

In your Play! application's `application.conf` file you'll find this section of commented out code

    # Open file from errors pages 
    # ~~~~~ 
    # If your text editor supports opening files by URL, Play! will 
    # dynamically link error pages to files 
    # 
    # Example, for textmate: 
    # play.editor=txmt://open?url=file://%s&line=%s

**Wouldn't it be cool to be able to replace `txmt://` with `idea://`?** 

This little applescript does just that by adding a custom **idea://** protocol that launches the script
when called by Play!. The script is fed the file path and the line number from the error page and
passes this on to IntelliJ's internal xml-rpc based file opener server.

## Prerequsites

You need to have [xmlrpc](http://xmlrpc-c.sourceforge.net/) located in `/usr/local/bin/xmlrpc` 

If you install it with `brew install xmlrpc-c` this location is the default. If your xmlrpc executable is located elsewhere you have to alter the path inside `PlayIdeaLauncher` using the AppleScript Editor.

## Installation

1. [Download the application](https://github.com/torbjornvatn/PlayIdeaLauncher/archives/master)
2. Place it on your path and chmod it to be executable.

I like to place it in `~/bin`, but it can go anywhere on the $PATH.

## Usage

The next step is to uncomment and alter the play.editor property in your Play! application and
replace **txmt** with **idea**

Then that portion of the `application.conf` file should look like this

    # Open file from errors pages 
    # ~~~~~ 
    # If your text editor supports opening files by URL, Play! will 
    # dynamically link error pages to files 
    # 
    
    play.editor=idea://open?url=file://%s&line=%s

If you now click on a line in a Play! error page, IntelliJ will open on that line in the file
containing the error. 

**Enjoy!**
