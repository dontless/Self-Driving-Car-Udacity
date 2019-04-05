# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

### Finding Lane Lines on the Road**

The goals / steps of this project are the following:-

 ### Lane lines detecting pipeline consists of the following steps:
 
1.we need to import the cv2 module, which will make available the functionalities needed to read the original image and to convert it to gray scale.
2.apply Gaussian blur filter to the grayscaled image in order to suppress noise and spurious gradients by averaging;
3.apply Canny edge detection to determine edges on the picture;
4.define a region of interest and make anything else black;
5.detect lines in the region of interest using Hough transformation;
6.prepare a black image on which lane lines will be drawn;
7.draw lines following the approach described below:-
8.combine initial image with lane lines image to get the final result.
   

[//test_images/solidWhiteRight.jpg]: # (Image References)

[oads\submit-a7a46b1f-3b31-4c05-aef7-8b57a502a3a6\home\CarND-LaneLines-P1\gray_image]: ./examples/grayscale.jpg "Grayscale"

---

 
### draw_lines() function

To get lines begining from the bottom of the image, the least squares algorithm was applied to the input set of points that define beginings and ends of the lines (output of Hough transformation). That was enough to correctly process all images and first videos. There was a problem with the last video called challenge.mp4. There were a lot of edges detected by Canny algorithm so that it was needed to adjust threshould parameters. That was not enough however, there was a need not to react immediately on substantial changes of the lines' positions. Function was modified to be aware of previous positions of lines and in case of substantial line's position change, change coordinates by a small fraction of the actually "requested" change. The last modification helped to "stabilize" lane lines in the challenge.mp4 video.



### Reflection

## Shortcommings

image processing could be faster;
lane lines detecting might be over-stabilized, i.e. will react only on a huge changes in the line's slope; there is no confidence that it will succeed in cases with a lot of sharp turns; but it should be checked first.

## Improvements

Author was not fammiliar with numpy python library. Some calculations were done using pure python where vectorized operations provided by aforementioned library could be applied instead. Author believes that the usage of vectorized operations will slighlty descrease a processing time.
For the roads with turns there is a need to detect curves, not just lane lines. May be it will be enough just to split each line (left and right) to two lines and then sharp turns may be handled better.

### Resulting Images

Few examples of images with detected lane lines: alt text alt text

[\\home\CarND-LaneLines-P1\test_images\\solidWhiteCurve.jpg]

[\\home\CarND-LaneLines-P1\test_images\\solidYellowCurve2.jpg]

[\\home\CarND-LaneLines-P1\test_images\\solidCarLaneSwitch.jpg]

[\\home\CarND-LaneLines-P1\test_images\\solidWhiteRight.jpg]

[\\home\CarND-LaneLines-P1\test_images\\solidYellowCuurve.jpg]

[\\home\CarND-LaneLines-P1\test_images\\solidYellowLeft.jpg]

 
