bellow script let to make MP3 file smaller 
```bash
#!/bin/bash

FILES="*.mp3"

for F in $FILES
do
    echo "$F"
    newname=`basename "$F" "mp3"`
    newname=${newname}"-smaller.mp3"
    ffmpeg -i "$F" -acodec libmp3lame -ac 2 -ab 160k -ar 44100 "$newname"
done
```