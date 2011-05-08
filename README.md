#Play! "_Open file from errors pages_" launcher for IntelliJ 

In your Play! application's `application.conf` file you'll find this section of commented out code

    # Open file from errors pages 
    # ~~~~~ 
    # If your text editor supports opening files by URL, Play! will 
    # dynamically link error pages to files 
    # 
    # Example, for textmate: 
    # play.editor=txmt://open?url=file://%s&line=%s

### Wouldn't it be cool to be able to replace `txmt://` with `idea://`?

This little applescript does just that by adding a custom *idea:// protocol* that launches the script
when called by Play!. The script is fed the file path and the line number form the error page and
passes this on to IntelliJ's internal xml-rpc based file opener server.


