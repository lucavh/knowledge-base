# Photo a Day project

## Step 1: collect and prepare all photos per month

1. Using an iOS device with the Dropbox app, import photos from your Photo Library to the folder `Dropbox/4 - Sentiment/Jaaroverzichten/1 - Photo A Day/photos/<yyyy>-<mm>`. By using this method the date will be included in the file name.
2. Collect any photos that are not in Photos Library from:
    - Telegram
    - Whatsapp
    - Desktop
    - etc
3. Using the Name Mangler app on a MacOS device, apply a find and replace transformation to the file names:
    1. Find regex: `(.*)\ (\d+)\-(\d+)\-(\d+)\,\ (\d+)\ (\d+)\ (.*)`
    2. Replace with: `$4-$3-$2-$5.$6.$7`
4. Correct any wrongly named files manually.

## Step 2: store photos in archive

1. Copy all photos from the month folder (`Dropbox/4 - Sentiment/Jaaroverzichten/1 - Photo A Day/photos/<yyyy>-<mm>`) to `Dropbox/3 - Foto's/[<yyyy>]`.
2. Sort photos in archive accordingly.

## Step 3: create Photo A Day sheet

1. Make a selection of photos per month in the corresponding folder (`Dropbox/4 - Sentiment/Jaaroverzichten/1 - Photo A Day/photos/<yyyy>-<mm>`)
2. Place the photos in the Sketch template and adjust accordingly (`Dropbox/4 - Sentiment/Jaaroverzichten/1 - Photo A Day/workspace.sketch`)
3. Export the monthly sheet to PDF and store in `Dropbox/4 - Sentiment/Jaaroverzichten/1 - Photo A Day/big`
4. Compress the monthly sheet using PDF Squeezer with default settings and store in `Dropbox/4 - Sentiment/Jaaroverzichten/1 - Photo A Day/small`
5. Add the compressed sheet to the full document `Dropbox/4 - Sentiment/Jaaroverzichten/1 - Photo A Day/small/_2020-2023.pdf`

## Step 4: clean-up

Clean up the Photo Library and remove any other duplicates. 

