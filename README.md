# Image Registration: easy manual alignment of images for GAN datasets

A simple tool to aid in the manual processing of large image datasets, to pad, resize, and align images.

## Description

iRegister was created to allow the user to manually process large image datasets, padding to create square images, resizing, and aligning images based on selected points from within the images. It was designed to do these tasks, and these tasks only, making highly efficient the use of the users time. The user can process approximately 400 images every 15 minutes using this method. 

## Getting Started

### Dependencies

* Numpy
* Copy
* Cv2
* Jupyter notebook or similar platform compatible with CV2's imshow() method

### Installing

* git clone https://github.com/secretsather/iRegister to a path within your jupyter startup folder

### Executing program

The first cell in the notebook defines 2 folders, *picsPath* & *resultPath*, and 1 image file, *modelImage*. *picsPath* points to a folder location containing the images you would like to align, while *resultPath* is the folder location where the images will be saved after processing. *modelImage* shall point to a pre-processed image, which should be a perfect representation (crop, rotation) of what you are trying to match the other images to. 

There are 2 size definitions in the first cell, *workingSize* & *imgSize*. *imgSize* is the final output size (square image) you want the processed images to be scaled to. *workingSize* is the size of the image as it will load on your screen. While it will become evident upon use, the *workingSize* is recommended to be as large as possible, without extending past the smallest dimension of your screen/monitor. Using a small *workingSize* will result in low quality output due to the downsizing then upsizing of this process.

Run the first two cells. The 3rd cell, upon execution, will open a screen via CV2 with your model image loaded to the *workingSize*. The user is to select 2 points on the model to which they would like to match all subsequent points from all subsequent images. Upon selecting these points, a "0" and "1" will be overlayed on the image. The "0" and "1" text will be slightly shifted to the top and right of the selected point. If a wrong point is made, the chosen points may be cleared by clicking the right mouse button over the image. This will allow the user to select two new points. Once the points are selected and satisfactory, pressing any key on the keyboard will load the first image from withing the *picsPath* folder and begin the process of alignment. 

![Screencap](/examples/cats/screenshot.png)

```
code blocks for commands
```

## Help

Any advise for common problems or issues.
```
command to run if program contains helper info
```

## Authors

Contributors names and contact info

ex. Dominique Pizzie  
ex. [@DomPizzie](https://twitter.com/dompizzie)

## Version History

* 0.2
    * Various bug fixes and optimizations
    * See [commit change]() or See [release history]()
* 0.1
    * Initial Release

## License

This project is licensed under the [NAME HERE] License - see the LICENSE.md file for details

## Acknowledgments

Inspiration, code snippets, etc.
* [awesome-readme](https://github.com/matiassingers/awesome-readme)
* [PurpleBooth](https://gist.github.com/PurpleBooth/109311bb0361f32d87a2)
* [dbader](https://github.com/dbader/readme-template)
* [zenorocha](https://gist.github.com/zenorocha/4526327)
* [fvcproductions](https://gist.github.com/fvcproductions/1bfc2d4aecb01a834b46)
