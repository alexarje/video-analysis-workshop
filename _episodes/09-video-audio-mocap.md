---
title: "Combining video, audio and mocap"
teaching: 5
exercises: 20
questions:
- "How is it possible to analyze video, audio and mocap together?"
objectives:
- "Learn to create and manipulate MGT structures"
keypoints:
- "An MGT struct can be used to organize and manipulate different types of data."
---




This example is showing how it is possible to use MGT for the combined analysis of visualization of video data together with video and audio. As opposed to the previous example, this requires the use of the MGT data structure for handling synchronization of the data streams. 


## Reading in multiple data files

We start by reading in three files from the same recording session: video (.mp4), audio (.wav) and motion capture data (.tsv):

    mg = mgread('pianist.avi','pianist.wav','pianist.tsv');

This leads to the structure *mg* containting the following information: 

![An MG structure in Matlab](../fig/mg-structure_250.png)

These are three very different types of files, and they therefore have to be treated differently inside of Matlab. The aim is that MGT should take care of most of these differences, so that you can work on the MGT structure directly. 


## Trimming the structure

The benefit of using an MGT structure is that it will handle the trimming of all related files and data: 

    mgseg = mgreadsegment(mg,10,30);

Here *mgseg* is a new (and complete) structure that can be used for further processing. 

    mgsegmo = mgmotion(mgseg,'Diff','Regular',0.1);


## Plotting together

The function mgvideoplot plots the horizontal and vertical motiongram combined with mocapgram over time.

    mgvideoplot(mgsegmo);


Next, we can investigate the audio recording. mgwaveplot plots the waveform of audio, root mean square, and their spectrum.

    mgwaveplot(mgsegmo);



## Periodicity

Next,the periodicity of movement might be investigated from the quantity of motion. Let's
have a look at it.

    [per,ac,eac,lag] = mgautocor(mgsegmo,'video');

The autocorrelation function for the data shows periodicities:

    plot(lag, ac), xlabel('Period / secs')

The enhanced autocorrelation function for the same data looks like this:
 
    plot(lag, eac), xlabel('Period / secs')


## Statistics

If we want to look at some features of motion image, function mgstatistics can generate
first order and second order features.

    features1 = mgstatistics(mgsegmo,'Video','FirstOrder');
    features2 = mgstatistics(mgsegmo,'Video','SecondOrder');



{% include links.md %}
