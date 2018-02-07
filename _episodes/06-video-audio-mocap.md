---
title: "Combining video, audio and mocap"
teaching: 10
exercises: 20
questions:
- "What are different video visualization techniques?"
- "How can you create video visualizations in Matlab using MGT"
objectives:
- "Understand what "
keypoints:
- "A video file is just a series of images."
---




## Example set #2: Analysis of piano performance (video, audio, mocap)

This example is showing how it is possible to use MGT for the combined analysis of visualization of video data together with video and audio. As opposed to the previous example, this requires the use of the MGT data structure for handling synchronization of the data streams. 



This example shows how you can read video, audio, mocap files into Matlab and how you can preprocess the data. The data is stored as musical gestures data structure after importing. The Musical Gestures Toolbox includes mgdemo1 that contains video, audio, mocap recordings. It is used for the example of this manual. Firstly, read video data into matlab workspace, mgread can read video, audio, mocap data and create a data structure.

    mg = mgread(’pianist.mp4’,’pianist.wav’,’pianist.tsv’)

A musical gestures data structure is imported into Matlab workspace. It shows three substructs, video, audio, mocap, respectively. The video recordings are the pianst who is playing the piano. The length of the video is around 97.5seconds. Let’s futher look at the video substruct: Next, we can extract the segment from the structure. For instance:

    mgseg = mgvideoreader(mg,’Extract’,10,20);

This operation will extract the lenght of 20 seconds from 10 seconds to 30 seconds of the video. In order to keep the same segment with video, it needs to do the same extraction on the audio and mocap data. This can be done by function mgmap.

    mgseg = mgmap(mgseg,’Both’);

Alternatively, all operations above can be simply done by one step. The function mgread- segment does it.

    mgseg = mgreadsegment(mg,10,30);

Sometimes, you may think the video recordings are too large. For instance, the video
frame is with 480 by 680 dimension. Usually, this is large enough to satisfy your needs.
Down sampling the video may be helpful. The function mgvideosample could help you
sample the video conveniently.

    mgsam = mgvideosample(mgseg,[2,2],’samplevideo.avi’);

Now, each video frame has been reduced to half. And, the sampled video ’samplevideo.avi’
was written back to disk as well. The sampling factor [2,2] means row and column fac-
tors respectively. If we want to look only the region of interest of the video locally, here
mgvideocrop will crop specified region on each frame. User can define any shape of region
of insterest and draw the region on the video frame. The cropped video can be used to
compute the motion as well. In a sense, the result should have good estimation off local
object, for instance, hands, head, etc. Next, the motion grams, quantity of motion and
centroid of motion can be computed. If the position of the region is not given, user can
draw a region, and right-click the mouse and select crop image to create the region.

    mgcrop = mgvideocrop(mg);
    mgcrop = mgvideocrop(mg,pos);

    mgsammo = mgmotion(mgsam,’Diff ’);
    mgsegmo = mgmotion(mgseg,’Diff ’);

The method ’Diff’ uses the absolute difference between two successive frames. It provides
also optical flow method to compute the motion. Furthermore, the function mgmotion
could do some filtering operations as well.

    mgsegop = mgmotion(mgseg,’OpticalFlow’);

It is interesting to note the player does almost the same action repeatedly from the
quantity of motion. From the view of the centroid of motion, most of the blue points
cluster in the right side. This is because the player plays the piano using his left hand
more often. So the center of movement appears in the right side.
Next,the periodicity of movement might be investigated from the quantity of motion. Let’s
have a look at it.

    [per,ac,eac,lag] = mgautocor(mgsegmo);

The period is 0.198 seconds. The first maximum at nonzero lag is 0.198 seconds, this
is the same as the privious value. Sometimes, it is necessary to show the motion grams
and mocap gram. The function mgvideoplot plots the horizontal and vertical motion gram
combined with mocap gram over time.

    mgvideoplot(mgsegmo);


To look at motions more clearly, the vertical motion gram is transposed and the motion
grams are plotted by imagesc function after some noise removal. It can be showed that
31Figure 6: motion gram and mocap gram over time
Figure 7: horizontal and vertical motion gram,the vertical motion gram is transposed
the player repeats the similar action from the horizontal motion gram, which corresponds
to the quantity of motion. From the vertical motion gram, it is very clear to note there
32is only hand playing the piano from 19 seconds to 23 seconds. This explians why most
centroid of motion locate in the right side.

Next,let’s continue to investigate the audio recording. mgwaveplot plots the waveform of
audio, root mean square,and their spectrum.

    mgwaveplot(mgsegmo);

Figure 8: waveform,rms and their spectrum
We may hope that the spectrum of the quantity of motion also gives us some useful
information. Here we can compare it with the spectrum of the rms.
Look at the spectrum of qom, the foundamental frequency is given by 5Hz, which is 0.2
seconds. This value is the same as period estimated by mgautocor function.
If we want to look at some features of motion image, function mgstatistics can generate
first order and second order features.
features1 = mgstatistics(mgsegmo,’Video’,’FirstOrder’);
features2 = mgstatistics(mgsegmo,’Video’,’SecondOrder’);
33Figure 9: spectrum of qom and rms
Figure 10: the first order feature space
34Figure 11: the second order feature space
