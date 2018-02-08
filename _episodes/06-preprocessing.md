---
title: "Preprocessing video"
teaching: 5
exercises: 10
questions:
- "How is it possible to improve the video before analysing?"
objectives:
- "Learn to trim, crop and downsample a video."
keypoints:
- "A video is *trimmed* in time, *cropped* in space, and *downsampled* in pixels."
---



## Trimming the files

If we only want to analyse a part of this recording, we may choose to extract a segment of 20 seconds from 10 seconds to 30 seconds of the original video. Here MGT will handle the trimming of all related files and data: 

    mgseg = mgreadsegment(mg,10,30);

Here *mgseg* is a new (and complete) structure that can be used for further processing. 



## Cropping video

To further save some computational time, and focus more particularly on a particular part of the video, we may also look only at the *region of interest* of the video. 

    mgcrop = mgvideocrop(mg);


The *mgvideocrop* function will crop specified region on each frame. User can define any shape of region
of insterest and draw the region on the video frame. The cropped video can be used to
compute the motion as well. In a sense, the result should have good estimation off local
object, for instance, hands, head, etc. Next, the motion grams, quantity of motion and
centroid of motion can be computed. If the position of the region is not given, user can
draw a region, and right-click the mouse and select crop image to create the region.

    mgcrop = mgvideocrop(mg,pos);

    mgsammo = mgmotion(mgsam,'Diff ');
    mgsegmo = mgmotion(mgseg,'Diff ');


## Rotating

Sometimes you may want to rotate the video before doing an analysis. For example, analysing standing people may be easier to do with a video recorded in portrait mode. Then it may be useful to rotate the video in Matlab. This can be done like this: 

    mgrot = mgvideorotate(file,angle);


## Downsampling

Analysing large, full-size video files can be very time-consuming. Therefore it may sometimes be useful to downsample the video file before moving on. This can be done like this: 

    mgsam = mgvideosample(mg,[2,2],'samplevideo.avi');

This reduces the framesize of the video with a factor of 2 in both rows and columns. It also writes the downsampled video to a new file 'samplevideo.avi'.





{% include links.md %}
