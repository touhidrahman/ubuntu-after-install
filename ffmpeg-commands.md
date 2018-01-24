## Trim media 

`ffmpeg -i file.mkv -ss 20 -to 40 -c copy file-2.mkv`
`ffmpeg -i file.mkv -ss 00:00:20 -to 00:00:40 -c copy file-2.mkv`

This should create a copy (file-2.mkv) of file.mkv from the 20 second mark to the 40 second mark.


