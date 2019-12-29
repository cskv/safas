# safas
**s**edimentation **a**nd **f**loc **a**nalysis **s**oftware

A Python module for processing and interpretation of images and videos of flocs, a.k.a. aggregates, a.k.a. cohesive sediments.

## Overview
This package permits the direct analysis of images and videos of flocs. Size, morphology and settling rate information may be captured and saved in an easily accessible format. Several features of this package are documented in Jupyter notebooks in the notebooks directory, including how to use the filters and visualizing the results.

The main modules are:

* **gui** and **trackpanel** contain components for visualization, image processing control, and object selection.

* **track** contains classes and scripts that permit manual or semi-automated labelling of flocs in a time series of images.

* **filter** contains a set of scripts that were developed for the special case of segmenting and extracting flocs from images and video.

## Why Safas?
**Safas** is written in Python. It is open-source and the image filters are acessible and extensible. The image filters use functions from  and were designed and tested for segmenting and quantifying images of flocs.

**Safas** has several features that make if useful for the analysis of floc images and video:
* **"One-step" analysis.** The user can open a video file and directly process the frames. The results may exported to an .xlsx file in tabular format for analysis or reporting.

* **Optimized floc filters.** Image analysis can be challenging and each image class often requires a different treatment. The pre-defined filters are built on OpenCV and Scikit-Image and have been designed to work well with images of flocs.

* **GPU-enabled.** Several filters in safas are GPU-enabled, through OpenCV with OpenCL, if the software environment is configured correctly during installation.

### Setup with Conda package manager
Setup from the environment file with Conda will create an environment called safas_env:
```shell
conda env create -f environment.yml
```
Activate the environment:
``` shell
conda activate safas_env
```

``` shell
python setup.py install
```

### Use



### GPU-enabled OpenCV in Windows
OpenCV4 was used during development. For Windows, this is one way to install GPU-enabled OpenCV:

1. Confirm whether any previous installation of OpenCV is OpenCL-enabled. In a Python shell:
``` shell
import cv2
cv2.ocl.useOpenCL()
```
2. If Step 1. was False, then remove the existing OpenCV installation and proceed to install the pre-comiled OpenCV executable from Source Forge.
3. Download the [precompiled OpenCV binary for windows:](https://sourceforge.net/projects/opencvlibrary/files/opencv-win/).
4. Click: "Download Latest Version" (opencv-4.1.2-vc14_vc15.exe), then extract the package.
4. Activate your conda environment
3. Setup the environmental variables. Run 'opencv/build/setup_vars_opencv4.cmd' in the command prompt to update the path variables that will enable your Python executable to find OpenCV.
4. Copy the OpenCV .pyd file from 'opencv\build\python\cv2\python-3.6\cv2.cp36-win_amd64.pyd' to the directory of your Python executable. For example, with a Conda Python 3.6 environment called 'safas_env', move the file to '\Miniconda3\envs\safas_env.'
5. Check that you can import OpenCV and that it is OpenCL-enabled, as in Step 1.