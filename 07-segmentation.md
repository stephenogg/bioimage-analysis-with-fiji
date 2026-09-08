---
title: "Segmentation"
teaching: 50
exercises: 25
---

:::::::::::::::::::::::::::::::::::::: questions

- What is segmentation?
- How can objects be separated from the background?
- What is a binary image?
- How can we evaluate whether a segmentation is successful?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Explain the purpose of image segmentation.
- Generate binary images using thresholding.
- Compare manual and automatic thresholding methods.
- Interpret and evaluate binary masks.
- Describe the relationship between segmentation and quantitative measurements.

::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction

Many biological image-analysis workflows are ultimately concerned with measuring objects.

For example:

- How many nuclei are present?
- What is the average size of a cell?
- How many bacteria are visible in an image?
- What proportion of a tissue section expresses a marker?

Before we can answer these questions, we must first identify the structures that we wish to measure.

This process is called **segmentation**.

Segmentation separates the image into regions representing:

- objects of interest (foreground)
- everything else (background)

A successful segmentation allows individual objects to be measured, counted, and compared.

## What Is Segmentation?

Consider a fluorescence image of cell nuclei.

To a human observer, identifying the nuclei may be straightforward.

However, a computer sees only a matrix of intensity values.

Segmentation converts these intensity values into a simplified representation where pixels are classified as either:

`Foreground` or `Background`


The result is often called a **binary mask**, it has only two values. 
Many image processing programs create binary images with values of 0 an 1. 
Fiji creates binary masks with values 0 and 255.

::::::::::::::::::::::::::::::::::::: challenge

Consider a fluorescence image containing nuclei.

Which pixels should be classified as foreground and which should be classified as background?

:::::::::::::::::::::::: solution

Pixels belonging to nuclei should be classified as foreground.

Pixels not belonging to nuclei should be classified as background.

The challenge of segmentation is determining where the boundary between foreground and background lies.

:::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

## Thresholding

One of the simplest and most widely used segmentation methods is **thresholding**.

Thresholding classifies pixels according to their intensity values.

For example:

```text
Intensity > Threshold
        ↓
    Foreground

Intensity ≤ Threshold
        ↓
    Background
```

Pixels brighter than the chosen threshold become foreground.

Pixels darker than the threshold become background.

## Applying a Threshold

Open the sample image:

```text
File → Open Samples → HeLa Cells
```

Split the channels and select the blue DAPI channel, containing clearly visible nuclei.

Open the Threshold window:

```text
Image → Adjust → Threshold...
```

A red overlay is displayed.

The overlay indicates which pixels will be included in the foreground.

Move the threshold sliders and observe how the highlighted regions change.

::::::::::::::::::::::::::::::::::::: challenge

Adjust the threshold values.

What happens when the threshold is set:

- too low?
- too high?

:::::::::::::::::::::::: solution

If the threshold is too low:

- background pixels may be incorrectly included
- neighbouring objects may merge together

If the threshold is too high:

- dim regions of objects may be lost
- some objects may disappear completely

:::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

## Manual Thresholding

Sometimes a threshold can be selected manually.

This approach allows the user to visually inspect the segmentation result and choose a threshold appropriate for the image.

Manual thresholding can be useful when:

- analysing a small number of images
- image quality varies considerably
- expert knowledge is required

However, manual thresholding can also introduce subjectivity.

Different users may choose different threshold values.

## Automatic Thresholding

To improve consistency, Fiji provides a variety of automatic thresholding methods.

Examples include:

- Otsu
- Triangle
- Mean
- Li
- Yen

These methods calculate a threshold automatically based on the intensity distribution of the image.

Within the Threshold window, choose several different methods from the method drop-down menu.

Observe how the segmentation changes.

::::::::::::::::::::::::::::::::::::: challenge

Compare two or more automatic thresholding methods.

Do they produce identical segmentation results?

:::::::::::::::::::::::: solution

No.

Different algorithms make different assumptions about the image intensity distribution.

As a result, different methods often produce different thresholds and different segmentation results.

:::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

## Creating a Binary Mask

Once a satisfactory threshold has been selected:

1. Open:

   ```text
   Image → Adjust → Threshold...
   ```

2. Select a threshold.
3. Click:

   ```text
   Apply
   ```

Fiji converts the image into a binary image.

A binary image contains only two values:

```text
0   = Background

255 = Foreground
```

Biological structures are represented as white pixels and the background as black pixels.

The binary image is often referred to as a **binary mask**.

## Binary Images

A binary image is much simpler than the original image.

The original image contains intensity information:

```text
0 – 255
```

or:

```text
0 – 65535
```

depending on image bit depth.

The binary mask contains only:

```text
Object
```

or:

```text
Background
```

information.

The original intensity measurements are discarded.

Only object locations remain.

::::::::::::::::::::::::::::::::::::: challenge

Create a binary mask from the HeLa Cells image.

Can you identify all the structures you intended to segment?

Are any structures missing or incorrectly included?

:::::::::::::::::::::::: solution

The answer depends on the chosen threshold.

The goal is to identify the structures of interest while excluding as much background as possible.

:::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

## Evaluating Segmentation Results

Not every segmentation is a good segmentation.

When evaluating a segmentation, consider the following questions:

- Are all objects detected?
- Is background excluded?
- Have neighbouring objects merged together?
- Have objects been fragmented into multiple pieces?
- Does the segmentation reflect biological reality?

A segmentation should support the measurements you wish to make.

::::::::::::::::::::::::::::::::::::: challenge

Inspect your binary mask carefully.

Can you identify any of the following problems?

- Missing objects
- Merged objects
- Fragmented objects
- Background incorrectly classified as foreground

:::::::::::::::::::::::: solution

Most segmentation results contain imperfections.

The goal is not necessarily to achieve perfection but to produce a segmentation that accurately represents the structures being measured.

:::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

## Segmentation Determines What Gets Measured

Every downstream measurement depends upon the segmentation.

Imagine that one threshold produces:

```text
120 nuclei
```

while another threshold produces:

```text
150 nuclei
```

The resulting biological conclusions may differ substantially.

Similarly, object area measurements depend directly on the boundaries defined during segmentation.

For this reason, segmentation should always be evaluated critically.

::::::::::::::::::::::::::::::::::::: callout

## Segmentation Is A Scientific Decision

Segmentation is not merely a computational step.

Every segmentation reflects decisions about:

- what constitutes an object
- what constitutes background
- which structures should be included in measurements

Good segmentation combines image-analysis techniques with biological knowledge.

::::::::::::::::::::::::::::::::::::::::::::::::

## Binary Masks Are Often Imperfect

Thresholding frequently produces masks that contain problems such as:

- small noisy objects
- holes within objects
- merged neighbouring objects
- fragmented structures

Fortunately, these problems can often be corrected.

In the next episode we will learn how to refine binary masks using morphological operations such as:

- Fill Holes
- Erode
- Dilate
- Open
- Close
- Watershed

These operations help improve segmentation results before object counting and measurement.

## Discussion

Thresholding is one of the most common segmentation techniques used in biological image analysis.

It is:

- simple
- fast
- reproducible

However, thresholding is not always sufficient.

Complex images may require additional preprocessing or more advanced segmentation approaches.

Nevertheless, understanding thresholding provides an essential foundation for later object analysis workflows.

## Looking Ahead

The binary masks created during segmentation are rarely perfect.

In the next episode we will improve these masks using morphological operations that:

- remove artefacts
- fill holes
- separate touching objects

before moving on to object counting and measurement.

## Key Points

::::::::::::::::::::::::::::::::::::: keypoints

- Segmentation separates foreground objects from background.
- Thresholding is a common segmentation technique based on pixel intensity.
- Fiji supports both manual and automatic thresholding methods.
- Binary masks contain only foreground and background information.
- Different threshold choices can produce different measurements.
- Segmentation quality affects all downstream analyses.
- Binary masks often require refinement before object counting and quantification.

::::::::::::::::::::::::::::::::::::::::::::::::
