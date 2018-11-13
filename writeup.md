# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[color_select]: ./writeup_images/imageCs.jpg "color_select"
[grayscale]: ./writeup_images/imageGray.jpg "grayscale"
[blur]: ./writeup_images/imageBlur.jpg "blur"
[edges]: ./writeup_images/imageEdges.jpg "edges"
[masked]: ./writeup_images/imageMasked.jpg "masked"
[overlay]: ./writeup_images/imageOverlay.jpg "overlay"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 7 steps. First, I combined a white and a yellow color mask to extract white and yellow objects in the image. Then I converted to grayscale, applied gaussian smoothing, used Canny edge detection and applied a region of interest mask. Then I used the Hough function to extract lines and overlayed the result on the original image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by increasing the thickness to 7 pixels, separating left and right lane lines into two slope ranges, dismissing all the "noisy" lines that wouldn't fit into either range, using the numpy polyfit function to determine linear function parameters for the average left and right lines and extrapolating a line from the bottom of the image to the top of the region of interest for each side.

![color_select][color_select]
![grayscale][grayscale]
![blur][blur]
![edges][edges]
![masked][masked]
![overlay][overlay]


### 2. Identify potential shortcomings with your current pipeline

One potential shortcoming would be any situation that would cause the slope of the lane lines to change:
* if the camera is moved to a different position on the car, or to a different angle
* during a lane change
* going uphill or downhill
* for a wider or narrower road

Another shortcoming could be if the color hue of the lane lines changes due to a change in ambient light.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use a moving average filter for the line parameters to make things look a bit smoother.

Another potential improvement could be to use a wider range of white and yellow tones to account for the different hues depending on daylight and weather.

Moreover it would be helpful to have a wider slope range for uphill and downhill rides or wider or narrower roads.
