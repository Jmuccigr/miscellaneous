---
author: John D. Muccigrosso
title: Adding Zotero to pandoc
date: Tuesday, 7 February 2017
...

# Getting started

## Zotero

1. Create an account at <http://zotero.org/>. It's free!
1. Download and install the Zotero standalone app at <https://www.zotero.org/download>.
	- Enter your account info in the **Sync** preference.
1. Download and install the browser plugin for your preferred browser.
1. Download and install the Better BibTeX plugin <https://github.com/retorquere/zotero-better-bibtex/wiki/Installation>.
	- Once installed, check the "Show citekey..." option in its **Citation** preference.

-----

## Let's add some citations

- Manually
- Via a downloaded citation file from [JSTOR](http://jstor.org/)
- Via the browser plugin

-----

To use citations, you'll need a text file containing your citations in a special format. Fortunately we can set up Zotero so that it automatically exports such a file whenever you make a change to your library.

1. In Zotero, choose "Export Library" from the **File** menu.
1. In the dialog box that opens, select the **Better CSL JSON** format.
1. Click **OK** and select a destination for the bibliography file.
1. Once the export finishes (should be a few seconds), open up the preferences and go to the Better BibTeX pane and click on the *Automatic Export* tab.
1. You should see the export you just did listed in the box. Click the radio button on "on idle" so that new exports will happen only when you're not actively working in Zotero (though it has to be open).

## Adding citations for pandoc

Now when you are writing a document and need to insert a citation:

1. Find the item you want to add in your Zotero library.
1. Note the citation key for that item.
1. Cite that work by writing the citation key in your document, preceded by `@`:  

. . .

```
    Here is some text with a citation (@Muccigrosso2011).
```

. . .

Pandoc will replace the citation key with an in-line citation and a full one at the end of the document, by default all in the Chicago Manual of Style author-date format.

-----

But to do this, pandoc needs to know where the bibliography file is. You indicate that file with the `--bibliography` option to the pandoc command. So:

    pandoc --bibliography=/path/to/your/file

. . .

If necessary, you can use `pwd` to get the path to the directory of your file. On my computer, it's:

    pandoc --bibliography='/Users/john_muccigrosso/Documents/My Documents.json'

The `'` are there in case the file name has a space in it which normally marks a word end. Alternatively you can precede any space in a file name with `\`:

    pandoc --bibliography=/home/jmuccigr/pandoc/muccigrosso/My\ Documents.json

-----

Our sample text:

    Here is some text with a citation (@Muccigrosso2011).

will now be processed into:

. . .

> Here is some text with a citation (Muccigrosso (2011)).
> 
> Muccigrosso, John D. 2011. “The 2010 Excavation Season at the Site of the Vicus Ad Martis Tudertium (PG).” *FOLD&amp;R* 227: 12. <http://www.fastionline.org/docs/FOLDER-it-2011-227.pdf>

pandoc grabbed all the information from the bibliography file and inserted it in-line and at the end of the file.

-----

If you surround the citation with square brackets, pandoc will be a little smarter about the formatting:

    Here is some text with a citation [@Muccigrosso2011].
      
    Here's a citation using the author's name in the text, followed by  
    a bracketed page reference from @Muccigrosso2011 [p. 12].

becomes

> Here is some text with a citation (Muccigrosso 2011).
> \ 
> Here’s a citation using the author’s name in the text, followed by a bracketed page reference from Muccigrosso (2011, 12).

Note how pandoc is smart about the second citation.

## Footnotes too!

One more thing: you can use citations within notes, if you want:

    This guy says blah.[^1]
                       
    [^1]: @Muccigrosso2011.

. . .

Becomes the following, with the full citation still given at the end of the document (though not shown here):
    
> This guy says blah.<sup>1</sup>  
> &nbsp;  
> &nbsp;  
> &nbsp;
> ___  
> 1\. Muccigrosso (2011).

# Formatting the bibliography

## csl Files

Another kind of text file, in a format called *citation style language* (`.csl`), is used by pandoc to format your citations. Zotero comes with dozens of them, so all you have to do is pick the one you (or the publisher) prefers and not worry about it.

. . .

The command to tell pandoc is

```
pandoc --csl=/path/to/the/csl/file
```

## Quick review

Now you can:

1. Generate a bibliography file with Zotero and have it automatically updated.
1. Make pandoc do the hard work of creating citations in the right format.
1. Include footnotes.

# Some added CLI convenience

## Aliases

You can create shortcuts—called *aliases*—for commands that you use frequently. To see what aliases are already in place, issue the command `alias`. (You may not have any!) To create an alias, use the same command with a long argument:

    alias <new command>='<existing command>'

For example, the following will create a new command, `ll`, equivalent to `ls -l`:

    alias ll='ls -l'

## The .bashrc file

When you log out, that alias will be destroyed; it lasts only for the session in which you execute it. So what's so convenient about that, if you have to create the alias every time you open a session?

. . .

When you open a new session, you're running an environment called a *shell*. The one we're running is called *Bash*. When you open up the shell, it reads and executes whatever commands are in a file in your home directory called *.bashrc*. You won't have noticed that file in your home directory because a leading `.` in a filename keeps that file from being shown by `ls` (or the GUI) unless you specify the `-a` option. 

-----

Let's edit your *.bashrc* file:

1. Once in your home directory, list **all** the files to make sure you have *.bashrc*. If you don't have one, create it with `touch`.
1. Open *.bashrc* for editing with `nano`.
1. Look for an `alias` command in the *.bashrc* file. Create one for yourself. From now on every **new** shell you create will use your new aliases.
1. To avoid the hassle of exiting your current session and re-opening a new one, simply enter `source ~/.bashrc` and the system will load the *.bashrc* file in your home directory, making your new aliases active.

## Putting it all together

Let's make our own alias to help with our use of pandoc:

1. Open .bashrc for editing via `nano`.
1. Go to the end of the file and add the following:  
   `alias pandoc='pandoc --bibiliography=/your/bibliography/file.json'`
1. Close and save the file.
1. `Source` it to make the new alias active.

. . .

From now on all your invocations of pandoc will know to use the bibliography file you specified in .bashrc, and you won't have to worry about it.


## Review of new CLI commands

1. `alias '<new command>=<existing command>'` to create a new alias.
1. `alias` by itself will display the active aliases.
1. `source <filename>` will execute the file as if it were a series of shell commands.
