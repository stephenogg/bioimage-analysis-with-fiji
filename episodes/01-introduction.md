---
title: "Introduction to Bioimage Analysis and Fiji"
teaching: 30
exercises: 15
---

:::::::::::::::::::::::::::::::::::::: questions

- What is bioimage analysis?
- Why do researchers use bioimage-analysis workflows?
- What is Fiji and how is it used in biological research?
- What makes an image-analysis workflow reproducible?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Describe the role of bioimage analysis in biological research.
- Explain why images should be treated as scientific data.
- Identify the major steps in a bioimage-analysis workflow.
- Navigate the Fiji user interface.
- Explain the importance of reproducibility in image analysis.

::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction

Modern biological research generates vast quantities of image data.

Microscopy facilities can produce hundreds, thousands, or even millions of
images during a single experiment.

As datasets grow larger, manual analysis becomes increasingly difficult,
time-consuming, and prone to bias.

Bioimage analysis provides a framework for extracting quantitative information
from image data in a reproducible and scalable manner.

Throughout this lesson, we will use **Fiji** to develop image-analysis
workflows that transform images into quantitative biological measurements.

## What Is Fiji?

Fiji ("Fiji Is Just ImageJ") is a free, open-source image-analysis platform
widely used in the life sciences.

It combines:

- ImageJ
- a large collection of community-developed plugins
- tools for image visualisation
- tools for measurement and quantification
- tools for automation and batch processing

Fiji has become one of the most commonly used image-analysis platforms in
biological research because it is:

- free
- flexible
- extensible
- reproducible

Throughout this lesson we will use graphical tools within Fiji to build a
complete image-analysis workflow.

## Starting Fiji

Launch Fiji on your computer.

After Fiji opens, you should see the Fiji toolbar.

![Fiji Main Window](fig/01-introduction/fiji-main-window.png){alt="Fiji's main interface window"}


The toolbar provides access to:

- selection tools
- drawing tools
- measurement tools
- image navigation tools
- the menu bar (in Windows/Linux)
- the search box
- information about the current image

Spend a few moments exploring the interface.

Do not worry about understanding every tool yet.

We will introduce them as they become relevant.

::::::::::::::::::::::::::::::::::::: challenge

Open Fiji and identify three tools on the toolbar that you have not used
before.

What do you think they might be used for?

:::::::::::::::::::::::: solution

Answers will vary.

The purpose of this exercise is to encourage learners to explore the interface
and become comfortable locating tools.

:::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

## Images Are Data

Many researchers initially think of images as pictures.

However, for image analysis, images are better thought of as data.

Consider the following questions:

- How many cells are present in an image?
- What is the average area of each nucleus?
- How much fluorescence is present within each cell?
- Does a treatment affect cell morphology?
- How does protein localisation change over time?

All of these questions can be answered using information contained within image
pixels.

Images are therefore measurements.

Our goal in bioimage analysis is to extract meaningful biological information
from these measurements.

## The Bioimage Analysis Workflow

Although image-analysis workflows vary between experiments, most follow a
similar structure.

```text
Acquire Images
       ↓
Exploratory Data Analysis
       ↓
Preprocess Images
       ↓
Segment Objects
       ↓
Measure Features
       ↓
Analyse Results
```

This lesson will follow exactly this workflow.

Each episode introduces one stage of the analysis process and explains why that
step is necessary.

::::::::::::::::::::::::::::::::::::: challenge

Consider a microscopy experiment from your own research.

What measurements could potentially be extracted from the resulting images?

Examples might include:

- object counts
- object size
- object shape
- fluorescence intensity
- distances between objects

:::::::::::::::::::::::: solution

There is no single correct answer.

Any property that can be quantified from image pixels may potentially be
measured and used to answer a biological question.

:::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

## Why Not Analyse Images Manually?

Humans are remarkably good at recognising biological structures.

However, manual analysis does not scale well.

Imagine an experiment containing:

- 500 images
- 1,000 cells per image

A researcher would need to inspect approximately:

```text
500,000 cells
```

Even simple measurements become impractical at this scale.

Manual analysis is often:

- slow
- difficult to reproduce
- prone to subjective interpretation
- vulnerable to human error

Automated image analysis allows measurements to be performed consistently and
efficiently.

## Reproducibility

Suppose two researchers independently analyse the same image.

Will they obtain exactly the same result?

Perhaps not.

People make subjective decisions regarding:

- object boundaries
- image quality
- weak signals
- overlapping structures

Image-analysis workflows help reduce this variability.

Rather than relying on undocumented decisions, we can record exactly how an
analysis was performed.

This allows analyses to be:

- repeated
- inspected
- validated
- shared with collaborators

::::::::::::::::::::::::::::::::::::: callout

## A Workflow Is More Important Than A Button Click

One of the goals of this lesson is to develop good image-analysis habits.

It is easy to learn where a particular Fiji command is located.

It is much more valuable to understand:

- why a processing step is required
- when it should be applied
- what effect it has on the data

Good bioimage analysis is built upon scientific reasoning, not memorising menu
commands.

::::::::::::::::::::::::::::::::::::::::::::::::

## A First Look At Automation

One of Fiji's strengths is the ability to automate repetitive analyses.

Later in this lesson we will learn how to:

- record analysis steps
- create simple macros
- process batches of images
- generate reproducible results

Automation allows the same workflow to be applied consistently across entire
datasets.

::::::::::::::::::::::::::::::::::::: challenge

Which of the following tasks would benefit from automated image analysis?

1. Measuring fluorescence intensity in 10,000 cells
2. Counting bacteria in 500 images
3. Measuring organoid size in a screening experiment


:::::::::::::::::::::::: solution

The correct answer is:

```text
All of the above
```

As image datasets increase in size, automated analysis becomes increasingly
important.

:::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

## Looking Ahead

The next episode introduces digital images and image metadata.

We will explore how images are represented inside a computer and why concepts
such as pixels, dimensions, bit depth, and calibration are essential for
quantitative image analysis.

## Key Points

::::::::::::::::::::::::::::::::::::: keypoints

- Bioimage analysis converts images into quantitative measurements.
- Fiji is a widely used platform for biological image analysis.
- Images should be treated as scientific data rather than pictures.
- Most image-analysis workflows consist of inspection, preprocessing, segmentation, and measurement.
- Automated analysis improves scalability and reproducibility.
- Reproducible workflows are more valuable than undocumented manual measurements.

::::::::::::::::::::::::::::::::::::::::::::::::
