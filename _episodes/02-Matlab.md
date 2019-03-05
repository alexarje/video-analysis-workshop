---
title: "Getting around Matlab"
teaching: 5
exercises: 10
questions:
- "How do you get set up in Matlab?"
objectives:
- "Understand that Matlab is a text-based programming environment."
- "Learn how to set the path for toolboxes."
keypoints:
- "A semicolon at the end of a line will not display the commands output."
- "Toolboxes need to be added to path before they can be used."
---


Before we get started with MGT, we will familiarize ourselves just a little bit in Matlab.


## Your first Matlab scripting

Matlab is a scripting language, in which you type a message in the command window and press <kbd>Return</kbd>. Try to type in the following lines:

~~~
1+1
~~~
{: .matlab}

One of the strengths of Matlab is to be able to work with symbols. Try this:

~~~
a=1
b=2
c=a+b
~~~
{: .matlab}

You can also try combinations of symbols and numbers:

~~~
(a+1)*(b+2)
~~~
{: .matlab}


## The semicolon

The semicolon is important in Matlab. Look at the difference between this:

~~~
a+b;
~~~
{: .matlab}

and this message:

~~~
a+b
~~~
{: .matlab}


## Plotting

One of the big strengths of Matlab is all the plotting functions. Try this example:

~~~
xlabel('x = 0:2\pi')
ylabel('Sine of x')
title('Plot of the Sine Function')
~~~
{: .matlab}

That is about what you need to know to get started with MGT.



> ## Escape
> If you ever get stuck in Matlab, you can press <kbd>Ctrl</kbd>+<kbd>C</kbd> to interrupt the running process.
{: .callout}


## Toolboxes

One of the strenghts of Matlab is that there are lots of toolboxes available. The MGT is one such toolbox, and it builds on some other toolboxes: [matlabPyrTools](https://github.com/LabForComputationalVision/matlabPyrTools/archive/master.zip), [MoCap Toolbox](https://www.jyu.fi/hum/laitokset/musiikki/en/research/coe/materials/mocaptoolbox) and [MIRtoolbox](https://www.jyu.fi/hum/laitokset/musiikki/en/research/coe/materials/mirtoolbox). For these toolboxes to work properly, we need to add them to the *path* of Matlab. That is a location for extra stuff that we want to add. This should typically be a folder in your home folder.

## Adding path
> Add the files from the [workshop zip-file](../setup.html) to your Matlab path: under the "Home" section, click "set path". Click the "Add Folder" button and choose the "source-code" folder and finally click "save".
{: .challenge}

It is also possible to set the path via the command line in Matlab, using something like:

    addpath('~/Documents/Toolboxes');



When you are done, you should be able to run the following command:

~~~
mgcheck
~~~
{: .matlab}


{% include links.md %}
