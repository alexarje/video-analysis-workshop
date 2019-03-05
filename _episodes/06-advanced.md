---
title: "Advanced techniques"
teaching: 5
exercises: 15
questions:
- "What more advanced features are there?"
objectives:
- "Create more advanced motion videos, using optical flow and video magnification."
- "Extract some statistical features."
keypoints:
- "Optical flow shows the direction of motion, but is much more CPU-consuming."
- "MGT is the starting point for a lot of more advanced analyses."
---


The MGT contains several more advanced analysis features, some with limited documentation, and several that are still in development. We will here look at some of them. 


## Optical Flow

Optical flow is a different motion estimation method, which not only looks at whether pixels change, but also in which directions they change. Thus a motion video created with optical flow, can also show motion vectors. 

    mgmotion('dance.avi','OpticalFlow');

The downside to this, is that it is much more computationally heavy than plain frame differencing. 


## Motion magnification

[Eulerian Video Magnification](http://people.csail.mit.edu/mrub/vidmag/) is a method for amplifying parts of the image that are seemingly "invisible". It requires quite some fine-tuning of the parameters to work properly. Try for example: 

    mg = mgvideomagnify('standstillcrop.avi','IIR',0.4,0.05,10,16,0.1);

or

    mg = mgvideomagnify('standstillcrop','Butter',3.6,6.2,60,90,30,0.3)




{% include links.md %}
