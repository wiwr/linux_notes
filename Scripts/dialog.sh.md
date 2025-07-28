`dialog --msgbox "Hello World" 6 30`

```
#!/bin/bash

option_1() {
        clear
        echo "You selected Option 1"
        read -n1 -r -p "Press any key to continue..."
}
option_2() {
        clear
        echo "You selected Option 2"
        read -n1 -r -p "Press any key to continue..."
}
option_3() {
        clear
        echo "You selected Option 3"
        read -n1 -r -p "Press any key to continue..."
}

dialog --inputbox "What is your name: " 8 40 2>name.txt

if [ $? -eq 0 ] ; then
        name=$(<name.txt)
        dialog --msgbox "Hello $name" 6 30
fi

rm -f name.txt

while true; do
        dialog --menu "Choose an item: " 10 30 2 \
                1 "Option 1" \
                2 "Option 2" \
                3 "Option 3" 2>menu.txt

        if [ $? -ne 0 ]; then
                break
        fi

        choice=$(<menu.txt)
        case $choice in
                1) option_1 ;;
                2) option_2 ;;
                3) option_3 ;;
        esac
done
rm -f menu.txt
clear
echo "Ended"

```