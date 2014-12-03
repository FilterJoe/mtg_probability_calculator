# Joe Golton's Magic the Gathering (mtg) Land Probability Calculator

> Just let me see it! Web version (NBViewer):
[mtg_probability_calculator](http://nbviewer.ipython.org/github/FilterJoe/mtg_probability_calculator/blob/master/mtg_probability_calculator.ipynb)

Note that the interactive sliders do not appear or work on the web version of this as of December 3, 2014. When iPython Notebook moves to version 3.0, it will work. Until then, interactivity will only work if the notebook is downloaded to a local system where iPython Notebook is up and running.

## Introduction

This land probability calculator for Magic the Gathering is a fun way for me to cement my understanding of probability theory ([DeGroot and Schervish](http://www.amazon.com/Probability-Statistics-4th-Morris-DeGroot/dp/0321500466), chapter 1), practice probability calculation in Python, and at the same have an interesting tool to support my family's new hobby.

## What this does

Magic the Gathering intro packs recommend the following defaults for land construction:

* 60 card deck
* 24 lands in the deck

There is better than an 85% chance of starting with at least 2 lands when drawing your initial 7 card hand, which the tool shows with its default settings. You can use the sliders to change around any of the numbers and see how probability is impacted for each possible number of lands appearing in the initial hand draw.

It can be useful to think of land tappable creatures as lands for the purposes of this calculation. For example, if you have 20 lands and 4 Mystic Elves, that is essentially equivalent to 24 lands (well, not really, because there are many more ways to lose a Mystic Elf than a land . . . but it's still useful to think of your starting hand this way as you're not likely to lose a Mystic Elf on turn 1).

You may want to consider mulligans in your calculation. Move the mulligan slider to "1" and you'll see the probabilities for the subsequent 6 card draw, as well as the chances of getting below or above your desired range of lands to start with.

I assume for this analysis that mulligans automatically occur when below minimum required land or above maximum required land, but not otherwise. Therefore, the probability, p, of having too little land after 1 or 2 draws (2nd draw only if 1st draw outside of target range) is:

p = p1(below) * (p0(below) + p0(above))

where

* p0 represents probability in a 7 card draw (zero mulligans)
* p1 represents probability in a 6 card draw (1 mulligan)
* p0(below) represents probability that the number of cards drawn is below the required minimum

## Why iPython Notebook

iPython Notebook is a natural match for anything that combines math, coding, and (interactive) graphical output. I can quickly prototype and annotate my experiments. I can get output that is cleaner, clearer, and more flexible, including LaTex formatted equations and embedded plots. And the ability to rerun a small part of the code without having to start over from the beginning saves time.

## Requirements

* Python 2.7.6
* ipython==2.1.0
* numpy==1.8.1
* matplotlib==1.3.1
* scipy==0.14.0

## How to Launch iPython Notebook

iPython notebook's default behavior does not allow inline plots, nor does it allow matplotlib's default behavior of keeping the active plot open so that you can draw it multiple times. Most exercises require this behavior. It can be enabled by starting iPython notebook as follows:

ipython notebook --InlineBackend.close_figures=False --IPKernelApp.matplotlib='inline'

I am not using pylab --inline, because: [No Pylab Thanks] (http://carreau.github.io/posts/10-No-PyLab-Thanks.ipynb.html)

## 
