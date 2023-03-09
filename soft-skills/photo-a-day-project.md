# Photo a Day project

Per month of the year:

1. Using an iOS device with the Dropbox app, import photos from your Photo Library to the folder `...`. By using this method the date will be included in the file name.
2. Collect any photos that are not in Photos Library from:
    - Telegram
    - Whatsapp
    - Desktop
    - ...
2. Using the Name Mangler app on a MacOS device, apply a find and replace transformation to the file names:
    1. Find regex: `(.*)\ (\d+)\-(\d+)\-(\d+)\,\ (\d+)\ (\d+)\ (.*)`
    2. Replace with: `$4-$3-$2-$5.$6.$7`