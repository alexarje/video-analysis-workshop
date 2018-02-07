---
title: "Advanced techniques"
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


## mgdemo2

This example shows how you can read video, audio, mocap files into Matlab and how
you can preprocess the data. The data is stored as musical gestures data structure after
importing. The Musical Gestures Toolbox includes mgdemo2 that contains video, audio,
mocap recordings. It is used for the example of this manual. It extracts 20 seconds from 5
seconds to 25 seconds of the video recording. After this, it should map the same temporal
segment to audio and mocap data recording.
mg = mgread(’dance.mp4’);
mgseg = mgvideoreader(mg,’Extract’,5,25);
mgseg = mgmap(mgseg,’Both’,’dacne.wav’,’dance.c3d’);
A musical gestures data structure is imported into Matlab workspace. It shows three
substructs, video, audio, mocap, respectively. The video recordings are the nine people
dancing to music. The length of the video is around 10 minutes. In this demo, we will find
that preprocessing the video recording is very important if the video recordings are quite
large. Because the frame size is 1080 by 1920, this is very high resolution video recording.
In partice, 320 by 480 is enough to compute the motion gram and extract the features. In
35order to speed up the the calculation, resample the video is necessary.
mgsam = mgvideosample(mgseg,[4,4],’dancesamplevideo.avi’);
The function mgvideosample resamples the video recording. After sampling, the size of
each frame is reduced into 270 by 480. Here because of the permission issue, the figure is
not shown here, we will only show the motion image and motion gram results.
Now, the musical gestures data structure mgsam contains the same temporal segment of
video, audio, mocap data. Next, you can do analysis based on this data structure.
mgsammo = mgmotion(mgsam,’Diff ’);
The quantity of motion and centroid of motion are showed in following figures.
Figure 12: Qom and Com of dancing video
The periodicity is estimated by mgautocor based on quantity of motion. The func-
tion waveplot shows the RMS, waveform, spectrogram and spectrum of RMS in one figure.
[per,ac,eac,lag] = mgautocor(mgsammo);
36Figure 13: Motion grams of dancing video
mgwaveplot(mgsammo);
In the enhanced period, the first nonzero lag is 0.5 seconds. It will be interesting
to investigate the tempo of the sound and spectrum of the quantity of motion. Here the
tempo of the sound can be estimated by funtion mirtemp in MIR Toolbox. It is 122bpm,
namely around 2 beats per second. Figure 15 shows how the QoM changes according to
the RMS.

Next, we try to analysis the movements according to mocap data set. The similarity
between 9 persons is calculated by function mgsimilarity in MGT box. However, before
computing, the mocap data should be preprocessed. Firstly, take the absolute difference
between two successive frames as the way of computing motion image. Secondly, norm
the dataset, this is simply done by function mcnorm in Mocap tool box.
37Figure 14: Periodicity estimation of dancing
Figure 15: QoM and RMS
sm = mgsimilarity(mgsammo.mocap.data);
To analysis movements of every person, the peroidicity of absolute difference move-
ment of each person can be computed by the same way. Figure 19 shows the each person’s
38Figure 16: plot waveform, rms, spectrogram of audio
Figure 17: Similarity matrix of 9 persons
periodicity of absolute difference movement. From this view, person 2 move to music very
regularly.
39Figure 18: Similarity matrix of spectrum of 9 persons
Figure 19: Periodicity of each person
40