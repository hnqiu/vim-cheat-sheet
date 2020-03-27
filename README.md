# My Vim Cheat Sheet

## Tips
- Many of the commands can use a `number` prefix as the times of repeating the command.
- Some commands (e.g., `o`, `i`, `p`) have upper & lower cases. The upper ones operate (open, insert, paste) before or on top of the cursor; the lower ones operate after the cursor.
- Command `d` and `c` are very similar. The only difference is `c` will enter the insert mode after characters are deleted.
- Map key bindings in [Vim](http://vimdoc.sourceforge.net/htmldoc/map.html) & [VSCode Vim extention](https://github.com/VSCodeVim/Vim#key-remapping).

## Global
```sh
:help [keyword] # show help
:o [file] # open file

:set number # show line number
:set nonumber # hide line number

u # undo
<C-r> # redo

<C-c> / <C-[> / <Esc> # exit to the normal mode
```

## Exiting
```sh
:w # write file
:w [file] # write to file
:wq [or] :x # write & quit
:q # quit
:q! # quit without saving

:w !sudo tee % # write out the current file with root permission
# w - save the buffer as
# tee - redirect output to files and/or to standard outputs
# % - the current file
```

## Moving Cursor
```sh
h # move cursor left
j # move down
k # move up
l # move right
<sapce> # move cursor rightwards through lines
2k # move up 2 lines
- # move cursor to the beginning of the previous line

H # move to the top of screen
L # move to the bottom of screen
3L # move to the last third line of screen
<C-b> # page up
<C-f> # page down
<C-u> # move cursor up half page
<C-d> # move cursor down half page

z <Enter> # move current line to the top of screen
zz / z. # move current line to the centre of screen
z- # move current line to the bottom of screen

G # move to the end of file
gg # move to the top of file
3G/3gg # go to line 3

( # jump backward to the start of this block or to the end of the previous if the cursor is already at the start
) # jump forward to the end of this block or to the start of the next if the cursor is already at the end
{ # jump to the previous paragraph/block
} # jump to the next paragraph/block

0 # jump to the beginning of a line
^ # jump to the first non-blank character of a line
$ # jump to the end of a line

# uppercase of the following commands means the word contains punctuation
w/W # jump forward to the start of next word 
e/E # jump forward to the end of a word
b/B # jump backwards to the start of a word
2w # jump forward 2 times to the start

% # move to the matching character, eg, () {}

/chars # search the corresponding characters
n # find next
N # find previous
fx # jump to the next character `x` in the current line
Fx # jump to the previous character `x` in the current line
; # repeat the above movement
, # repeat the above movement backwards
```

## Copy & Paste
```sh
yl/y<space>/vy # yank current character
yy # copy a line
ye # yank from current to the end of the word (including the end)
yw # yank from current to the start of the next (without the next word)
dd # cut a line
di( / di{ / di[ # delete in parenthesis: delete contents within () / {} / []
D/d$ # cut to the end of a line
p # paste after cursor
P # uppercase: paste before cursor
x # cut a character
2dd # cut 2 lines
```

## Editing
```sh
~ # switch case
r/R # replace a character(s)
s # substitute: delete a character and switch to insert mode
cw # change (delete) to the end of the word and switch to insert mode
ciw # delete the current word and switch to insert mode
ci( / ci{ / ci[ # change in parenthesis: substitude contents within () / {} / []
C/C$ # cut to the end of a line and switch to insert mode
S/cc # clear the current line and switch to insert mode
J # join line below to current with one space in between
```

## Insert Mode
```sh
i # insert
a # append: insert after cursor
I # insert at the beginning of a line
A # insert at the end of a line

o # open a new line below the current line
O # open a new line above the current line
```

## Visual Mode
```sh
v # visual
V # visualize a line
`Ctrl`+v # visualize block
aw # (mark) a word
o/O # switch between the ends of marked area

y # yank marked text
d # cut marked text
c # delete marked text and switch to insert mode
U/u # switch to upper/lower case
```

## VSCodeVim
```sh
gd # go to definition

gc # toggle line comment
gcc gc<space> gcl # toggle line comment for the current line
gc2j # toggle line comment for the current and the next two lines

gC # toggle block comment
(gC) # toggle comment for the current block
gCi) # comment out what's inside parenthesis

gb # multi-cursor mode, add cursor on the next same word
```

## Special Characters
```sh
$ # move cursor to the end of this line
% # move to the matching character, eg, () {}
^ # move cursor to the first non-blank character of this line
0 # move cursor to the beginning of this line
- # move cursor to the beginning of the previous line
/ # find pattern
~ # switch case
```

## Example
- Insert the same characters (e.g., comment-out character) across multiple lines:
  - use visualized block
    ```sh
    `Ctrl`+v # and select block
    I/s/r # to insert/replace texts
    `Esc` # (optional) to evoke changes
    ```
  - use `.` (`dot`) to repeat command
    ```sh
    I/s/r # to insert/replace texts
    j # move cursor
    . # repeat
    ```
- Select all: `ggVG`
