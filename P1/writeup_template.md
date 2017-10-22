# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe of the pipeline.

My pipeline consistes of 5 steps. 

First, I converted the images to grayscale, then I use Gaussian Blur, ROI limitation and Canny Edge Detection to detect the edges.

Then, a Hough transformation is used to identify the lines in the edge image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by adding another filter function to filter the lines:
(1) Eliminate the lines according the slopes of the lines 
(2) Judge whether the lines are left lanes or right lanes according the (x,y) position in the image and the slopes of lines
(3) Merge all left lines into a "Main Left Lane".  Merge all right lines into a "Main right Lane".

### 2. Potential shortcomings


One potential shortcoming would be what would happen when the resolutions of the images changed, the code cannot get a correct ROI. So the Hough function will return many noise lines which will affect the result.

Another shortcoming could be incapability of curves.


### 3. Suggest possible improvements

A possible improvement would be to replace the identification of long lines to identification of short lines because the curve consists of many lines.

Another potential improvement could be using CNN to identify the lanes.
