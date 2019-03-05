---
title: "Preprocessing video"
teaching: 5
exercises: 10
questions:
- "How is it possible to improve the video before analysing?"
objectives:
- "Learn to trim, crop and downsample a video."
- "Learn some of the specialized functions in MGT."
keypoints:
- "A video is *trimmed* in time, *cropped* in space, and *downsampled* in pixels."
- "There are a number of things to set and modify in the code, most of which are documented in the help files."
---


## Working with structures

For the more advanced examples we will change from working directly on video files to handling a matlab *structure* containing a pointer to the file. 

    mg = mgread('dance.avi');

From here you can refer to *mg* instead of the name of the video file. 


## Trimming the files

If we only want to analyse a part of this recording, we may choose to extract a segment of 20 seconds from 10 seconds to 30 seconds of the original video. Here MGT will handle the trimming of all related files and data: 

    mgseg = mgreadsegment(mg,10,30);

Here *mgseg* is a new (and complete) structure that can be used for further processing. 


## Cropping video

To further save some computational time, and focus more particularly on a particular part of the video, we may also look only at the *region of interest* of the video. The *mgvideocrop* function will crop specified region on each frame. Start by using: 

    mgcrop = mgvideocrop(mg);

The user can "draw" the region on the video frame followed by right-clicking to start the export. 


## Rotating

Sometimes you may want to rotate the video before doing an analysis. For example, analysing standing people may be easier to do with a video recorded in portrait mode. Then it may be useful to rotate the video in Matlab. This can be done like this: 

    mgrot = mgvideorotate(mg,90);


## Downsampling

Analysing large, full-size video files can be very time-consuming. Therefore it may sometimes be useful to downsample the video file before moving on. This can be done like this: 

    mgsam = mgvideosample(mg,[2,2],'samplevideo.avi');

This reduces the framesize of the video with a factor of 2 in both rows and columns. It also writes the downsampled video to a new file 'samplevideo.avi'.


## Run your analysis

After doing all of the above, you may want to run your analysis on the output, say: 

    mgan = mgmotion(mgsam);


## Colour analysis

The plan is to implement a colour option in all functions. For now, however, you can enable colour processing by setting this flag: 

    mg.video.mode.color = 'On';

Then you can run 

    mgmotion(mg,'Diff','Regular',0.1);

to create a motion video and motiongrams in colour. 


## Colour inversion

Sometimes you may want to invert colours in the output files, particularly if you want to print something on paper. Then you can set this flag: 

    mg.video.mode.convert = 'On'

and possibly also revert back to using greyscales: 

    mg.video.mode.color = 'Off';

before running the analysis: 

    mgmotion(mg,'Diff','Regular',0.1);

and you will get black on white, instead of white on black. 


{% include links.md %}
