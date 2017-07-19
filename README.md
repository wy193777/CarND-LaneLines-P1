# **Finding Lane Lines on the Road**


---

[//]: # (Image References)

[image1]: /home/shenghan/CarND-LaneLines-P1/test_images_output/solidWhiteCurve.png "Two Line"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps:

1. Convert the original image to grayscale image.
2. Convert the grayscale image to edge image using canny's method
3. Set regions that aren't so interesting to black.
4. Extract lane line using Hough's method.
5. Combine lines extracted by Hough's method to one left lane and one right lane.
6. Draw two lanes on original image.


 Group lines extracted by Hough's method by their slope. Lines with negative slope as left lanes and with positive slope as right lane.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by grouping lines extracted by Hough's method by their slopes. Lines with negative slope as left lanes and with positive slope as right lane. Then using 1 dimensional fitting to fit two lines from two groups.

Here is the output of one image.
![two lines][image1]


### 2. Identify potential shortcomings with your current pipeline


The result is highly depend on light, shadow and the position of camera. That is to say, in different light condition, you might have to use different sets of parameters. If there are lots of shadows on the road like the challenge video, it's pretty hard to have a robust result. So the pipeline is pretty hard to scale out.




### 3. Suggest possible improvements to your pipeline

Experiment more on parameters line kernel size and those parameters related to Hough's method.

Use some time based filters that could average lanes over time to prevent glitches. 

I see there is a project called Advanced Lane Finding. So I guess this highly depend on parameters solution might not be suitable in real self driving cars.
