# Important Git Commands
This is a reference for commonly used or handy Git commands.  Much of it is provided as a condensed summary for quick reviews; however, certain links provide deeper detail.

|Installation                                                                        |Documentation                                                         |
|------------------------------------------------------------------------------------|--------------------------------------------------------------------|
|[Git Download (Windows)](https://git-for-windows.github.io/) (v2.18.0+ recommended) |[Pro Git Book](http://git-scm.com/book)                             |
|[Git LFS (Windows)](https://git-lfs.github.com/)                                    |[Git LFS Tutorial](https://github.com/git-lfs/git-lfs/wiki/Tutorial)|

-------------------------------------------------------------------------------
> 
> ## Legend
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
-------------------------------------------------------------------------------

## Configuring (rare)
* __config__  {[ [--system] | [--global] | [--local] ]}  [[--list] | {[--get]} __*[attribute]*__  {__*[value]*__}]  
  > Set or get configuration *attribute value*.

[--system]: / "Apply to system settings; stored in <installfolder>/etc/gitconfig"
[--global]: / "Apply to global settings; stored in <user>/.gitconfig"
[--local]: / "Apply to local settings; stored in <repository>/.git/config"
[--list]: / "List the attributes in the indicated settings"
[--get]: / "Get \"attribute’s\" value"
[attribute]: / "Configuration attribute to retrieve or change"
[value]: / "Content to assign to the attribute"

## Creating Projects
* __init__  {[--bare]}  {__*[destination]*__}
  > Create new repository.  Defaults to current folder (automatically creating a .git/ subfolder).

* __lfs install__
  > Add Git LFS hooks in repository.  (Git LFS must be previously installed.)

* __clone__ {[--bare]} *source* {__*[destination]*__}
  > Copy (clone) a *source* repository into the current folder, or the *destination* subfolder.

[--bare]: / "Create a repository with no working tree that is suitable for a remote repository; right in current folder (no .git/ subfolder)"
[destination]: / "Optional subfolder destination.  When used with --bare, convention is to end destination with \".git\""



[]: / ""