# vimtutor
vimtutor
required vim-enhanced
# macros
## With back to beginning of line: 
```
qa0<ESC>q
```
0 back to beginning of line 
## All on entire file: 
Till end of file 
:normal @a 
:2,$:normal @a 
## Example: 
q – to start a macro 
h – register under h 
Sequens of actions 
q – to stop a macro 
@h – to run a macro 
9@h- to run a macro 9 times 
# commands
:!command - to execute any shell command

# Change to
~    : Changes the case of current character  
guu  : Change current line from upper to lower. 
gUU  : Change current LINE from lower to upper. 
guw  : Change to end of current WORD from upper to lower. 
guaw : Change all of current WORD to lower.  
gUw  : Change to end of current WORD from lower to upper.
gUaw : Change all of current WORD to upper. 
g~~  : Invert case to entire line  
g~w  : Invert case to current WORD  
guG  : Change to lowercase until the end of document.  
gU)  : Change until end of sentence to upper case  
gu}  : Change to end of paragraph to lower case  
gU5j : Change 5 lines below to upper case  
gu3k : Change 3 lines above to lower case
# Modes
## binary
Start vim with –b flag 

:%!xxd 

:%!xxd -r 

Use xxd as a filter within an editor such as vim(1) to hexdump a region marked between `a' and `z'. 

       :'a,'z!xxd 

       Use xxd as a filter within an editor such as vim(1) to recover a binary hexdump marked between `a' and `z'. 

       :'a,'z!xxd -r 

       Use  xxd as a filter within an editor such as vim(1) to recover one line of a hexdump.  Move the cursor over 

       the line and type: 

       !!xxd -r

## g command
```
:g/patter/cmd
```
```
:g/original/p
:g/original
```
```
:g/original/d
```
```
:g/original/norm A coś tam
```


# v command
is inversion
# p command
print

## gn
```
/Music
gn
c
cgn
.

gN
cgN
e! - to revert changes
```

## i & Crtl+0

## i & Ctrl+N
Ctrl+N Ctrl+P Ctrl+Y

## i & indent
To add Ctrl+T
To remove Ctrl+D

## i & Ctrl+R

## :!
```
:!wc -w file_name
```
or 
```<CTRL-R>%``` - paste current file name to command line
```
.!cowsay "
```
and ```
<CTRL-R><CTRL-L>``` - paste current line to command line
```
"
```

## Tab completion

## Repeat command
```
@:
```

## Normal command
to add word on end of each line
```
:1,10 norm A word
```
```<CTRL-V>``` select range

```
norm A test
```

```
:%norm 0wi*^[ea*
```