=====================================================
HOW TO REMOVE IMAGE METADATA WITH EXIFTOOL
=====================================================

WHAT THIS IS
------------
ExifTool is a free command-line program that removes hidden metadata
(EXIF, GPS location, camera info, editing history, AI provenance tags)
from image files.

Quick version:

    exiftool -all= image.png


-----------------------------------------------------
STEP 1: INSTALL EXIFTOOL (ONE TIME ONLY)
-----------------------------------------------------

WINDOWS (manual)
  1. Go to https://exiftool.org and download the "Windows Executable" zip.
  2. Extract it. Inside is a file named  exiftool(-k).exe
  3. Rename it to  exiftool.exe
  4. Put it in the same folder as your image
     (or in C:\Windows so it works from any folder).

WINDOWS (winget)
    winget install OliverBetz.ExifTool

MAC
    brew install exiftool

LINUX (Ubuntu / Debian)
    sudo apt install libimage-exiftool-perl


-----------------------------------------------------
STEP 2: OPEN A TERMINAL IN YOUR IMAGE FOLDER
-----------------------------------------------------

WINDOWS
  Open the folder that has your image, click the address bar,
  type  cmd  and press Enter.

MAC / LINUX
  Open Terminal and go to the folder, for example:
    cd ~/Downloads


-----------------------------------------------------
STEP 3: RUN THE COMMAND
-----------------------------------------------------

    exiftool -all= musafir_banner_fixed.png

Replace the file name with your own.
If the name has spaces, use quotes:

    exiftool -all= "my image.png"


-----------------------------------------------------
STEP 4: CHECK THE RESULT
-----------------------------------------------------

    exiftool musafir_banner_fixed.png

Only basic file info (name, size, dimensions, type) should remain.

By default ExifTool keeps your original file as:
    musafir_banner_fixed.png_original
Delete it before sharing the folder.


-----------------------------------------------------
USEFUL COMMAND VARIATIONS
-----------------------------------------------------

Clean one image:
    exiftool -all= image.png

Clean and do NOT keep a backup:
    exiftool -all= -overwrite_original image.png

Clean all PNG files in the current folder:
    exiftool -all= -overwrite_original *.png

Clean a folder and all its subfolders:
    exiftool -all= -r ./images

View all metadata (changes nothing):
    exiftool image.png


-----------------------------------------------------
OTHER WAYS TO CLEAR METADATA
-----------------------------------------------------

WINDOWS (built in, no install)
  Right-click image > Properties > Details tab >
  "Remove Properties and Personal Information" >
  "Create a copy with all possible properties removed".

MAC
  Preview > Tools > Show Inspector can remove GPS data only.
  Use ExifTool for a full wipe.

PYTHON (Pillow)
    from PIL import Image
    im = Image.open("image.png")
    clean = Image.new(im.mode, im.size)
    clean.putdata(list(im.getdata()))
    clean.save("clean.png")

SCREENSHOT
  A screenshot of the image creates a new file without the original
  metadata (image quality may drop).

PHONE
  In the share sheet on iPhone/Android, turn off "Location" before
  sending.


-----------------------------------------------------
TROUBLESHOOTING AND NOTES
-----------------------------------------------------

* Error: "'exiftool' is not recognized" (Windows)
  The exe is not in the current folder or in your PATH.
  Move exiftool.exe into the image's folder and try again.

* AI-generated images (e.g. from ChatGPT) often carry C2PA / Content
  Credentials in addition to EXIF. "exiftool -all=" removes most of it.
  Run "exiftool image.png" afterwards to confirm.

* Many social media sites strip metadata on upload, but do not rely
  on it. Clean the file yourself first.

* Always keep a copy of the original if you may need its metadata later.

=====================================================