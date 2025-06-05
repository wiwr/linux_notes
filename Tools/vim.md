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
