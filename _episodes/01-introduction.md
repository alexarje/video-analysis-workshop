---
title: "Introduction"
teaching: 10
exercises: 0
questions:
- "What is a digital video file?"
objectives:
- "Understand the basics of digital video, including framerate, number of planes and bitrate."
keypoints:
- "A video file is just a series of images."
---



## Why video analysis?

For researchers interested in studying humans and human motion, a regular video recording is often the easiest, fastest and cheapest solution to start with. Nowadays, everyone has access to fairly high quality video cameras even in their mobile phones, and the cost of professional-quality video cameras is also within the reach for many researchers.

One of the positive things about video analysis is that it opens for a broad range of analysis techniques, from purely qualitative methods to purely
quantitative. For example, having a video recording that can be
played back multiple times, and at various speeds, is very useful for
visual inspection. And, as we shall see later, 
even a regular video recording can be used to extract meaningful
quantitative motion data. Furthermore, it is also common to use video
recordings as a reference when recording motion with sensor-based motion
tracking technologies. In such cases, the video recording can be used to
help the qualitative interpretation of numerical results.


## Recording video for analysis

One thing to bear in mind is that a video recording meant for analytical
purposes is quite different from a video recording shot for documentary
or artistic purposes. The latter type of video is usually based on the
idea of creating an aesthetically pleasing result, which often includes
continuous variation in the shots through changes in the lighting,
background, zooming, panning, etc. A video recording for analysis, on
the other hand, is quite the opposite: it is best to record it in a
controlled studio or lab setting with as few camera changes as possible.
This is to ensure that it is the *content* of the recording, that is,
the human motion, which is in focus, not the motion of the camera or the
environment.

Even though a controlled environment may be the best choice from a
purely scientific point of view, it is possible to obtain useful
recordings for analytical purposes also out in the field. This, however,
requires some planning and attention to detail. Here are a few things to
consider:

-   Foreground/background: place the subject in front of a background
    that is as plain as possible, so it is possible to easily discern
    between the important and non-important elements in the image. For
    computer vision recordings it is particularly important to avoid
    backgrounds with moving objects, since these may influence the
    analysis.

-   Lighting: avoid changing lights, as they will influence the final
    video. In dark locations, or if the lights are changing rapidly
    (such as in a disco or club concert), it may be worth recording with
    an infrared camera. Some consumer cameras come with a “night mode”
    that serves the same purpose. Even though the visual result of such
    recordings may be unsatisfactory, they can still work well for
    computer-based motion analysis.

-   Camera placement: place the camera on a tripod, and avoid moving the
    camera while recording. Both panning and zooming makes it more
    difficult to analyse the content of the recordings later. If both
    overview images and close-ups are needed, it is better to use two
    (or more) cameras to capture different parts of the scene in
    question.

-   Image quality: it is always best to record at the highest possible
    spatial (number of pixels), temporal (frames per second) and
    compression (format and ratio) settings the camera allows for.
    However, the most important is to find a balance between image
    quality, file size and processing time.

As mentioned earlier, a video recording can be used as the starting
point for both qualitative and quantitative analysis. We will here look
at a couple of different possibilities, moving from more qualitative
visualisation methods to advanced motion capture techniques.

## What is a video file?

We will get started with the first hands-on activities. First of all, we want to understand more about what a video file contains. 

Find a video file on your computer, or select the file dance.avi from the example folder. Open the file and try to find out: 

- what is the frame rate? 
- what is the bitrate?
- what type of compression is used? 

On most systems (Linux, Mac, Windows) you should be able to do this by selecting something like "properties" from the file inspector.

The important thing to understand here, is that a digital video file can be seen as a series of still images. This opens for doing various types of mathematical operations on the file. 

![Video file information](video_info.png) 

