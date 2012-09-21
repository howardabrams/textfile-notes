Not sure if you've read the description about [my note taking
system][1], but I thought that my `notes` script for analyzing text
files might be useful to share.

Usage
-----

    notes [-a] <action> [-r|-p] [-n <names>] [-t <tags>] ...

This script searches through text files in the folder/directory: `~/Dropbox/Notes`
as if they were *notes*. This script can help you search and manipulate them.

The first argument is an *action* that tells the script what to do:

  * `list`     - Lists all of the note filenames. Useful with `-t` option.
  * `find`     - Searches the notes that contain a particular string
  * `view`     - Converts a markdown formatted note into HTML. Opens in browser.
  * `all-tags` - List all of the tags used in all notes.
  * `export`   - Export some notes as HTML into the directory: `~/Sites/Notes`

The command actions accept the following parameters:

  * `-a <action>` for specifying the action or command to do.
  * `-n <name>`   for working with files whose names match this argument
  * `-t <tags>`   for working with files that have all the tags given
  * `-r`          for raw output format (full note names and whatnot)
  * `-p`          for print-printing the output (trimmed filenames)


Installation and Setup
-------------

Just do the following three steps:

  1. Install either the [Markdown][2] or [MultiMarkdown][3] scripts
  2. Install the [OpenMeta][4] binary file.
  3. Place the `notes` script (and other binaries) somewhere in your `$PATH`.

I recommend adding the following to your `.bashrc` (or equivalent):

    export NOTEDIR=$HOME/Dropbox/Notes
    export NOTEDEST=$HOME/Sites/Notes

    alias notes-find="notes -a find"
    alias notes-view="notes -a view"
    alias notes-list="notes -a list"
    alias notes-export="notes -a export"

These alias make tab-completion a wee bit easier.


OpenMeta Wrapper
----------------

I like the concept that meta data (like tags) can be stored with a file, but not
*inside* the file. However, the interface to [OpenMeta][4] is quite crufty,
so unless you use something like [Notational Velocity (Alt)][5] to set your
tags, you might appreciate the [tagit][6] wrapper.

To use it, simply source it into your shell, e.g.

    source $HOME/.notes/notes-tag-helper

This gives you the following commands:

 * `tags <file>`      - Lists all the tags for a note (or other relative file)
 * `tag-clear <file>` - Removes all tags from a note (or file)
 * `tag-add <tag ...> <file>`   - Adds one or more tags to a note
 * `tag-set <tag ...> <file>`   - Sets the tags to just the ones listed


Questions
--------------

*Why did you write them as shell scripts?*

These shell scripts are not very fast, but I wanted to make it easy
for anyone to fork, and adapt this script to new environments and
usage style.

That said, if anyone wants to take the ideas and redo them in
something faster, that'd be pretty cool.


Tasks
-----

What can you expect in the next revision? Probably:

  * I need to re-write my script to gather up all of the tags used in all
notes and put them in a list. I find this pretty helpful at times.

  * The results of the `export` command is pretty spartan, and it would be
nice to include nicer stylesheets/javascript in order to read through
the notes.


  [1]: http://www.howardism.org/Technical/My_Note_Taking_System.html
  [2]: http://daringfireball.net/projects/markdown/
  [3]: http://fletcherpenney.net/multimarkdown/
  [4]: http://code.google.com/p/openmeta/
  [5]: http://brettterpstra.com/project/nvalt/
  [6]: notes-tag-helper