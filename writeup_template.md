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

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps described below. 

1. Update image to filter yellow and white lane markings.

2. I converted the images from RGB to grayscale. 

3. Applied Gaussian blur. Canny edge detection which is next step will also apply Gaussian blur internally. Applied additional time to make the output better.

4. Performed Canny edge detection.

5. Idenitfy the region of interest which is the area in front of the Ego vehicle and filter the unwanted portions of the image.

6. Perform Hough transformation and generate Hough lines.

7. Multiple lines are detected for a lane line so find a avarage line for the same.

8. Some lane lines are recognized partially. So extrapolate the line to cover full lane line length.

9. Lay the lanes on top of original image. These are the lines that are retrived in previous step.

10. Darw the lanes.

11. Repeat the above steps for each clip from each of the video that needs lanes identified. 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function  

1. Use slope to identify left and right lane segements.

2. Left lane segements going to have slope between small negative number and zero.

3. Right lane segements going to have slope between zero and small positive number.

4. To come up with avarage line for multiple lines that are detected.

5. Extrapolate and draw full lane line For the lines that are detected partially.

### 2. Identify potential shortcomings with your current pipeline

Solution is not working well for challanging scenario and might work for some other complex scenarios like wet road, snow covered roads and roads with lane markings that got fade out.

### 3. Suggest possible improvements to your pipeline

Improve the solutions to make it work challanging and other complex scenarios.
