# **Finding Lane Lines on the Road** 

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Pipline should work on photos and videos


[//]: # (Image References)

[image]: ./test_images/solidWhiteCurve.jpg "Original image"
[image1]: ./steps/gray_solidWhiteCurve.jpg "Grayscale"
[image2]: ./steps/blur_gray_solidWhiteCurve.jpg "Blured"
[image3]: ./steps/edges_solidWhiteCurve.jpg "Canny"
[image4]: ./steps/masked_edges_solidWhiteCurve.jpg "Masked"
[image5]: ./steps/lines_solidWhiteCurve.jpg "Lines"
[final]: ./test_images_output/result_solidWhiteCurve.jpg "Final"

---

### Reflection

### 1. Steps taken for pipelining lane lines on the Road

My pipeline consisted of 5 steps.
1. Converted the images to grayscale
2. Used Gaussian filter for image smooting
3. Filtered edges using Canny over smoothed image
4. Set region of interested(using polygon) and "color" edges
5. Process lines only image with Hough Lines formula

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by increasing thicknes from 1 to 7.

For connecting lines I used 150 pixel as maximum gap line between connectable line segments.

For polygon area, I didn't used fixed numbers, but a little bit of math, so I tried to resize photos and got (almost) the same result.

Here are 5 steps of processing image example: 

#### Original
![alt text][image]

#### 1. Grayscale
![alt text][image1]

#### 2. Blured
![alt text][image2]

#### 3. Canny
![alt text][image3]

#### 4. Masked
![alt text][image4]

#### 5. Lines
![alt text][image5]

#### Final
![alt text][final]

### 2. Identify potential shortcomings with your current pipeline

Main shortcomings is sometimes lines break, and it's not fixable by increasing "maximum gap line"

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to create a simple photo video editor with parameters like "opencv-gui-parameter-tuner" where you can see all step changes on the fly

### Challenge

Changed a pipeline a bit, before "grayscaling" image, I filtered yellow and white colors from image, and removed "canny" from pipeline
Also I have increased max line gap up to 300.
Polygon shape has been a bit modified so front part of car is not inside a polygon.

### Result (Video)

#### Challenge [video](https://github.com/Horki/CarND-LaneLines-P1/blob/master/test_videos_output/challenge.mp4), [YouTube Video](https://youtu.be/DK-ZuadfIY0) (sample)
<img src="samples/challenge.gif"/>

#### Solid White Right [video](https://github.com/Horki/CarND-LaneLines-P1/blob/master/test_videos_output/solidWhiteRight.mp4) (sample)
<img src="samples/solidWhiteRight.gif"/>

#### Solid Yellow Left [video](https://github.com/Horki/CarND-LaneLines-P1/blob/master/test_videos_output/solidYellowLeft.mp4) (sample)
<img src="samples/solidYellowLeft.gif"/>
