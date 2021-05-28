# **Finding Lane Lines on the Road** 

## Lawrance Towsen

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

### 1. My pipeline and draw_lines() function

My pipeline consists of 5 steps.  After copying the image I run it through a grayscale filter before blurring the image using a 
guassian blur.  Now that the image is prepped I run canny edge detection on it and then run the image through a mask to keep only the 
section with lane lines.  As the final step I have a hough transform to detect the lines and allow me to draw them onto the image.  

The draw_lines function works by first seperating the lines into left or right lane lines.  It does this by checking their gradient and location 
on the screen.  The next step is to run a linear regression on the respective lane lines to get the function of the left and right lane line.  Once that is done I calculate the start and end points of the two lane lines using the y-intercept, slope received from the linear regression algorithm and picking x points based on the rough location of the lane lines for the calculation.  Once the start and end points are calculated for both lanes they are then drawn onto the image. 

### 2. Potential shortcomings with my current pipeline
* Not being able to detect curving lane lines.  
* Requiring an estimate for lane line positions(selecting x coordinates for start and end point calculations).

### 3. Possible improvements to my pipeline
*  Using a quadratic function in the hough transfrom instead of a linear one to allow for curved lines
*  The image could be run through more filters before processing to further account for light conditions
*  A history of previous lane lines could be stored to help smooth out transition between frames as the lane lines are currently very jumpy
