# Important Git Commands

This is a reference for commonly used or handy Git commands.  Much of it is provided as a condensed summary for quick reviews; however, certain links provide deeper detail.

|Installation                                                                        |Documentation                                                         |
|------------------------------------------------------------------------------------|--------------------------------------------------------------------|
|[Git Download (Windows)](https://git-for-windows.github.io/) (v2.18.0+ recommended) |[Pro Git Book](http://git-scm.com/book)                             |
|[Git LFS (Windows)](https://git-lfs.github.com/)                                    |[Git LFS Tutorial](https://github.com/git-lfs/git-lfs/wiki/Tutorial)|

>-------------------------------------------------------------------------------
>
> ## Legend
>
> In the syntax statements below:  
> * { } indicate optional arguments; do not type { } characters
> * [ | ] indicate mutually-exclusive arguments; do not type [ | ] characters
> * [links] provide argument descriptions when moused-over and sometimes more info upon clicking
> * normal text should be typed in exactly as shown
> * *italic* text should be replaced with custom content
> * > command descriptions appear like this
>
> [links]: / "hints"
>
>-------------------------------------------------------------------------------

## Configuring

* __config__  {[ [--system] | [--global] | [--local] ]}  [[--list] | {[--get]} __*[attribute]*__  {__*[value]*__}]  
  > Set or get configuration *attribute value*.

[--system]: / "Apply to system settings; stored in <installfolder>/etc/gitconfig"
[--global]: / "Apply to global settings; stored in <user>/.gitconfig"
[--local]: / "Apply to local settings; stored in <repository>/.git/config"
[--list]: / "List the attributes in the indicated settings"
[--get]: / "Get \"attribute’s\" value"
[attribute]: / "Configuration attribute to retrieve or change"
[value]: / "Content to assign to the \"attribute\""

## Creating Projects

* __init__  {[--bare]}  {__*[destination]*__}
  > Create new repository.  Defaults to current folder (automatically creating a .git/ subfolder).

* __lfs install__
  > Add Git LFS hooks in repository.  (Git LFS must be previously installed).

* __clone__ {[--bare]} __*[source]*__ {__*[destination]*__}
  > Copy (clone) a *source* repository into the current folder, or the *destination* subfolder.

[--bare]: / "Create a repository with no working tree that is suitable for a remote repository; right in current folder (no .git/ subfolder)"
[destination]: / "Optional subfolder destination.  When used with \"--bare\", convention is to end destination with \".git\""

!!! Need to resolve exclusive switches/syntax !!!
* __remote__ {[add]} {[rm]} {[prune]} {[rename] __*[oldname]*__} {[--verbose]}  __*[nickname]*__ {__*[source]*__}
  > Manage tracked repositories.  (Leave off switches to see a list of remotes).

[add]: / "Creates a new entry called \"nickname\" for a remote repository \"source\""
[rm]: / "Deletes the \"nickname\" remote reference"
[prune]: / "Deletes all stale remote-tracking branches that have already been removed from the repository"
[rename]: / "Changes the remote's nickname from \"oldname\" to \"nickname\""
[oldname]: / "Nickname to change"
[--verbose]: / "Shows source URL for nickname(s)"
[nickname]: / "The short name to refer to the remote repository \"source\""
[source]: / "The url of the remote repository"

## Determining State
* __status__ {[--short]}
  > Show status of repository (added, deleted, modified, untracked, copied, and renamed files)

[--short]: / "Displays in a simplified format"

* __lfs status__
  > Show status of repository with Git LFS details.  (Git LFS must be previously installed). 

* __log__ {[-n]} {[--oneline]} {[--pretty]=__*[format]*__} {__*[since..until]*__} {[--after]=__*date*__} {[--before]=__*date*__} {[--reverse]} {[--graph]} ...  
..... {[--grep]=”__*message*__”} 

  > Show commit history log.

[-n]: / "-n limits display to n commits"
[--oneline]: / "Displays a condensed history of the commits"
[--pretty]: / "Formats the display"
[format]: / "May be: oneline, short, medium, full, fuller, email, raw, and format:string.  
NOTE: Use email format to see the whole commit message, word-wrapped, on the screen."
[since..until]: / "Limits display to commits between named \"since\" and \"until\" points."
[--after]: / "Limits display to commits after the given date"
[--before]: / "Limits display to commits before the given date"
[--reverse]: / "Displays commits in reverse order"
[--graph]: / "Displays commits with text-based graphical representation of relationship"
[--grep]: / "Displays only commits that match a portion of the message"




[]: / ""

