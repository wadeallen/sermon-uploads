# Instructions

This repository contains the necessary scripts for preparing and uploading the sermons from First Baptist Muncie.

**Step One:** Move the MTS files from the SD Card to your computer. This can be done by simply copying the files over in a file manager. I use a bash script that creates a folder on my desktop and places the files in that folder. The files are located on the SD card in the following directory.

`/PRIVATE/AVCHD/BDMV/STREAM/`

**Step Two:** If there is more than one file, you will need to combine the files into one. You might double check to make sure that all the files are necessary. If you find files that are not necessary, you can delete them. If there is only one file, this step is not necessary.

You may need to change the file names in the script of they are different or change the name of the MTS files to match the script. You will need to be in the folder of the files to run this script.

`merge_MTS`

**Step Three:** When you have only one file (either a .MTS file or a m2ts file). You need to encode a .mp3 file. You will need to have the following information ready for the script: sermon title, preacher and description.

`audio filename.MTS` or `audio filename.m2ts`

When the script is finished, rename the .mp3 file to the current date (i.e. 2017-04-10). It must be in this format YYYY-MM-DD.

**Step Four:** You need to upload the .mp3 file to the church's amazon S3 bucket. I use a tool called s3cmd. You will need to get the credentials to set up the software. You could you any sort of Amazon S3 client for this task.

`upload filename.mp3`

**Step Five:** The next step is to encode the youtube video. You will run this script on the .MTS or .m2ts file. 

`youtube filename.MTS` or `youtube filename.m2ts`

**Step Six:** Upload the output (filename.mp4) to YouTube. You will need to get the sign in credentials for my church account.

**Step Seven:** Prepare the .md file on the website and move push it to GitHub. You can move the file from the worship folder to the posts folder and edit it before pushing to GitHub.

From the root of the website repository, the worship files reside in:

`_worship`

The file for a given Sunday will need to be moved to:

`_posts`

Then you will need to edit the file, adding meta-data for the sermon.

Here is an example with comments:

```
---
author: Wade Allen # This line should already be in file
title: Crucified # This line should already be in file
scripture: Matthew 27:11-54 # This line should already be in file
date: 2017-04-09 # This line should already be in file
layout: sermon # need to add this line
category: video # need to add this line
duration: '0:29:17' # need to add this line
length: 42176361 # need to add this line
video_url: E17Bso9znuY # need to add this line
---

As we begin Holy Week, we will walk through the story of Jesus' arrest and crucifixion. Jesus' control and determination to fulfill his mission are stunning. He could have called it off at any point. Yet, he willingly steps into pain, suffering, humiliation in order to rescue us.

```
You have to add both of these lines for the webpage to render properly:

```
layout: sermon
category: video
```

You will need some sort of software to find the duration and length. I use the following script:

`duration`

Finally, you need to grab the video id from the YouTube url and place it in the video field.

Once this file is complete, make sure it is in the `_posts` folder of the website repository.

The site usually takes about 1-2 minutes to refresh with the new content. I always check it out to make sure everything works.




