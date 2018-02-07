---
title: "Some plotting"
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



### Computer vision

The broad field of *computer vision* (CV) is concerned with extracting
useful information from video recordings. There is a lot of progress in
the field, as summarised in
[@moeslund_survey_2001; @moeslund_survey_2006; @rautaray_vision_2015],
and we will here only look at a few possible methods.

Some basic motion features that are commonly used in music research are
derived directly from the motion image. Since the motion image only
shows pixels that have changed between the two last frames in a video
sequence, the sum of the values of all these individual pixels will give
an estimate of the *quantity of motion* (QoM). Calculating the QoM for
each frame will give a numeric series that can be plotted and used as an
indicator of the activity, such as illustrated in the graph of a dance
sequence in Figure \[fig:36-bevegelsesmengde3\]. Here it is possible to
see where the dancer moved or stood still.

![A plot of the quantity of motion for a 5-minute long dance sequence.
The grey line is a plot of the tracked data, and the black line is a
filtered version of the same data
set.[]{data-label="fig:36-bevegelsesmengde3"}](figures/Jensenius_Fig_1_6){width="100.00000%"}

The *centroid of motion* (CoM) and *area of motion* (AoM) are other
basic features that can easily be extracted from a motion image, and the
differences between them are illustrated in Figure \[fig:37-com\]. The
CoM and AoM features can be used to illustrate *where* in an image the
motion occurs as well the spatial displacement of motion over time.

![Illustrations of the area and centroid of body and
motion.[]{data-label="fig:37-com"}](figures/Jensenius_Fig_1_7){width="100.00000%"}

The field of computer vision has diverged into a number of different
directions over the years. Most notably, there are now numerous methods
available for tracking bodies and body parts in space, many of which are
also being used in music interaction and analysis through tools such as
EyesWeb [@camurri_analysis_2004], GEM for PureData [@zmolnig_gem_2004]
and Jitter for Max [@levin_computer_2006]. In addition to using regular
video cameras for such analyses, there are several different types of
specialised cameras that are made particularly for computer vision
methods, including:

-   infrared cameras capturing only light in the infrared (non-visible)
    range. Such cameras can be very useful in musical applications,
    since they work well also in dark spaces (such as a concert hall) or
    in locations with changing lights (for example club or stage
    lights).

-   time-of-flight cameras emitting a modulated acoustic signal and
    receive the reflected signal from which it is possible to measure
    the time it took for the signal to return to the camera.

-   stereo-cameras employing the same strategy as human vision, using
    two cameras next to each other (like our eyes), and then using the
    differences between the two images to estimate motion and rotation.

There are also examples of the combination of these three capturing
methods, as well as the use of multiple cameras around the capture
space. By combining multiple cameras distributed in space it is possible
to create true three-dimensional recordings. This can now be done
without markers on the body, but still the
state-of-the-art when it comes to camera-based motion tracking are the
marker-based systems using infrared cameras. 

