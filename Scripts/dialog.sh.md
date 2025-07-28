`dialog --msgbox "Hello World" 6 30`

```
dialog --inputbox "What is your name: " 8 40 2>name.txt

if [ $? -eq 0 ] ; then
        name=$(<name.txt)
        dialog --msgbox "Hello $name" 6 30
fi      

rm -f name.txt
dialog --menu "Choose an item: " 10 30 2 \
        1 "Option 1" \
        2 "Option 2" \
        3 "Option 3"
clear
```