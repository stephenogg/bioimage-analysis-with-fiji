---
title: "Preparing Images for Analysis"
teaching: 45
exercises: 20
---

:::::::::::::::::::::::::::::::::::::: questions

- Why do images require preprocessing?
- What types of image artefacts can affect analysis?
- How can Fiji improve image quality prior to segmentation?
- How do we decide which processing operations to apply?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Describe common image artefacts encountered in microscopy images.
- Apply smoothing filters in Fiji.
- Perform background subtraction.
- Compare images before and after processing.
- Explain how preprocessing influences downstream image analysis.

::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction

Real microscopy images are rarely perfect.

Images may contain:

- noise
- uneven illumination
- background fluorescence
- detector artefacts
- out-of-focus signal

These imperfections can interfere with:

- object detection
- segmentation
- measurements
- quantitative analysis

Image preprocessing aims to improve image quality before further analysis.

However, image processing should never be performed simply because it makes an image look nicer.

Every processing step should support a specific analytical goal.

## Why Preprocess Images?

Imagine attempting to identify nuclei in a noisy image.

Random fluctuations in pixel intensity may be mistaken for biological structures.

Similarly, uneven illumination may cause some objects to appear bright and others dim, even when they are biologically identical.

Preprocessing can help:

- reduce noise
- remove background signal
- improve object visibility
- improve segmentation performance

::::::::::::::::::::::::::::::::::::: challenge

What problems might arise if you attempted to segment a noisy image?

:::::::::::::::::::::::: solution

Noise can produce:

- false objects
- missing objects
- inaccurate object boundaries

These problems can affect downstream measurements and biological conclusions.

:::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

## Signal and Noise

Open the Fiji sample image:

```text
File → Open Samples → HeLa Cells
```

Microscopy images contain both:

- signal
- noise

The **signal** corresponds to the biological structures we wish to analyse.

The **noise** consists of unwanted variations in intensity that do not represent real structures.

Noise can arise from:

- photon statistics
- electronic camera noise
- specimen preparation
- image acquisition conditions

Zoom into the image.

Can you identify small intensity fluctuations that do not appear to represent real biological structures?

## Smoothing Filters

One common preprocessing approach is smoothing.

Smoothing reduces local intensity variations (noise) and makes biological structures easier to identify.

### Mean Filter

Open:

```text
Process → Filters → Mean...
```

The mean filter replaces each pixel value with the average value of neighbouring pixels.

### Gaussian Blur

Open:

```text
Process → Filters → Gaussian Blur...
```

Gaussian smoothing is one of the most commonly used filters in bioimage analysis.

Try values such as:

```text
Sigma = 1
```

and:

```text
Sigma = 2
```

Compare the processed image to the original image.

You should notice:

- reduced noise
- smoother appearance
- slightly blurred edges

::::::::::::::::::::::::::::::::::::: challenge

Apply increasing values of Gaussian blur to the image.

At what point do biological structures begin to lose useful detail?

:::::::::::::::::::::::: solution

There is no single correct answer.

Small amounts of smoothing may reduce noise while preserving biological structures.

Excessive smoothing removes information and can make segmentation more difficult.

:::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: callout

## More Processing Is Not Better

Each image-processing operation changes the image.

Applying more filters does not necessarily improve an analysis.

Every processing step should have a specific purpose and a biological justification.

::::::::::::::::::::::::::::::::::::::::::::::::

## Comparing Smoothing Filters

Different filters affect images in different ways.

The choice of filter depends on the problem you are trying to solve.

Open the sample image:

```text
File → Open Samples → HeLa Cells
```

We will compare two commonly used smoothing filters:

- Gaussian Blur
- Median Filter

Both filters can reduce noise, but they do so in different ways.

## Gaussian Blur

Open:

```text
Process → Filters → Gaussian Blur...
```

The Gaussian filter replaces each pixel value using a weighted average of neighbouring pixels.

Apply a small blur:

```text
Sigma = 1
```

Notice that:

- noise is reduced
- intensity changes become smoother
- object edges become slightly blurred

Gaussian filtering is often used prior to thresholding and segmentation.

## Median Filter

Now re-open the original image and select:

```text
Process → Filters → Median...
```

Apply a radius of:

```text
Radius = 1
```

or:

```text
Radius = 2
```

The median filter replaces each pixel value with the median value of neighbouring pixels.

Unlike Gaussian filtering, the median filter is less influenced by isolated bright or dark pixels.

As a result:

- noise is reduced
- edges are often preserved more effectively
- small isolated artefacts may be removed

::::::::::::::::::::::::::::::::::::: challenge

Apply both a Gaussian blur and a median filter to the same image.

Compare the resulting images.

Which filter appears to preserve object boundaries more effectively?

:::::::::::::::::::::::: solution

The median filter often preserves sharp edges better than the Gaussian filter.

This is because the median filter replaces pixel values using the median of neighbouring pixels rather than a weighted average.

Gaussian filtering generally produces a smoother image, but can blur object boundaries.

:::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

## Choosing A Filter

Neither filter is universally better.

Different filters are appropriate for different situations.

| Filter | Typical Effect |
|----------|----------|
| Gaussian Blur | Smooths noise but can blur edges |
| Median Filter | Reduces isolated noise while preserving edges |

When choosing a filter, consider:

- the type of noise present
- the structures being analysed
- the requirements of downstream analysis

For example:

- A small Gaussian blur is commonly used before thresholding.
- A median filter may be useful when images contain isolated bright or dark pixels.

::::::::::::::::::::::::::::::::::::: callout

## Every Filter Changes Your Data

Filtering operations permanently alter pixel values.

Before applying a filter, ask yourself:

> What problem am I trying to solve?

A filter should only be applied when it improves a subsequent analysis step, such as segmentation or measurement.

The goal is not to make the image look nicer. The goal is to improve the reliability of the analysis.

::::::::::::::::::::::::::::::::::::::::::::::::

## Background Signal

Many fluorescence images contain unwanted background signal.

Sources of background include:

- autofluorescence
- out-of-focus light
- detector offsets
- uneven illumination

Background signal can make objects appear less distinct and can affect measurements.

Open the Fiji sample image:

```text
File → Open → data/06-image-preprocessing/DAPI_etoposide07_R3D.ome.tif
```

Notice that the image contains both bright structures (nuclei) and diffuse background signal.

## Background Subtraction

A common way to reduce background signal is to use Fiji's background subtraction tool.

Select:

```text
Process → Subtract Background...
```

Fiji uses a rolling-ball algorithm to estimate and remove slowly varying background intensity.

The most important parameter is:

```text
Rolling Ball Radius
```

The radius controls the scale of structures considered background. 
Things that are smaller than the radius can be removed.

Try several different values and compare the resulting images.

Observe how the appearance of the image changes.




::::::::::::::::::::::::::::::::::::: challenge

Apply background subtraction using several rolling-ball radii.

Which values remove the background while preserving the structures of interest?

:::::::::::::::::::::::: solution

The optimal radius depends on the size of the structures being analysed.

A radius that is too small may remove biological features.

A radius that is too large may leave unwanted background signal.

:::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

## Why Background Subtraction Matters

Background signal does not simply make an image look noisier, 
it can directly affect quantitative measurements.

Imagine two fluorescent objects with measured intensities of 120 and 100 arbitrary units. 
At first glance, the brighter object appears to be 20% brighter than the dimmer one. 
However, if both objects are on a background of 80 intensity units, 
the biologically relevant fluorescence signals are actually 40 and 20 units after background subtraction. 
The brighter object is now twice as bright as the dimmer one. 
In this case, the background signal masked the true difference between the objects.

Alternatively, if the background varies across an image, 
two identical structures may appear to have different intensities simply 
because one lies in a brighter region of the image (due to background variability) than the other.

For this reason, background subtraction is often an essential step in quantitative fluorescence microscopy. 
Accurate measurements depend on separating the fluorescence signal produced by the 
biological structure of interest from unwanted background signal arising from the specimen, microscope, or detector.


## Comparing Before and After

Image processing should always be evaluated critically.

Arrange the original and processed images side by side.

Ask yourself:

- What improved?
- What became worse?
- Are structures easier to identify?
- Would segmentation be easier now?

Remember that every image-processing operation alters the image.

The goal is to improve analysis performance, not simply visual appearance.

::::::::::::::::::::::::::::::::::::: challenge

Compare an original image and a processed image.

Identify one feature that improved and one feature that became less clear after processing.

:::::::::::::::::::::::: solution

Answers will vary.

Common observations include:

- reduced noise
- improved contrast
- softer object boundaries
- loss of fine detail

The usefulness of a processing step depends on the analytical goal.

:::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

## Documenting Processing Steps

Image processing choices should be documented.

For example:

```text
Gaussian Blur
Sigma = 1.5
```

or:

```text
Subtract Background
Rolling Ball Radius = 50 pixels
```

Recording processing parameters allows analyses to be:

- reproduced
- reviewed
- shared with collaborators

Reproducibility is a central principle of quantitative image analysis.

::::::::::::::::::::::::::::::::::::: callout

## Processing Parameters Matter

Two researchers may apply different preprocessing settings to the same image.

Different settings can produce different segmentation results and different measurements.

Whenever possible, document every processing step and its parameters.

::::::::::::::::::::::::::::::::::::::::::::::::

## Discussion

Suppose two researchers analyse the same image.

One researcher applies heavy smoothing and aggressive background subtraction.

The other performs only minimal preprocessing.

Should they expect to obtain identical segmentation results?

Probably not.

Preprocessing decisions influence every subsequent stage of the workflow.

For this reason, preprocessing should be guided by the biological question and not by visual preference.

## Looking Ahead

Preprocessing is often performed to prepare images for segmentation.

In the next episode we will learn how to separate foreground objects from the background using thresholding and binary images.

The workflow is beginning to take shape:

```text
Raw Image
    ↓
Preprocessing
    ↓
Segmentation
    ↓
Measurements
```

## Key Points

::::::::::::::::::::::::::::::::::::: keypoints

- Real microscopy images frequently contain noise and background signal.
- Preprocessing can improve downstream image analysis.
- Common preprocessing techniques include smoothing and background subtraction.
- Every processing operation changes the image.
- Processing should be guided by analysis goals, not aesthetics.
- Processing parameters should be documented for reproducibility.
- Preprocessing is often an important step before segmentation.

::::::::::::::::::::::::::::::::::::::::::::::::
