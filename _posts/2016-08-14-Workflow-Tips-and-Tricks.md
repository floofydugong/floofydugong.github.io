---
layout: post
section-type: post
title: Workflow Tips and Tricks
category: Tech
tags: [ 'Workflow', 'Sublime', 'Terminal', 'Python']
---

Each student at Metis is required to investigate and share about two topics relating to the field of data science. These **"investigations"** gives us the opportunity to not only share what we enjoy learning about, but also gives us the chance to practice our oral presentation skills.

This past Friday, I chose to teach about technical **workflow tips and tricks** that I've picked up over these past few years as a developer. A lot of classmates enjoyed the presentation, so I'd thought it be helpful to share my [presentation in PDF format](https://github.com/floofydugong/sf16_ds3/blob/master/investigations/submissions/floofydugong/Workflow%20Tips%20and%20Tricks.pdf) to those interested.

## So what is a workflow?

To help me define what a workflow is, I'll go ahead and start with a simple example. Say you have a few files that you need to remove manually from a folder. Generally, most people would  navigate to their folder using the operating system's explorer to select/delete aforementioned files. The task sounds easy enough, but what happens when you can't click on the filters to easily group the files you need to delete. To make matters worse, the files you needed to review were in the thousands. To sit there and manually sift through each file to check if it needed to be deleted would not only take hours, but may also lead you to possibly skip over files or delete others by accident. Sound familiar?

This is where command line comes into play to help improve this task. Instead of manually finding each file and hitting delete, the same task can be accomplished with the **-rm ** command and **regular expressions** in a user's terminal, which might sound like a lot of fancy mumbo jumbo...but really just looks like this:

```
-rm *name_of_files.*
```

To breakdown the command line above, the "rm" stands for "remove" and the asterisk symbols stand for wild characters. The command will remove anything that has "name_of_file" included within it, without the user having to specify what file types to remove.

To me, being able to accomplish a task is one thing, but being able to complete it efficiently and without error is another. Keeping this in mind, **an optimized workflow can therefore be defined as completing tasks in a manner that is not only efficient but also effective, all while reducing the complexity and time.**

Ben Lorica, who is currently the Chief Data Scientist of O'Reilly Media, Inc, best sums up workflows for Data Scientists when he said:

> "Data scientists tend to use a variety of tools, often across different programming languages. Workflows that involve many different tools require a lot of context-switching which affects productivity and impedes reproducibility"

For a someone who doesn't enjoy overloading his phone/laptop with useless applications, this was music to my ears. I've always been the kind of person who hated switching between different programs to accomplish tasks that were too unique to write scripts for, yet to lengthy to complete manually.

That's where [Sublime Text Editor](https://www.sublimetext.com/) changed everything.

<img src="{{ site.url }}{{ site.baseurl }}/images/SublimeText.png" alt="">

I've always been a long time user, but recently just paid the $70 for a fully licensed editor. Honestly, there's nothing different between the free/paid version, except for the fact that you don't get a pop-up every so often. But the reason why I chose to finally pay for it was because I realized how much I've been using it. In fact, **I'm using it right not to write/commit this blog post (yes! you can do that all from within Sublime with the right workflow! 😉**   If you haven't had a chance yet, check out a few of the awesome functions that Sublime Text can do at [their website](https://www.sublimetext.com/). My favorite is probably the multi-line editing. That seriously changed my workflow life forever. If you don't know that is, just Google it and you'll thank me later.

If you have any cool tips/tricks that help with your daily workflow, let me know in the comments below!