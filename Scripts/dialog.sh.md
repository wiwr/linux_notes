`dialog --msgbox "Hello World" 6 30`

```
dialog --inputbox "What is your name: " 8 40 2>name.txt

if [ $? -e1 0 ] ; then
        name =$(<name.txt)
        dialog --msgbox "Hello $name" 6 30
fi      

rm -f name.txt
```