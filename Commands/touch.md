`comand -v touch` - to check if is present in system
`sudo apt install coreutils` - to install touch if missing
`touch file_name.txt` - if the file doesn't exist, it will be created. If the file does exist, its timestamp will be updated
`touch file_name.txt next_file.txt other_file.txt` - to create or updated multiple files
`touch -t 2025070272232 file_name.txt` - to updated file with specific timestamp