---
title: "Setup"
---

# Setup

Before attending this workshop, you will need to install Fiji and download the lesson data.

## Learning Objectives

By completing this setup, you will be able to:

- Install Fiji on your computer.
- Launch Fiji successfully.
- Verify that Fiji is working correctly.
- Download and organise the lesson data.

## Software Requirements

For this workshop, we will use the **Stable** release of Fiji to ensure that all learners are working with the same software version.

## Download Fiji

1. Navigate to:

   <https://fiji.sc>

2. Locate the **Stable Downloads** button and press it.

3. Download the version appropriate for your operating system.

## Install Fiji

::: tab

### Windows

1. Download: `fiji-stable-win64-jdk.zip`

2. Extract the ZIP archive.

3. A folder called `Fiji` will be created.

4. Move the `Fiji` folder to a suitable location.

   We recommend:  `C:\Users\<your-username>\Fiji`

5. Do **not** install Fiji in:

   `C:\Program Files`

   Installing Fiji in your home directory avoids permission issues when updating Fiji or installing plugins.

6. Open the `Fiji` folder.

7. Launch Fiji by double-clicking:  `fiji-windows-x64.exe`

### macOS

1. Download:   `fiji-stable-macosx-jdk.zip`

2. Extract the ZIP archive.

3. Open the extracted `Fiji` folder.

4. Move: `Fiji.app` folder to your **Applications** folder.

5. Launch Fiji from the Applications folder.

6. The first time you launch Fiji, macOS *may* display a security warning 
   because the application was downloaded from the internet.

   If this happens:

   - Open **System Settings**
   - Select **Privacy & Security**
   - Click **Open Anyway**
   - Launch Fiji again


### Linux

1. Download:  `fiji-stable-linux64-jdk.zip`

2. Extract the ZIP archive.

3. A folder called: `Fiji` will be created.

4. Move the folder to a suitable location, for example: `~/Fiji`

5. Open a terminal.

6. Navigate to the Fiji directory:  `cd ~/Fiji`

7. Launch Fiji:   `./ImageJ-linux64`

:::

## Test Your Installation

To confirm that Fiji is installed correctly:

1. Start Fiji.
2. Select **File → Open Samples → Blobs**.
3. A sample image should open.
4. Select **Image → Properties**.

You should see information describing the image dimensions and pixel size.

If you can open the sample image and view its properties, Fiji is working correctly.

## Download the Lesson Data

Download the lesson data archive from the link provided by your instructor and extract it into a dedicated workshop folder.

We recommend the following directory structure:

```text
bioimage-analysis-using-fiji/
|
├── data/
├── macros/
└── results/
```

The lesson images will be stored in the `data` directory, any provided macros in the `macros` directory, and analysis outputs in the `results` directory.

## Updating Fiji

Fiji includes a built-in updater that can install bug fixes and plugin updates.

Before you come to the workshop, pleaes update Fiji:

1. Start Fiji. The updater may run at startup by default, if not:
2. Select **Help → Update...** - *NOT* **→ Update ImageJ...**
3. Click **Apply Changes** if updates are available.
4. Restart Fiji when prompted.

> We recommend **updating Fiji before the workshop**. Updating beforehand is fine, updating during the workshop can cause delays.

## Setup Checklist

Before the workshop starts, make sure you can:

- [ ] Launch Fiji.
- [ ] Open the sample **Blobs** image.
- [ ] View the image properties.
- [ ] Locate your lesson data folder.

If all four items are complete, you are ready to begin the lesson.

