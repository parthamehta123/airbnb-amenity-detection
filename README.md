# Replicating Airbnb's Amenity Detection with Detectron2 👁 🛏

This repository contains all the code from a project https://www.notion.so/Replicating-Airbnb-s-Object-Detection-Pipeline-Project-27e6744573034e7d99e0edd45f2e4add to replicate Airbnb's amenity detection using [Detectron2](https://github.com/facebookresearch/detectron2).

![example of how amenities might be detected in an image](https://raw.githubusercontent.com/parthamehta123/airbnb-amenity-detection/master/custom_images/airbnb-amenity-detection-workflow-large.png)

Sample image taken from: https://www.airbnb.com/rooms/2151100

**What's amenity detection?**

Object detection but for common and useful household items someone looking for an Airbnb rental might want to know about. For example, does this home have a fireplace?

Original inspiration was drawn from the article [Amenity Detection and Beyond — New Frontiers of Computer Vision at Airbnb](https://medium.com/airbnb-engineering/amenity-detection-and-beyond-new-frontiers-of-computer-vision-at-airbnb-144a4441b72e).

## Try it for yourself

To see the major pieces of the puzzle (data downloading, preprocessing, modelling), check out the [example Colab Notebook](https://colab.research.google.com/drive/1gQ8Z2UXYiyQWg7LhfsBuvfO01qLT4eOe).

You can also see a [live and deployed app which uses the model](https://airbnb-amenity-detection.appspot.com/) (note: this may have been taken down by the time you check it due to costs, an extension would be finding a way to deply the model for little to no costs).

## What's in this repo?

* Notebooks with 00-10 are all the steps I took to train the full model, largely unchanged from when I originally wrote them.
  * For a cleaned up version, see the [example Colab Notebook](https://colab.research.google.com/drive/1gQ8Z2UXYiyQWg7LhfsBuvfO01qLT4eOe).
* `preprocessing.py` contains the preprocessing functions for turning [Open Images images & labels](https://storage.googleapis.com/openimages/web/index.html) into [Detectron2 style](https://detectron2.readthedocs.io/tutorials/datasets.html).
* `downloadOI.py` is a slightly modified downloader script from [LearnOpenCV](https://www.learnopencv.com/fast-image-downloader-for-open-images-v4/) which downloads only certain classes of images from Open Images, example:

```
# Download only images from the Kitchen & dining room table class from Open Images validation set
!python3 downloadOI.py --dataset "validation" --classes "Kitchen & dining room table"
```
* `app` contains a Python script with a [Streamlit](https://www.streamlit.io) app built around the model, if you can see the live version, Streamlit is what I used to build it.
* `custom_images` contains a series of different images related to the project, including various rooms around my house to test the model.
