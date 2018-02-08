---
title: "More visualization"
teaching: 10
exercises: 20
questions:
- "Some more visualization techniques?"
objectives:
- "Create motion average images."
- "Create motion history videos."
keypoints:
- "A motion average image is a kind of open-shutter technique."
- "A motion history video visualizes motion trajectories."
- "All functions can be run on any type of video input."
---



## Motion average image

While motiongrams are good for getting a general sense of the spatiotemporal distribution of a video file, a *motion average image* is good for getting a general sense of the space covered. This may be thought of as similar to an "open shutter" on a camera, since the function just averages (and normalizes) over all the frames. Try: 

    mgmotionaverage('dance_motion.avi');

If the motion is evenly distributed in the image, the motion average image may not contain much information. But if a person has been standing still in one spot, it will show up very clearly. 

It is also possible to run this function on the original video: 

    mgmotionaverage('dance.avi');

Such an *average image* may also be useful in combination with the motion average image. 

If you only want to look at a particular part, you may choose to identify the start and stop positions of the averaging (in seconds from the start of the file):

    mgmotionaverage('dance.avi',0,5);

So here we get the average of the first 5 seconds of the file. 



## Motion history video

One dynamic visualization technique is that of creating a *motion history video*, which gives you an idea of how the motion has been unfolding in time. This can be done with the following command: 

    mgmotionhistory('dance_motion.avi');

It can, in fact, also be run on the original video: 

    mgmotionhistory('dance.avi');

We have up until now primarily worked with video in greyscales. This is more cpu-friendly, since it only consumes 1/4 of the processing power as that of colour. Sometimes colour may be important, though, so it is possible to run the process on all the video planes like this: 

    mgmotionhistory('dance.avi',20,'color');

The number 20 here refers to the number of frames of the history. You can try some different settings here too. 



{% include links.md %}
