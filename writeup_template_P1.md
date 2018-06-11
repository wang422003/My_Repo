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

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I set the thresholds for Canny and applied the Canny transition. After that  I used the gaussian function to blur the image and ignore the noise. Before I did the Hough transform, I set the mask of the image, so that the unimportant objects such as the other vehicles were ignored. After properly set the values for Hough Transform(which was not easy because I tried again and agian :<) and the extrapolation, I got the videos as required.
In order to draw a single line on the left and right lanes, I modified the draw_lines() function by built a new function named 'extrapolate_lines'. This function got the result of the Hough Transform which was a group of (x,y). The function then calculated the slope between any pair of the points of Hough Transform. At the same time, the output slope was accumulated by the weighted slope acoording to the length between the points. After set the height of the lines, the position of the starting and ending points of the two lines would be output.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![solidwhitecurve](https://user-images.githubusercontent.com/40182472/41254891-2145d9fc-6dc5-11e8-9161-6bf534487b30.png)
![solidwhiteright](https://user-images.githubusercontent.com/40182472/41254906-2c47dcb0-6dc5-11e8-82ae-688a28c1e16e.png)
![solidyellowcurve](https://user-images.githubusercontent.com/40182472/41254908-2e0fa168-6dc5-11e8-8072-caba8389f63e.png)
![solidyellowcurve2](https://user-images.githubusercontent.com/40182472/41254911-2f68cf3a-6dc5-11e8-8bb2-920ecbf090a1.png)
![solidyellowleft](https://user-images.githubusercontent.com/40182472/41254914-30e59654-6dc5-11e8-8749-d50ac7abbc28.png)
![whitecarlaneswitch](https://user-images.githubusercontent.com/40182472/41254915-32659c7c-6dc5-11e8-8ab0-bee0da0633df.png)



### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when it comes to a curve or the distance between the vehicle and the fornt vehicle is too small. 

Another shortcoming could be if the road is under construction and there is a edge between the present lane and the other lane, the edge might be seen as line on the lane.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to adding different kinds of library of the traffic lines such as color and width, so that the pipeline can detect the proper line according to the library.

Another potential improvement could be to extrapolate the Hough Transform using curves, which makes it safer when the vehicles run in curve.
