---
title: "Images, Pixels and Metadata"
teaching: 45
exercises: 15
---

:::::::::::::::::::::::::::::::::::::: questions

- How are digital images represented inside a computer?
- What information is stored alongside an image?
- Why is image metadata important?
- Why does image calibration matter for quantitative measurements?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Describe an image as a collection of pixels.
- Identify common image dimensions and image types.
- Inspect image metadata in Fiji.
- Explain the importance of spatial calibration.
- Distinguish between pixel measurements and real-world measurements.

::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction

Before we can analyse biological images, we must understand what an image
actually is.

Although images appear to us as visual representations of biological samples,
computers do not "see" cells, nuclei, bacteria, or tissues.

Instead, computers store images as collections of numerical values.

In this episode we will explore how images are represented and how Fiji can be
used to inspect image information and metadata.

## Opening an Image

Start Fiji and open one of the built-in sample images.

Select:  `File → Open Samples → HeLa Cells`

![HeLa Cells](fig/02-images-pixels-metadata/hela-cells.png){alt="three channel fluorescence micrograph of 4 HeLa Cells."}

The image should appear in a new image window.

Note that Fiji uses floating windows. 

Take a moment to inspect the image.

What biological structures can you identify?

Although we immediately recognise cells and nuclei, the computer only sees a
collection of numbers arranged in a grid.

## Images Are Made Of Pixels

Digital images consist of small elements called **pixels**.

Pixel is short for:  `Picture Element`

Each pixel stores a numerical value.

For grayscale images:

- low values appear dark
- high values appear bright

Together, large numbers of pixels create the images we recognise.

Zoom into the image using:  `View → Zoom → In`

or the magnifying glass tool. (or use the `+` and `-` keys.)

At high magnification the individual pixels become visible.

::::::::::::::::::::::::::::::::::::: challenge

Zoom into the image until individual pixels can be seen.

What shape are the pixels?

:::::::::::::::::::::::: solution

Pixels are arranged in a grid and appear as square elements.

Each pixel stores a numerical intensity value.

:::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

## Image Dimensions

Biological images frequently contain more information than a simple
two-dimensional picture.

An image may include:

- Width (X)
- Height (Y)
- Channels (C)
- Depth (Z)
- Time (T)
- Well number

Modern microscopy experiments often generate multidimensional datasets.

## Exploring Image Properties

With the sample image open, select:  `Image → Properties`


A dialog box appears containing information about the image.

![Image Info](fig/02-images-pixels-metadata/image-properties.png){alt="Fiji's Image Info Window"}

This information includes:

- image dimensions
- pixel size
- units
- number of slices
- number of frames

Collectively, this information forms part of the image metadata.

Fiji stores information describing the image
alongside the pixel data, if the image has the metadata embedded.


## What Is Metadata?

Metadata is often described as:

> Data about data or Data that describes data

For microscopy images, metadata may include:

- pixel size
- microscope settings
- objective lens
- channel names
- acquisition date
- exposure information
- dimensional information

Without metadata, it can be difficult or impossible to interpret image
measurements correctly.

## Why Calibration Matters

Suppose two nuclei each occupy:

```text
1000 pixels
```

Are they the same size?

Not necessarily.

The answer depends on the size represented by each pixel.

If:

```text
1 pixel = 0.1 µm
```

the object has a different physical size than if:

```text
1 pixel = 1.0 µm
```

Measurements reported in pixels are often difficult to interpret biologically.

Calibration allows measurements to be expressed in meaningful units such as:

- micrometres (µm)
- square micrometres (µm²)
- millimetres (mm)


## Bit Depth

Pixel values are stored using a specific ranges of values that are computer friendly. 
These ranges are called  the image "bit-depth".

Common bit depths include:

| Bit Depth | Possible Values | Type
| ---------- | ---------- | -------- |
| 8-bit | 0 to 255 | Positive Integer
| 16-bit | 0 to 65,535 | Positive Integer
| 32-bit | Large numerical range | Floating Point (Fractions!)

Higher bit depths allow finer graduations between intensity measurements 
and the storage of non-integer and negative values.

In fluorescence microscopy, 16-bit images are commonly used.

To view image information, select:  `Image → Show Info`

![Image Info](fig/02-images-pixels-metadata/image-info.png){alt="Fiji's Image Info Window"}

## Why Metadata Must Be Preserved

Many image-analysis problems begin when image data are exported incorrectly.

For example:

- calibration may be lost
- channel information may disappear
- bit-depth may be changed
- dimensional information may be removed

When image information is lost, quantitative measurements become unreliable.

Good scientific practice includes preserving both:

- image data
- metadata

throughout an analysis workflow.

::::::::::::::::::::::::::::::::::::: callout

## Images Are More Than Pictures

A microscopy image contains two equally important components:

1. Pixel data
2. Metadata

Removing the metadata is similar to removing labels from measurements in a
spreadsheet.

The numbers remain, but their meaning may be lost.

::::::::::::::::::::::::::::::::::::::::::::::::

## Looking Ahead

Now that we understand how images are represented inside a computer, we can
begin making quantitative measurements.

In the next episode we will learn how to:

- create regions of interest (ROIs)
- measure biological structures
- record quantitative measurements using Fiji

## Key Points

::::::::::::::::::::::::::::::::::::: keypoints

- Digital images are collections of pixels.
- Each pixel stores a numerical intensity value.
- Biological images may contain multiple dimensions, including channels, z-slices and timepoints.
- Metadata describes how an image was acquired and interpreted.
- Calibration is required to convert pixel measurements into biological units.
- Bit depth influences the range of intensity values that can be recorded.
- Quantitative image analysis depends on preserving both image data and metadata.

::::::::::::::::::::::::::::::::::::::::::::::::
