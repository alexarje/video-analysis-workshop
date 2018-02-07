---
title: "Visualization"
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



## Video visualisation

Videos can be watched as they are, but they can also be used to develop
new visualisations to be used for analysis. The aim of creating such
alternate displays from video recordings is to uncover features,
structures and similarities within the material itself, and in relation
to, for example, score material. Three useful visualisation techniques
here are *motion images*, *motion history images* and *motiongrams*.




## Simple motion analysis

The easiest way to get started with analysing video with MGT is by just running the function mgmotion. You can try this with one of the example files like this: 

    mgmotion('dance.avi');

This will generate four files in the same location as your source file: 

- dance_motion.avi: the motion video that is used as the source for the rest of the analysis
- dance_mgx.tiff: a horizontal motiongram
- dance_mgy.tiff: a vertical motiongram
- dance_data.csv: a data file with some quantitative features
- dance_com_qom.eps: an image file with plots of centroid and quantity of motion

We will examine each of these in a little more detail. 




## Motion images

One of the most common techniques when working with motion analysis from
video files is to create a *motion image* by calculating the absolute
pixel difference between subsequent frames in the video file (Figure
\[fig:motion-image\]). The end result is an image where only the pixels
that have changed between the frames are displayed. This can be
interesting in itself, but motion images are also the starting point for
many other video visualisation and analysis techniques.

![A *motion image* is created by subtracting subsequent frames in a
video file (Frame(2) -
Frame(1)).](figures/motion-images.jpg)


## Motion history images

Motion images only display the motion happening between two frames in a
video file, but often it is desirable to visualise motion over a period
of time, say, a few seconds. This can be done through *motion history
images* that display the temporal development of a motion sequence.
There are numerous ways of creating such displays [@ahad_motion_2012],
but many of the most common techniques are based on adding several
motion image frames together. The usefulness of motion history images
depend on carefully selecting a time window that fits the content of the
motion, as can be seen in the examples of percussion strokes in
Figure \[fig:drumming-mhi\].

![Individual motion history images of 14 separate percussion strokes
allow for studying stroke heights and patterns. The images have been
made by adding a motion history image on top of a picture of the scene,
thus showing both motion features and the contextual
information.[]{data-label="fig:drumming-mhi"}](figures/Jensenius_Fig_1_4){width="100.00000%"}

Motion history images have been used in various types of music analysis,
such as in the study of music and dance [@camurri_recognizing_2003], and
are also often to be seen in visual arts and creative practice.

## Motiongrams

While a motion history image may reveal information about the spatial
aspects of a motion sequence over a fairly short period of time, it is
possible to use a *motiongram* to display longer sequences
[@jensenius_video_2013]. Figure \[fig:3dancers-mg\] shows a motiongram
created from a dance improvisation recording, and this display is
created by plotting the normalised mean values of the rows of a series
of motion images. The motiongram makes it possible to see both the
location and quantity of motion of a video sequence over time, and is
thus an efficient way of visualising longer motion sequences.

![A motion average image and a motiongram of a 3-minute free-dance
sequence to music make it possible to study both spatial and temporal
features of a performance in connection to the spectrograom of the
audio.[]{data-label="fig:3dancers-mg"}](figures/Jensenius_Fig_1_5){width="100.00000%"}

A motiongram is only a reduced display of a series of motion images,
with no analysis being done. It might help to think of the motiongram as
a display of a collapsed series of pictures, or “stripes,” where each
“stripe” summarises the content of a whole motion image.

Dependent on the frame rate of the video file, motiongrams can be
created from recordings as short as a few seconds to several hours. For
short recordings it is possible to follow detailed parts of a body,
particularly if there are relevant colours in the image, while
motiongrams of longer recordings will mainly reveal larger sections of
motion. Motiongrams work well together with audio spectrograms, and
other types of temporal displays such as graphs of motion or sound
features.








### Filtering

If you think there is too much noise in the output images or video, you may choose to use some other filter settings. 

    mgmotion('dance.avi','Diff','Regular',0.2);




