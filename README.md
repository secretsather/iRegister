# Image Registration: easy manual alignment of images for GAN datasets

A simple tool to aid in the manual processing of large image datasets, to pad, resize, and align images.

![cats aligned](/examples/cats/aligned.png)

## Description

iRegister was created to allow the user to manually process large image datasets, padding to create square images, resizing, and aligning images based on selected points from within the images. It was designed to do these tasks, and these tasks only, making highly efficient the use of the users time. The user can process approximately 400 images every 15 minutes using this method. 

## Getting Started

### Dependencies

* Numpy
* Copy
* Cv2
* Jupyter notebook or similar platform compatible with CV2's imshow() method

### Installing

```
git clone https://github.com/secretsather/iRegister
```

* to a path within your jupyter startup folder

### Executing program

The first cell in the notebook defines 2 folders, *picsPath* & *resultPath*, and 1 image file, *modelImage*. *picsPath* points to a folder location containing the images you would like to align, while *resultPath* is the folder location where the images will be saved after processing. *modelImage* shall point to a pre-processed image, which should be a perfect representation (crop, rotation) to which you're trying to match the other images. 

There are 2 size definitions in the first cell, *workingSize* & *imgSize*. *imgSize* is the final output size (square image) you want the processed images to be scaled to. *workingSize* is the size of the image as it will load on your screen. While it will become evident upon use, the *workingSize* is recommended to be as large as possible, without extending past the smallest dimension of your screen/monitor. Using a small *workingSize* will result in low quality output due to the downsizing then upsizing of this process.

Run the first two cells. The 3rd cell, upon execution, will open a screen via CV2 with your model image loaded to the *workingSize*. The user is to select 2 points on the model to which they would like to match all subsequent points from all subsequent images. Upon selecting these points, a "0" and "1" will be overlayed on the image. The "0" and "1" text will be slightly shifted to the top and right of the selected point. If a wrong point is made, the chosen points may be cleared by clicking the right mouse button over the image. This will allow the user to select two new points. Once the points are selected and satisfactory, pressing any key on the keyboard will load the first image from within the *picsPath* folder and begin the process of alignment. A screenshot of this process has been provided below. 

![Screencap](/examples/cats/screenshot.png)

When processing the dataset images, selecting the two same points on the object within the image will align that object to the exact coordinates that were selected on the model image. This is done via a similary tranform, using rotation, scale, and translation. The transformed image is saved to the *resultPath* location before loading the next image. The interface to the dataset images works identically to the model images, selecting 2 points with the left mouse button, clearing all points with the right mouse button, and advancing to the next image with any key press on the keyboard. 

If no selections are made on the images, or if the selections are cleared prior to advancing to the next image, the image is not processed and will not appear in the *resultPath* folder. This allows the user to additionally use this as a filter, in the event there are images he/she does not want to appear or are not suitable for the final processed dataset. 

Examples of inputs & results are shown below: 

INPUT

![](/examples/cats/unaligned.png)

RESULT

![](/examples/cats/aligned.png)

INPUT

![](/examples/triangles/unaligned.png)

RESULT

![](/examples/triangles/aligned.png)

Moreover, the user may select points that allow any rotation, and may select multiple objects from a single image as shown in the example below: 

INPUT

![](/examples/crayons/unaligned.png)

RESULTS

![](/examples/crayons/aligned.png)

![](/examples/crayons/Animation.gif)

## How it works

The script works by first padding the image to make it square. It then resizes the square image to the *workingSize*, as defined in the first cell of the notebook. After point selections are made, this makes use of CV2's *estimateAffinePartial2D()* and *warpAffine()* methods, although this is not an affine transformation. Modification of the code could allow the user to implement an affine transformation, though that would have the consequence of shearing the image, and is not suitable for most applications.

After the transformation is performed, the image is then resized to the final *imgSize*. As recommended previously, the *workingSize* should be greater than the *imgSize* but less than the size of your screen in pixels. This allows the final output image to retain higher quality in the event the image is "zoomed-in" significantly to meet the requirements of the point selection/transformation. (e.g. the model image is a closeup of a cat and the transformation image from the dataset is at a far disntace) 

## Authors

George Gardner

## Version History

* 0.3 Working stable

## License

This project is licensed under the MIT License - see the LICENSE file for details.
