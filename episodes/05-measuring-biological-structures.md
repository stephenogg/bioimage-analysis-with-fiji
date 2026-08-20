---
title: "Measuring Biological Structures"
teaching: 40
exercises: 20
---

:::::::::::::::::::::::::::::::::::::: questions

- How can measurements be made from images?
- What is a Region of Interest (ROI)?
- How does Fiji calculate measurements?
- How can measurement results be recorded and exported?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Create regions of interest using Fiji selection tools.
- Configure Fiji measurement settings.
- Measure the size and intensity of biological structures.
- Use the ROI Manager to organise measurements.
- Interpret information in the Results table.

::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction

One of the primary goals of bioimage analysis is to convert images into
quantitative measurements.

Examples include:

- cell counts
- object area
- fluorescence intensity
- object shape
- distances between structures

Before we can automate these measurements, we must first understand how they
are made.

In this episode we will use Fiji to measure biological structures manually and
record the results.

## Opening an Example Image

Open the Fiji sample image:

```text
File → Open Samples → HeLa Cells
```

This image contains fluorescently labelled HeLa cells.

We will use this image to explore Fiji's measurement tools.

## Regions of Interest (ROIs)

A **Region of Interest (ROI)** defines the area of an image that will be
measured.

ROIs allow us to tell Fiji exactly which pixels should be included in a
measurement.

Common ROI shapes include:

- Rectangles
- Ovals
- Polygons
- Freehand selections
- Lines

Select the **Rectangle Selection Tool** from the toolbar and draw a rectangle
within the image.

The selected region is now an ROI.

## Making a Measurement

With the ROI selected:

```text
Analyze → Measure
```

or press:

```text
M
```

A Results window will appear.

Each row corresponds to a measurement.

By default, Fiji records measurements such as:

- Area
- Mean intensity
- Minimum intensity
- Maximum intensity

The exact measurements depend on the current measurement settings.

::::::::::::::::::::::::::::::::::::: challenge

Create several rectangle selections in different parts of the image and measure
each one.

Do all measurements produce the same result?

Why might they differ?

:::::::::::::::::::::::: solution

Measurements differ because each ROI contains a different set of pixels.

Different pixels have different intensity values and may contain different
biological structures.

:::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

## Choosing What To Measure

Fiji allows us to choose which measurements should be recorded.

Select:

```text
Analyze → Set Measurements
```

A dialog box appears containing many options.

Common measurements include:

- Area
- Mean gray value
- Standard deviation
- Minimum and maximum intensity
- Centroid
- Perimeter
- Shape descriptors

Enable:

- Area
- Mean gray value
- Perimeter

and press **OK**.

Repeat a measurement.

Notice that additional columns have been added to the Results table.

The recorded measurements are determined by the settings selected in this
dialog.

## Measuring Distances

Not all ROIs define areas.

The straight-line tool can be used to measure distances.

Select the **Straight Line Tool** and draw a line across the image.

Choose:

```text
Analyze → Measure
```

Fiji records the line length.

If the image is calibrated, measurements will be reported in physical units.

If calibration is unavailable, measurements are reported in pixels.

::::::::::::::::::::::::::::::::::::: challenge

Use the line tool to measure several structures within the image.

Are all lengths identical?

Would measurements reported in pixels be sufficient for comparing data between
different microscopes?

:::::::::::::::::::::::: solution

No.

Pixel measurements depend on image calibration.

Measurements reported in calibrated units are generally more informative and
easier to compare between experiments.

:::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

## The ROI Manager

As analyses become more complex, it is useful to save and organise ROIs.

Open the ROI Manager:

```text
Analyze → Tools → ROI Manager
```

Create several selections and click:

```text
Add
```

Each ROI is stored within the ROI Manager.

The ROI Manager allows you to:

- save ROIs
- rename ROIs
- display ROIs
- measure multiple ROIs
- reuse ROIs later

This is particularly useful when analysing many structures in a single image.

## Measuring Multiple ROIs

Create several ROIs and add them to the ROI Manager.

Select all ROIs in the ROI Manager and click:

```text
Measure
```

Fiji will measure every ROI and add the results to the Results table.

This approach is much more efficient than measuring objects individually.

::::::::::::::::::::::::::::::::::::: challenge

Create three ROIs and add them to the ROI Manager.

Use the ROI Manager to measure all three simultaneously.

How many rows appear in the Results table?

:::::::::::::::::::::::: solution

One row should be generated for each ROI.

The Results table allows measurements from multiple structures to be collected
and analysed together.

:::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

## The Results Table

The Results table stores measurement outputs.

Each row corresponds to a measurement.

Each column represents a different measurement type.

For example:

| Area | Mean | Perimeter |
|--------|--------|--------|
| 152.4 | 84.2 | 47.1 |
| 201.6 | 102.7 | 58.4 |

Results can be:

- copied
- saved
- exported
- analysed further

To save results:

```text
File → Save As
```

from the Results window.

The table can be saved as a CSV file for analysis in other software.

::::::::::::::::::::::::::::::::::::: callout

## Measurements Depend On The ROI

Fiji only measures pixels contained within the selected ROI.

Different ROI shapes or sizes may produce different results.

Always consider whether the selected ROI accurately represents the biological
structure you wish to measure.

::::::::::::::::::::::::::::::::::::::::::::::::

## Discussion

Manual measurements are useful for understanding how image-analysis workflows
operate.

However, manually measuring hundreds or thousands of structures quickly becomes
impractical.

In later episodes we will learn how to:

- automatically identify objects
- segment biological structures
- measure large numbers of objects
- generate reproducible analysis workflows

The principles remain the same, but Fiji will perform the work automatically.

## Looking Ahead

In the next episode we will explore image preprocessing.

We will learn how image-processing operations can improve image quality and
prepare data for segmentation and quantitative analysis.

## Key Points

::::::::::::::::::::::::::::::::::::: keypoints

- Regions of Interest (ROIs) define the pixels that will be measured.
- Fiji can measure object size, intensity, shape, and distance.
- Measurement settings determine which quantities are recorded.
- The ROI Manager can store and organise multiple ROIs.
- The Results table stores measurement outputs.
- Measurements should be interpreted in the context of image calibration.
- Manual measurements provide the foundation for automated image analysis.

::::::::::::::::::::::::::::::::::::::::::::::::
``
