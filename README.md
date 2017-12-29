# What does this do?
Takes one or more URLs as parameters and passes them to different user-defined programs, based on (also user-defined) regex rules.

# Config
Looks for the file **openurl.conf** inside your **XDG_CONFIG_DIRS** directories. The first line with a regex matching an URL is used to open that URL.  
Example config line, for opening YouTube videos with MPV:
```
^http.?://.*youtube\.com/.*v=.* mpv --keep-open $url$
```
First column is you URL regex, everything after it is the command to be run on the URL. Any occurence of **$url$** in the second part is replaced with the original URL.  
Having a catch-all at the bottom pointing at an actual browser is probably a good idea.  
Also have a look at **openurl.conf.example**.  

**Note**: If you have multiple different openurl.conf files in different config dirs, they are all read, in the order they appear in **XDG_CONFIG_DIRS** in.  

# Running
You can of course just put it in your **~/bin** and run it like any other script from the commandline etc., but personally I use it as my default browser, so any links I click anywhere get run through it.  
Where/how you set your default program for (http) links could vary depending on what distro/DE/whatever you're using. In case you also need a .desktop file to do so, putting **openurl.desktop** in **~/.local/share/applications/** worked for me, hopefully it does for you, too. :)
