## Step 1: Collect and prepare all photos per month

1. Open up the Photos Library app on a MacBook and export the photos to the folder `My Drive/Werkplaats/Photos To Archive/<yyyy>-<mm>`. In the Photo Library app go to `File > Export > Export .. Items`. Adjust the settings to export with the highest quality. 
2. Collect any photos that are not in Photos Library from:
    - Telegram
    - Whatsapp
    - Desktop
    - etc
3. Using the Name Mangler app on a MacOS device, apply a find and replace transformation to the file names:
    1. Find regex: `(.*)\ (\d+)\-(\d+)\-(\d+)\,\ (\d+)\ (\d+)\ (.*)`
    2. Replace with: `$4-$3-$2-$5.$6.$7`
4. Correct any wrongly named files manually.
## Step 2: Create Photo A Day sheet

1. Make a selection of photos per month in the corresponding folder -  make sure to copy the photos, not move (`My Drive/Werkplaats/Photo A Day/photos/<yyyy>-<mm>`)
2. Place the photos in the Sketch template and adjust accordingly (`My Drive/Werkplaats/Photo A Day/workspace_month.sketch`)
3. Export the monthly sheet to PDF and store in `My Drive/Werkplaats/Photo A Day/big`
4. Compress the monthly sheet using PDF Squeezer with default settings (Medium Compression) and store in `My Drive/Werkplaats/Photo A Day/small`
5. Add the compressed sheet to the full document `My Drive/Werkplaats/Photo A Day/small/_2020-2023.pdf`
## Step 3: Store photos in archive

1. Move the photos from the temporary folder (`My Drive/Werkplaats/Photos To Archive/<yyyy>-<mm>`) to their permanent archived spot `My Drive/Fotoboek/[<yyyy>]`.
2. Sort photos in archive accordingly.
## Step 4: clean-up

Clean up the Photo Library and remove any other duplicates. 

[[*personal-development]]