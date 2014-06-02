<!---
# Author: Ethan Alan Hereth
# Contact: ethan-hereth@utc.edu
#
# Please submit corrections, bugs, and/or typos to the contact above.
-->

![the official Vim icon] (http://www.vim.org/images/vim_editor.gif "the
official Vim icon")

What is Vim?
============

Vim is a (programmer's) modal text editor based of the legacy Vi editor written
by Bill Joy in '76. Vim stands for "Vi iMproved" and it is an open source,
multi-platform project created and maintained by Bram Moolenaar. There is a
large number of dedicated contributors that help maintain Vim.

Vim can be obtained, free of charge, at [vim.org] (http://www.vim.org). It
should be noted that Vim is charityware, which means that you do not have to
pay anything for it, but if you love Vim you can 'pay' for it by donating to
Bram's charity [ICCF Holland] (http://www.iccf-holland.org) which supports
needy children in Uganda.

A few things to know before you start reading this overview:

* Vim is a modal editor (`:help vim-modes`) which means you enter text in one
'mode' (insert mode) while you navigate your document and run commands in a
different 'mode' (normal/command mode.) Anything you come across in this text
that starts with a colon (`:`), for example `:wqa`, is a Vim command (an Ex
command really, but I'll leave it at that) that must be run from normal/command
mode. From *any* mode in Vim you can get into normal mode by pressing the
escape (`esc`) key and simply typing the command as you see it.

* When you open a file with Vim, it is loaded into what Vim calls a 'buffer';
the buffer is written to the file on disk every time you save/write the buffer.

* There is a GUI version of Vim, simply called 'Gvim', for those of us who
like to keep our terminal free for other things.

Why use Vim?

* It is on virtually every Linux machine.
* It can make you a much more efficient coder.
* It is *very* extensible.

What are alternatives? Emacs, Sublime Text 2, are among the most popular, see
this Slant.co [link]
(http://www.slant.co/topics/12/~what-is-the-best-programming-text-editor) as a
reference.

Getting Help
=============
Vim can be a daunting editor to start using; it has a steep learning curve. You
will need to know how to get help.

* Start with vimtutor: from a terminal in Linux run the command `vimtutor` and
simply follow the instructions. On other platforms the way you run the tutor
might be different; consult the help (`:help tutor`).

* Vim's built in help is extensive and exhaustive (and overwhelming?), access
the help pages by running the command `:help` or `:help
"command-I-don't-understand"`. There is even a help page about the help pages!
`:help help`. The help page can often be accessed by pressing the `<F1>` key as
well. When you are done, use `:q` to close the help window.

 * Good places to start perusing the help:
  * `:help help.txt` or simply `:help`.
  * `:help usr_toc.txt` table of contents.
  * `:help usr_01.txt` explain and describe the help manual.
  * `:help usr_02.txt` "The first steps in Vim"
  * etc... These "usr_##.txt" pages pretty much do what I am attempting to do
  with this document, but *much* better and *much* more detail.

 * Pay special attention to the following bit of text, pulled directly from
 Vim's help, which will help you to understand *how* to maneuver the help text.

> As you read the help text, you will notice some text enclosed in vertical bars
> (for example, |help|).  This indicates a hyperlink.  If you position the
> cursor anywhere between the bars and press CTRL-] (jump to tag), the help
> system takes you to the indicated subject.  (For reasons not discussed here,
> the Vim terminology for a hyperlink is tag.  So CTRL-] jumps to the location
> of the tag given by the word under the cursor.)
>     After a few jumps, you might want to go back.  CTRL-T (pop tag) takes you
> back to the preceding position.  CTRL-O (jump to older position) also works
> nicely here.
>     At the top of the help screen, there is the notation *help.txt*.  This name
> between "*" characters is used by the help system to define a tag (hyperlink
> destination).

* Other ways to get help:
 * `:helpgrep` a way to seach the help pages for something specific.
 * [Google.com] (http://www.google.com) well, there is always Google!
 * [Vim's wiki] (http://www.vim.wikia.com) there is a lot there.
 * [Learn Vimscript the Hard Way]
   (http://learnvimscriptthehardway.stevelosh.com) by Steve Losh.

* There are *way too many* cheat sheets, find one or two you like, keep them
next to your keyboard until you do not have to look at them anymore. A few that
I like:
 * [Graphical Vim Cheat Sheet]
 (http://www.viemu.com/a_vi_vim_graphical_cheat_sheet_tutorial.html) this is
 one of the first ones I really used.
 * [Beautiful Vim Cheat Sheet Poster] (http://vimcheatsheet.com/) this was a
 very successful kickstarter project not too long back.

Normal/Command Mode
====================
In this mode, you move around in the file and run commands. This is Vim's
default mode, when you run Vim for the first time you will be in normal mode.
You can return to normal mode from any other mode by pressing the escape key
(`esc`).

Opening files in Vim
--------------------

How do you tell Vim what file to edit? There are, as usual, many ways. Here are
a few of the methods I use most.

* From a terminal in Linux/OSX:
 * `vim <filename>` open the file <filename> in terminal Vim.
 * `gvim <filename>` open the file <filename> in gui Vim.

* From within an already running instance of Vim:
 * `:edit <filename>` replace current buffer with the contents of <filename>.
 * `:split <filename>` split the current window horizontally and open
 <filename> in one of the new windows.
 * `:vsplit <filename>` split the current window vertically and open
 <filename> in one of the new windows.

Saving and Quitting
-------------------
(`:help writing` or `:help quit`)

Help, how do I quit Vim and save my changes? If you have ever had to edit a
file using an unfamiliar text editor this can be a huge pain in the neck, and
even dangerous if you do something wrong and exit the editor without saving...
Yuck!  Here is how you save changes and/or exit Vim.

* `:w` save changes to a file in Vim. Save early and save often should be
everyone's mantra! (I am **not** kidding.)
* `:wq` write file and quit Vim.
* `:x`/`ZZ` write the file *only* if there are changes and quit Vim.
* `:q` quit Vim; this will fail if there are changes to the buffer.
* `:q!`/`ZQ` quit Vim without saving any changes, make sure that you *really*
want to do this if you hit enter any changes are **gone**. I mean **gone**.

There are versions of these commands for instances of Vim containing multiple
files/buffers:

* `:wa` save changes to all buffers.
* `:wqa` save all changes, close all windows and exit Vim.
* `xa` write the files *only* if there are changes and quit Vim.

Moving around in normal mode
----------------------------
(`:help navigation`)

Most of you movement in Vim *should* take place from normal mode. Try to learn
to NOT use the arrow keys/mouse, most Vim aficionados will swear that you will
be **much** more efficient if you learn to keep you hands on they keyboard.

* Basic movements: the following are what I consider to be the most basic,
albeit sometimes least powerful, movement commands in Vim. The most fundamental
Vim movements are the `h`/`j`/`k`/`l` commands; these will be the first
movement commands you will learn in Vim. These are all on the home row, you do
not have to move your hand from the keyboard.

 * `h` moves one character left.
 * `j` moves one line down.
 * `k` moves one line up.
 * `l` moves one character right.

* More basic movements:
 * `0` moves to the beginning of the line.
 * `^` moves to the first non-blank character of the line. (This is slightly
 different than the `0` command, I usually use `^`).
 * `$` moves to the end of the line.
 * `#|` moves to the '#'th column of the line.

* Word movements: moving around this way can be significantly faster than
using the movements above. Note that the capital variants of these commands
operate on 'WORD's instead of 'word's, please see `:help WORD` or `:help word`
for the details.
 * `w` (`W`) move forward to the beginning of the next word (WORD).
 * `e` (`E`) move forward to the end of the next word (WORD).
 * `b` (`B`) move backward to the beginning of the previous word (WORD).
 * `ge` (`gE`) move backward to the end of the previous word (WORD).

* Advanced linewise movements: these are, in my opinion, the most powerful
linewise movement commands Vim offers. Their main limitation is that they are
limited in scope to the line they are used from. Note that these movements can
be repeated with the `;` and `,` commands; `;` moves to the next match in the
*same* direction as the original movement and `,` moves to the next match in
the opposite direction.

 * `f{char}` move right to the first occurrence of `{char}` in the line.
 * `F{char}` move left to the first occurrence of `{char}` in the line.
 * `t{char}` move right until the first character before `{char}` in the line.
 * `T{char}` move left until the first character before `{char}` in the line.

 * Mnemonic: think of `f`/`F` as find and `t`/`T` as 'till.

* File movements: I call these set of movement commands 'file' movements
because they represent ways to quickly move around the entire file; the scope
of these movements are 'global' to the buffer.

 * `gg` move to the first line of the file.
 * `G` move the the last line of the file.
 * `:#` move to the '#' line of the file.
 * `ctrl-b` equivalent to page up, see `ctrl-y` and `ctrl-u` for more upward
 scrolling movements.
 * `ctrl-f` equivalent to page down, see `ctrl-e` and `ctrl-d` for more
 downward scrolling movements.
 * `#%` moves to (nearly) the '#'th percent of the file.

* Marks (`:help mark`): marks are a convenient way to 'remember' specific
locations in a Vim buffer. Marks can even be used to defines ranges in a text
file; see `:help ranges` if this piques your interest.
 * `m{char}` set a mark specified by `{char}` at the cursor location. Note that
 uppercase marks are global (valid between files) and lowercase marks are local
 to a single file.
 * `'{char}` jumps to line containing the mark `{char}`.
 * ```{char}`` jumps to the exact position of the mark `{char}`.

 * Special marks: there other marks automatically defined by Vim that can be
 quite useful.
  * `'.` or ```.`` jump to the position of the last change.
  * `''` or ```'`` jump to the position of the last jump.
  * There are more, read the help if you are intrigued.

Copying and Pasting
-------------------
(`:help yank` `:help put`)

The way Vim does copying and pasting is perhaps one of the more difficult Vim
concepts to learn. First, 'copy' in Vim is 'yank' and 'paste' is 'put',
acquaint yourself with that terminology. In Vim one yanks into and puts from
'registers' (`:help registers`). By default yanked text goes into the 'unnamed
register' `"` (not sure why it is called that) but you may also yank into, put
from specific (named) registers.

* Yanking
 * `y{motion}` yank text included by `{motion}` (see section on Operator
 and Operator Pending Mode or `:help motion`).
 * `yy` yank current line.

* Putting
 * `p` put copied text after the cursor.
 * `P` put copied text before the cursor.

Using named registers: text may be yanked/put from custom/named registers which
can be one of the {a-z/A-Z} characters. Note that text can be appended to a
named registers by using the uppercase case version of the register;
accumulating yanked text is sometimes useful. To use a named register, simply
prepend the above yank/put commands with `"<reg>`, i.e.`"<reg>yy` or `"<reg>p`.

* **Pro-tip**: yank/put from the system clipboard with `"+y{motion}`/`"+p`.

Deletion
--------
(`:help deleting`)

Deleted text goes into the default, unnamed register and can be put as outlined
in the above section.

* Simple deletion:
 * `x` delete character under the cursor.
 * `X` delete character behind the cursor.
 * `d{motion}` delete text included by {motion} (see section about Operators
 and Operator Pending Mode or `:help motion`).
 * `dd` delete current line.
 * `D` delete from the character under the cursor to the end of the line.

* Deletion with insertion: these are handy ways to delete text and immediately
enter insert mode and enter text.
 * `r` replace character under cursor.
 * `R` replace characters under cursor as you type, Vim calls this 'Replace
 mode'.
 * `c{motion}` change text included by `{motion}` (see section about Operators
 and Operator Pending Mode or `:help motion`, this is the last time I will say
 this.)
 * `cc` change current line.
 * `C` change from the character under the cursor to the end of the line.
 * `s` substitute character under cursor with typed text.
 * `S` substitute character under cursor until the end of the line with typed
 text.

Undoing and Redoing
-------------------
(`:help undo`)

Crap! I messed up... Vim can fix it. If `:set nocompatible` is set, you can
undo changes up unto the number of changes remembered by the value specified by
the `undolevels` option; see `:help undolevels` or `:help undo-remarks`.

* `u` undoes most recent change.
* `ctrl-r` redoes the most recent undone change.

Searching
---------
(`:help search-commands`)

Find stuff in your program. (Searches can be used as the target of `{motions}`
in operator pending mode.)

* Forward search:
 * `/{pattern}` search forward in buffer for `{pattern}`.
 * `*` search forward in buffer for word under the cursor.

* Backward search:
 * `?{pattern}` search backward in buffer for `{pattern}`.
 * `#` search backward in buffer for word under the cursor.

* Repeating the search: you can jump to the next/previous search `{pattern}`
easily to find the perfect match.
 * `n` repeat last search
 * `N` repeat last search in the opposite direction.
 * There are even more ways to repeat searches, read the manual.

There are useful and flexible ways to search a text in a case sensitive or
insensitive manner. The settings that I find most useful are: `set ignorecase`
and `set smartcase` (`:help ignorecase`, `:help smartcase`). If `ignorecase` is
on and `smartcase` is off, searching for foo or Foo will find the text foo,
Foo, FOO, fOo, foO, and fOO.  However, if `smartcase` is also on, the search
will become case sensitive as soon as a capitol character is included in the
pattern; i.e. searching for fOO will *only* find the word fOO. Another way to
force case sensitive/insensitive searching without these settings is to use
`\c` and `\C` in the search pattern (`:help \c`, `:help \C`).

Search and Replace
------------------
(`:help substitute`)

Vim's search and replace feature is very powerful, extremely useful, and a
programmer's greatest boon. Search and replace is instantiated using the
following incantation: `:[range]s/{pattern}/{replacement}/[flags]`. Wow, let's
break that apart:

* `[range]` defines the section of text you want to include in your
search-and-replace (`:help range`). If it is left out, the search-and-replace
operates only on the current line. An extremely useful range is `%`, which
represents the entire file.

* `s` stands for `substitute` or 'search-and-replace'.

* `{pattern}` is a normal search pattern, as outlined in the previous section,
and represents the text you desire to replace.

* `{replacement}` is the text you want to replace `{pattern}` with: the
substitution.

* `[flags]` these are optional flags that modify the way the substitution
behaves, see `:help s_flags`. Without any `[flags]` the substitution only
occurs on the first match found; some useful `[flags]` are listed below.

 * `g` replace all matches found in `[range]`.
 * `c` confirm each substitution; good if you want be extra sure you are not
 messing anything up!
 * `n` report how many substitutions this search-and-replace will cause, do not
 actually make any changes.

Regular expressions (`:help pattern`, `:help usr_27.txt`) can turn a 'normal'
search pattern into a 'super' search pattern. Regular expressions are
complicated, confusing, convoluted, but **powerful**!! See [this xkcd comic]
(http://www.xkcd.com/1171) and [this one] (http://www.xkcd.com/208) and [this
one] (http://www.xkcd.com/1313) as references.

Here I will give same basic Regular expressions to whet your appetite.

* `*` match zero or more times, e.g. `/a*` matches "", "a", "aa", "aaa", ...
* `\+` match one or more times, e.g. `/a\+` matches "a", "aa", "aaa", ...
* `\=` match zero or one times, e.g. `/ints\=` matches "int", and "ints"
* `.` match anything but the end-of-line, e.g. `/foobar.` matches "foobar", "foobarz", "foobar!", ...
* `^` match only at the beginning of the line, e.g. `/^foobar` matches the word
"foobar" but **only** at the beginning of a line.
* `$` match only at the end of the line, e.g. `/foobar$` matches the word
"foobar" but **only** at the end of a line.

* Read about them, they can be very, **very** helpful.

Operators and Operators Pending Mode
------------------------------------
(`:help operator`, `:help Operator-pending`)

Operators in Vim are commands that require a motion to tell Vim how far/how
much text to operate on before they are complete, hence they do not work by
themselves. Quoting directly from Vim's help: "these operators generally delete
or change text." Operator pending mode is the mode Vim is in between the time
you enter an operator command and supply it the required motion to complete the
command.

* Examples:
 * `dj` deletes the current line and the line below it.
 * `cfd` deletes the text from under the cursor up to and including the first
 'd' character in the line. (This command will fail if there exists no 'd'
 character in the line to the right of the cursor.)
 * `Vgg` visually select (linewise) all text from the current line to the top
 of the file.

Let me introduce yet another Vim nicety: Text objects. Text objects are clever
and useful Vim constructs; read about them at `:help text-objects`. They are
used as the `{motion}` to an operator command and they come in two flavors: 'a'
objects and 'i' objects. As a mnemonic, I think about 'a' as meaning 'around'
and 'i' as standing for 'inner'. You will probably need to read the help and
play with these before you really grok them, they are hard to explain. Note it
is **important** to understand that the cursor can be *anywhere* in the object
for these to work; this is one of the reasons they are so powerful. For
example, you can visually select the entire word
'supercalifragilisticexpialidocious' with `viw` even if the cursor is on the
last 'u' in the word. Here I will list some of the text objects I use most
often:

* `aw` (`aW`) around word/WORD, around in this sense will include whitespace
around the word.
* `iw` (`iW`) inner word/WORD, this motion will **not** include whitespace
around the word.

* `a(`/`a)` around a "() block", around in this sense will include the
parenthesis. Vim provides the command `ab` as an easier to type alias of this
object.
* `i(`/`i)` inner "() block", this 'inner' object will **not** include the
parenthesis. Vim provides the command `ib` as an easier to type alias of this
object.
* There exists two more text-objects, analogous to the "() block" object just
described, that are very useful:
 * The "{} block": the around flavor is `a{`/`a}`, the inner flavor is
 `i{`/`i}`, it also has an alias `aB` and `iB`.
 * The "[] block": the around flavor is `a[`/`a]`, the inner flavor is
 `i[`/`i]`, this object has no alias.

* I assume you get the idea; I will, however, mention a few more I use from
time to time.
 * `as`/`is` around/inner sentence.
 * `ap`/`ip` around/inner paragraph.
 * `a"`/`i"` around/inner double quoted string.
 * `a'`/`i'` around/inner single quoted string.

* Examples:
 * `daw` deletes word in cursor including surrounding whitespace.
 * `vis` visually selects the sentence containing the cursor.
 * `yi"` yanks the text inside a double quoted string containing the cursor.

Insert Mode
===========
This is the Vim mode with which you actually enter text. You will likely spend
less time in insert mode then you might initially expect. There are a few ways
to enter insert mode from normal mode.  To get out of insert mode back into
normal mode press `esc`.

* Getting into insert mode: here is how you actually enter text in Vim!
 * `i` insert text before the current cursor position.
 * `I` insert text at the beginning of the current line.
 * `a` append text after the current cursor position.
 * `A` append text at the end of the current line.
 * `o` begin a new line below the current line and insert text.
 * `O` begin a new line above the current line and insert text.

Insert mode completion
----------------------
(`:help ins-completion`)

Vim can auto complete some text for you as you type. Entire lines,
keywords, dictionary words, tags, file names, spelling suggestions, among
other things can be auto completed in Vim if you talk to it just right.

The most common case: simple keyword completion. If you are typing a word that
you have entered already at least once in the current file, press `ctrl-n` and
a menu will pop up with all the words Vim thinks you intend to insert. In the
case there is only one option it will be inserted for you. Pressing `ctrl-n`
again will cycle you forward through the menu and pressing `ctrl-p` will cycle
you backward in the menu.

* A cool example: `ctrl-x ctrl-l` will try to auto insert entire lines of text
if they have been type previously in the file.

Visual mode
===========
In Vim's visual mode, text can be visually selected character-wise, line-wise,
and column-wise. Text that has been visually selected can be yanked, deleted,
changed, and otherwise manipulated easily without modifying anything else.

Entering visual mode:

* `v` enter character-wise visual selection; use any normal mode movements to
select the desired text.
* `V` enter line-wise visual selection; move the cursor around to select the
desired lines of text.
* `ctrl-v` enter column-wise/block visual selection; move around to select
columns of text.

More detail about visual block selection. This is a most handy tool for
programmers. After selecting a block of text, you may insert text in front of
or behind the block.

* `I` inserts text before the visual block.
* `A` appends text after the block.
* `$A` appends text at the end of a misaligned/jagged visual block.

* **Pro-tip**: `gv` reselects last visually selected area!

Windows
-------
(`:help windows`)

With Vim you can edit multiple text files at the same time in multiple windows.
There are keyboard shortcuts that can be used to manipulate and move between
windows; window commands start with the `ctrl-w` keyboard combination.

Window creation commands:

* `ctrl-w s`/`:split <filename>` split the current window horizontally. By
default the same file is open in both windows; the `:split` variant may be
given a file name to be opened in the split.
* `ctrl-w v`/`:vsplit <filename>` split the current window vertically. The
comments from the `ctrl-w s`/`:split` bullet above apply here too.
* `ctrl-w n`/`:new` open a new window and start editing a new file in it.
* `ctrl-w o`/`:only` close all window but the one containing the cursor.

Moving between windows: now that you have split windows, how do you switch to
them?

* `ctrl-w h` switch to the window to the left.
* `ctrl-w j` switch to the window below.
* `ctrl-w k` switch to the window above.
* `ctrl-w l` switch to the window to the right.
* If the mouse is enabled (`:help mouse`) you can select the window you want to
edit with your mouse too.

Here are some handy mappings I use to make switching windows a little less
aerobatic on my fingers:

* `nnoremap <C-h>  <C-w>h` map the key sequence `ctrl-h` to `ctrl-w h`.
* `nnoremap <C-j>  <C-w>j` map the key sequence `ctrl-j` to `ctrl-w j`.
* `nnoremap <C-k>  <C-w>k` map the key sequence `ctrl-k` to `ctrl-w k`.
* `nnoremap <C-l>  <C-w>l` map the key sequence `ctrl-l` to `ctrl-w l`.

Moving windows around:

* `ctrl-w r` rotate windows downwards/rightwards.
* `ctrl-w R` rotate windows upwards/leftwards.
* `ctrl-w x` exchange current windows with the next one.
* There are more, see `:help window-moving`.

Resizing windows:

* `ctrl-w =` make all windows as equally sized as possible.
* `ctrl-w +` make current window taller.
* `ctrl-w -` make current window shorter.
* `ctrl-w >` make current window wider.
* `ctrl-w <` make current window narrower.
* There are more, see `:help window-resize`.

Tabs
----
(`:help tabpage`)

There are also tabs in Vim, I don't use them much but if you like tags, read
the manual.

Personalization and Customization:
==================================
Vim is virtually limitless, you can personalize and customize it to meet your
every whim. Here are some of the ways you can begin to tune Vim to fit your
liking.

The .vimrc
----------
(`:help vimrc`)

There are *so* many ways I want to customize/personalize the default behavior
of Vim to suite my fancy, how can I make these customizations permanent? Vim
reads a file called the vimrc file when it starts up to load user settings,
this is where you put settings you want to be permanent. On Linux machines the
users default vimrc file is located in their home directory is is named
".vimrc". This location may vary so read the help page if you are curious. (For
some reason the vimrc file's default name on Windows machines is "_vimrc".)

Be sure to comment you settings in your .vimrc, so you will be sure to
remember what the option does and why you set it that way. Comments begin with
the `"` character in the .vimrc file and they can go almost anywhere, but I
would try to keep them on their own lines.

Abbreviations
-------------
(`:help abbreviate`)

What I really meant was... You can make Vim correct your most common typos
automatically. You can make Vim insert some large piece of text you repeatedly
have to type on a day to day basis (copyrights, licences, signatures, etc.)
Vim's `abbreviate` command can make this happen; its syntax is `:abbreviate
{lhs} {rhs}` where `{lhs}` gets replaced by `{rhs}` whenever it is typed.

* Examples:
 * `:abbreviate teh the` replaces 'teh' with 'the' anywhere it is mistyped.
 * `:iab myif if ()<CR>{<CR>}<ESC>kk^f)i` enters a C style if statement ready
 to be filled in.
 * `:iab #i #include` insert a C style `#include` preprocessing macro.
 * `:iab @@ ethan-hereth@utc.edu` insert my email.
 * `:iab mysig --<CR>Ethan Hereth<CR>ethan-hereth@utc@edu` insert my signature.

There are variants to this command:

* `:iabbreviate` create an abbreviation that works in insert mode only.
* `:cabbreviate` create an abbreviation that only works in command mode.
* `:unab`/`:uniab`/`:uncab` clear (or unabbreviate) the abbreviations.

Maps
----
(`:help map-commands`)
Maps change the meaning of typed keys, they can make complicated editing tasks
a keystroke away. There are *lots* of versions of the map command depending on
which modes you need the map work in, you really do need to read the help.

You almost always you want the `nore...` versions to avoid recursive mappings.
For example, think about what might happen if the following two maps are
defined: `:map j G` and `:map k j`, and you try to use the `k` to move down a
line. Try it if you dare! This is why using `:noremap` is important.

* Some maps I like:
 * `:noremap Y y$` make `Y` behave like `D` and `C`
 * `:noremap <BS> <PageUp>` make the backspace key act like pageup.
 * `:noremap <Space> <PageDown>` make the space key act like pagedown.
 * `:noremap <Leader>ss :setlocal spell!<CR>` toggle spell check.

Some more examples of how the `:map` command can be used:

* `:map <F2> a<C-R>=strftime("%c")<CR><Esc>` inserts current date and time
after the cursor if you press `<F2>`.
* `:inoremap jk <esc>` some people do not like reaching all the way to the
`esc` key to switch modes, this map fixes the problem.

Make yourself learn it; map "bad" keys to `<nop>`:

* `:noremap <UP> <nop>` make the up arrow key do nothing in normal mode.
* `:noremap <DOWN> <nop>` make the down arrow key do nothing in normal mode.
* `:noremap <RIGHT> <nop>` make the right arrow key do nothing in normal mode.
* `:noremap <LEFT> <nop>` make the left arrow key do nothing in normal mode.

Color schemes
-------------
(`:help colorscheme`)

You can change the way Vim looks by default. There are a number of different
colorschemes that should come with the default Vim installation. You can change
the colorscheme by executing (`:colorscheme <TAB>`), this should bring up a
list of available colorschemes which you may try out until you find one that is
pleasing to your eye.

There are also *many* colorschemes available on the internet; Google "Vim
colorschemes" if you would like to see what else is out there. My personal
favorite is called 'solarized', you will find it [here]
(https://github.com/altercation/vim-colors-solarized).

Setting options
---------------
(`:help set`)

Vim has hundreds of options that can be set to effect the way it behaves.
There are three flavors of options: boolean options which can only be on or
off, number options which have numeric values, and string options which take
strings as their values.

* Querying current option values:
 * `:set all` display all current settings.
 * `:set` display current settings that have been changed from their defaults.
 * `:set {option}?` displays the `{option}`s current value.

* Setting boolean options: boolean options can be set in a couple ways.
 * `:set {option}` switches `{option}` on.
 * `:set no{option}` switches `{option}` off.
 * `:set {option}!`/`:set inv{option}` toggle the boolean option.

* Setting number and string options:
 * `:set {option}={value}`/`:set {option}:{value}` set either the string or
 number `{option}` to `{value}`.
 * `:set {option}+={value}` add `{value}` to a numeric `{option}` or append it
 to a string `{option}`.
 * `:set {option}^={value}` multiply a numeric `{option}` by `{value}` or
  prepend `{value}` to a string `{option}`.
 * `:set {option}-={value}` subtract `{value}` from a numeric `{option}` or
 remove it from a string `{option}`.

Note that an option can be reset to its default value by `:set {option}&`.

'Must have' settings: below are a few options that I use. Remember, if you are
not quite sure what I am talking about, consult the help: `:help {option}`.

* `:set nocompatible` be incompatible with old style Vi. Trust me, you **do**
want this setting, it should be the very first option set in your .vimrc.
* `:set textwidth=#` create a new line of text once the line extends past '#'
characters.
* `:set backspace=2` make the backspace key behave in a 'sane' manner.
* `:set autoindent` try to figure out how the text/code should be indented.
* `:set smartindent` really try to figure out how the code should be indented.
* `:set tabstop=#` define how many spaces a tab character should be.
* `:set expandtab` turn tabs characters into spaces (I really do not like tab
characters in my files.)
* `:set shiftwidth=#` number of spaces to insert when indenting.
* `:set incsearch` show matching text as it is typed.
* `:set hlsearch` highlight matching search patterns.
* `:set ignorecase` match case-insensitively.
* `:set smartcase` be case sensitive intelligently.
* `:set syntax on` enable automatic syntax highlighting.
* `:set filetype on` enable automatic filetype detection.
* `:set filetype plugin on` have Vim load its filetype plugins.
* `:set filetype indent on` enable automatic indention of recognized filetypes.

Other nice settings:

 * `:set ruler` show more information in the status line, controlled by
 `rulerformat`.
 * `:set number` show line numbers to the left of the buffer.
 * `:set relativenumber` like `:set number` but line numbers are relative to
 the cursor.
 * `:set hidden` allow switching of buffers even if there are unsaved changes.
 * `:set showmode` show info about the current mode in the command line.
 * `:set showmatch` show matching bracket if it is found.
 * `:set mouse=a` enable mouse in Vim.

Did I mention `:set nocompatible`?

Customize Vim's status line
---------------------------
(`:help statusline`, `:help status-line`)

Vim windows can have be configured to have a status line that takes up the last
line of the buffer. This status line can be configured to contain extra
information about the buffer. This feature can be quite useful, powerful, but
it can also become quite cumbersome and complicated; Fortunately, there are
very nice plugins that can make this easier and prettier; see the section below
about plugins.

The simple example below, shamelessly plagiarized from Chapter 17 of Steve
Losh's ["Learn Vimscript the Hard Way"]
(http://learnvimscriptthehardway.stevelosh.com/) configures Vim's status line
to display the line number of the cursor position with respect to the total
number of lines in the file. Try it out to get a feel for the status line.

* `:set statusline=Current:\ %4l\ Total %4L`

I also personally recommended configuring Vim to always show the status line by
setting the `laststatus` option like `:set laststatus:2`.

Plugins!:
=========
Vim has its own scripting language called Vimscript or VimL for short. This
scripting language can be used to extend Vim's functionality "to infinity and
beyond"! I am not very experienced with using VimL so I will not say much more
about it than stating that it exists, and plenty of people smarter than me use
it to make Vim even better.

There is a plethora of available plugins available to extend Vim's
functionality, there are almost no end to the possibilities. You almost surely
will find one that does *something* you will find helpful, even indispensable.
[Github] (http://www.github.com) is a great place to look for plugins as is
Vim's official [plugin repository] (http://www.vim.org/scripts/).

Before I go any farther, __Use a plugin manager__. The way plugins are
installed can be confusing and error prone, there are plugin managers that take
care up this for you and even help you keep your plugins up to date. Spend a
few minutes picking one of the following available options; I use Vundle.

* [Vundle] (https://github.com/gmarik/Vundle.vim) integrates nicely with
Github.
* [Pathogen] (https://github.com/tpope/vim-pathogen) a very popular plugin
manager.
* [Vim-addon-manager] (https://github.com/MarcWeber/vim-addon-manager) VAM for
short.
* [Neobundle] (https://github.com/Shougo/neobundle.vim) an extension to Vundle.

Wait, did I say that you should *Use a plugin manager*?

Must have plugins
-----------------

Here is a short list of plugins that I use and love. Some are very basic,
others are extremely configurable and complex. Depending on your workflow and
the types of projects you typically work on you will find other projects out
there that are perfect for you.

* [EasyMotion] (https://github.com/Lokaltog/vim-easymotion) Vim motions on
  speed!
* [CtrlP] (https://github.com/kien/ctrlp.vim) fuzzy file, buffer, mru, tag, etc
  finder.
* [UltiSnips] (https://github.com/SirVer/ultisnips) code snippet insertion.
* [Airline] (https://github.com/bling/vim-airline) lean & mean status/tabline
  for Vim that's light as air.
* [Unimpaired] (https://github.com/tpope/vim-unimpaired) pairs of handy bracket
  mappings.
* [Supertab] (https://github.com/ervandew/supertab) perform all your Vim insert
  mode completions with tab.

Vim and Git plugins
-------------------

These plugins make using Git from within Vim a breeze.

* [Fugitive] (https://github.com/tpope/vim-fugitive) a Git wrapper so awesome,
  it should be illegal.
* [GitV] (https://github.com/gregsexton/gitv) gitk for Vim.

Programming with Vim
====================

Vim is a programmer's editor, it has great features to make programming easier.
Here are a few of the tools I find useful when I am coding.

* `={motion}` automatically indent the section of code included by `{motion}`.
* `>{motion}` shift lines included by `{motion}` one shiftwidth right.
* `<{motion}` shift lines included by `{motion}` one shiftwidth left.
* `ctrl-a` increment number under or after the cursor.
* `ctrl-x` decrement number under or after the cursor.
* `%` jump to the match of 'item' under the cursor, or nearest 'item' after
cursor, 'item' may be one of:
 * ([{}]) opening or closing parenthesis, curly brackets, square brackets.
 * /\* \*/ start or end of C style block comment markers.
 * #if, #ifdef, #else, #elif, #endif various C preprocessor conditionals.

* **Pro-tip**: `xp` quickly transposes two characters.

If your project has a makefile you can run 'make' from the Vim command line
(`:make`), the resulting warnings/errors can be viewed in the 'quickfix-window'
(`:help quickfix-window`) by running `:copen`. Close the quickfix window with
`:cclose`. Jump through the errors in with `:cnext`/`cprevious`.

Maneuvering source code
-----------------------

Finding function declarations, header files, variable definitions, etc. in a
large source tree can be arduous at best; Vim can be used in conjunction with
programs like [Exuberant Ctags] (http://ctags.sourceforge.net/) and [Cscope]
(http://cscope.sourceforge.net/) to make these problems all but go away. Vim
has built in functionality to parse each of these program's databases to
quickly and efficiently navigate the functions, files, variable, classes,
structures, etc. that compose your source tree.

Vim treats the identifiers in these databases as "tags" (`:help tags`). You can
use the `ctrl-]` shortcut to jump to the tag under or nearest the cursor on the
right. When Vim uses tags, it keeps a 'tag stack' which allows you to jump back
to previous locations in the tag stack. If you jump to a tag using `ctrl-]`,
you can jump back to your previous position using the `ctrl-t` shortcut.

TODO
====

* Spell check (`:set spell`, `]s`, `z=`, ...)
* Diff mode.
* Repeat last action with `.`.
* Talk about `[count]`s.
* Talk about `[ranges]`s.
* Add more to the Programming section.
* Summarize tabs.
* Introduce macros.
* netrw's `:Explore`.
* External commands with `!`.
* Jump to file under cursor with `gf`.
* Switch to last buffer using `ctrl-^`.
* "Coming home to Vim".
* **Pro-tip**: mention `q:` and `q/`.
* **Pro-tip**: repeat last substitute *with* last flags using `[range]&&`.
* **Pro-tip**: limit search/search-and-replace to visual selection with `\/%V`.
