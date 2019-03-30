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

* __git config__  {[ [--system] | [--global] | [--local] ]}  [[--list] | {[--get]} __*[attribute]*__  {__*[value]*__}]

  > Set or get configuration *attribute value*.

[--system]: / "Apply to system settings; stored in <installfolder>/etc/gitconfig"
[--global]: / "Apply to global settings; stored in <user>/.gitconfig"
[--local]: / "Apply to local settings; stored in <repository>/.git/config"
[--list]: / "List the attributes in the indicated settings"
[--get]: / "Get \"attribute’s\" value"
[attribute]: / "Configuration attribute to retrieve or change"
[value]: / "Content to assign to the \"attribute\""

## Creating Projects

* __git init__  {[--bare]}  {__*[destination]*__}

  > Create new repository.  Defaults to current folder (automatically creating a .git/ subfolder).

* __git lfs install__

  > Add Git LFS hooks in repository.  (Git LFS must be previously installed).

* __git clone__ {[--bare]} __*[source]*__ {__*[destination]*__}

  > Copy (clone) a *source* repository into the current folder, or the *destination* subfolder.

[--bare]: / "Create a repository with no working tree that is suitable for a remote repository; right in current folder (no .git/ subfolder)"
[destination]: / "Optional subfolder destination.  When used with \"--bare\", convention is to end destination with \".git\""

__*!!! Need to resolve exclusive switches/syntax !!!*__
* __git remote__ {[add]} {[rm]} {[prune]} {[rename] __*[oldname]*__} {[--verbose]}  __*[nickname]*__ {__*[source]*__}

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
* __git status__ {[--short]}

  > Show status of repository (added, deleted, modified, untracked, copied, and renamed files)

[--short]: / "Displays in a simplified format"

* __git lfs status__

  > Show status of repository with Git LFS details.  (Git LFS must be previously installed). 

* __[git log]__ {[-n]} {[--oneline]} {[--format]=__*[fstring]*__} {__*[since..until]*__} {[--after]=__*date*__} {[--before]=__*date*__} {[--reverse]} {[--graph]} ...  
..... {[--grep]="__*message*__"}

  > Show commit history log.

[git log]: https://git-scm.com/docs/git-log "Go to online docs"
[-n]: / "-n limits display to n commits"
[--oneline]: / "Displays a condensed history of the commits"
[--format]: / "Formats the display"
[fstring]: https://git-scm.com/docs/git-log#_pretty_formats "May be: oneline, short, medium, full, fuller, email, raw, and \"%str\".  
NOTE: Use email format to see the whole commit message, word-wrapped, on the screen."
[since..until]: / "Limits display to commits between named \"since\" and \"until\" points."
[--after]: / "Limits display to commits after the given date"
[--before]: / "Limits display to commits before the given date"
[--reverse]: / "Displays commits in reverse order"
[--graph]: / "Displays commits with text-based graphical representation of relationship"
[--grep]: / "Displays only commits that match a portion of the message"

* __[git diff]__ {{[--staged]} __*[commit1]*__} {__*[commit2]*__}

  > Display difference between two folders; by default, the working folder and virtual staged folder

[git diff]: https://git-scm.com/docs/git-diff "Go to online docs"
[--staged]: / "Shows difference between virtual staged folder and named \"commit1\""
[commit1]: / "The named commit point to compare against the virtual staged folder (if \"--staged\" given) or \"commit2\""
[commit2]: / "The named commit point to compare against \"commit1\""

* __git lfs ls-files__

  > List the files being tracked and managed by Git LFS.  Files do not appear unless they’ve been committed.
    NOTE: Nonfunctional at the time of this writing.

* __git describe__ __*[commit][desc_commit]*__

  > Show the most recent tag that is reachable from __*commit*__ with later commits suffixed.

[desc_commit]: / "The commit to get information on"

## Modifying

* __git lfs track__ {__*[filepattern]*__}…

  > Add __*filepattern*__ to Git LFS’s tracking list (in .gitattributes).  Omit __*filepattern*__ to list all current patterns.

[filepattern]: / "A string of path and filename, with or without wildcards, indicating the files that Git LFS should manage (instead of just Git).  Use apostrophes (single-quotes) around filepattern to prevent the shell from expanding wildcards into unexpected absolute names.  Multiple filepatterns may be specified."

* __git add__ {[--all]} {[--force]} {__*[filepattern][add_filepattern]*__}…

  > Add working tree’s file(s)/folder(s) contents to virtual staged folder.

[--all]: / "Includes all new files, removes all deleted files, and updates all changed files in the virtual staged folder."
[--force]: / "Adds \"filepattern\"-specified files that are otherwise ignored (as indicated by the .git/info/exclude file or the core.excludesfile configuration settings)."
[add_filepattern]: / "A string of path and filename, with out without wildcards, indicating the files to add to the virtual stage folder.  If \"filepattern\" omitted, \".\" is assumed, meaning all files in current folder and subfolders.  Multiple filepatterns may be specified."

* __git commit__ {[--amend]} {[--message] "__*string*__"}… {__*[filename]*__}…

  > Commit the current virtual staged folder into the repository.

[--amend]: / "Adjust the comment of the tip of the branch (the most recent commit)."
[--message]: / "Uses string for the commit message.  If not specified, the default editor starts up to accept the commit message.  Multiple \"--message\" parameters can be given, with each resulting in a new line in the commit message."
[filename]: / "A specific path/file to commit.  If specified, this bypasses committing the current virtual staged folder."

* __git tag__ {[--list][tag_list]} {[--delete]} __*[name]*__ {__*[commit][tag_commit]*__}

  > Create, list or delete a friendly name for a commit.

[tag_list]: / "Show the existing tags that follow the \"name\" pattern, instead of creating one.  Omit --list (and name) to show all existing tags."
[--delete]: / "Remove the named tag instead of creating it."
[name]: / "The name to tag the commit with; must not contain spaces."
[tag_commit]: / "The commit to apply the tag to."

* __git branch__ {[--list][branch_list]} {[--all][branch_all]} {[--contains]} {[--remotes]} {[--delete][branch_delete]} {[--move] __*[oldname][branch_oldname]*__} {[--merged]} {[--no-merged]} ...  
..... {[--verbose][branch_verbose]} __*[name][branch_name]*__ {__*[branch_commit]*__}

  > Create, list or delete a branch from a commit.

[branch_list]: / "Show the branches that follow the \"name\" pattern, instead of creating one.  Omit --list (and name) to show all existing branches."
[branch_all]: / "Show local and remote-tracking branches."
[--contains]: / "Show only branches that contain the indicated commit."
[--remotes]: / "Show only remote-tracking branches.  May be combined with --delete."
[branch_delete]: / "Remove the named (and fully merged) branch.  May be combined with --remotes."
[--move]: / "Rename the \"oldname\" branch to \"name.\""
[--merged]: / "Filters to show only branches whose tips are reachable by \"commit.\""
[--no-merged]: / "Filters to show only branches whose tips are not reachable by \"commit.\""
[branch_verbose]: / "When combined with \"--list,\" shows the SHA1 and commit subject line, along with relationship to upstream branch, if any."
[branch_oldname]: / "The branch to rename."
[branch_name]: / "The branch to affect."
[branch_commit]: / "The commit to reference for the operation."




[]: / ""

