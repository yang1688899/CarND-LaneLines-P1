# **Finding Lane Lines on the Road** 

## Writeup

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_image_result/solidWhiteCurve.jpg
[image2]: ./test_image_result/solidWhiteRight.jpg
[image3]: ./test_image_result/solidYellowCurve.jpg
[image4]: ./test_image_result/solidYellowCurve2.jpg
[image5]: ./test_image_result/solidYellowLeft.jpg
[image6]: ./test_image_result/whiteCarLaneSwitch.jpg

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. 

First, I load the image with mpimg.imread() and apply grayscale() method in the helper functions to transform it to a grayscale picture.

Second, apply the cv2.Canny(blur_gray, 30, 150) method to find the edge in the image. 

Third, creat a create a image mask and use this image mask to mask the region of interest(where the lanes lies). 

Forth, apply the cv2.HoughLinesP function the extra the lines in the image. The difficult part is to find the right parameters for this function. I have try many times to get the parameters that seems work, witch have been prove later to be not good while i apply it to the video. I have to spend tons of time to try all sort of the diffient combination of the parameters. 

Fifth, draw the lines of lane on the image. Since the given draw_line function just draw all the lines the HoughLinesP produce, dons't seem to suit my need. So I modify it to take all the lines as input, get rip of the lines that definely seems to be noise, calculate the average left and right line and draw them with a lot highter thickness.

After do all this above, I get the result images like this:

![alt text][image1]
![alt text][image2]
![alt text][image3]
![alt text][image4]
![alt text][image5]
![alt text][image6]


### 2. Identify potential shortcomings with your current pipeline


Fisrt, althought my pipline work well on the two test video, it doesn't work on the changle video.

Second, when I mask the region of interest, I have to pass the parameter to tell the computer where to look, which doesn't seem to be quite right.

Third, I have to manualy tune the parameters of the HoughLinesP function, which time consuming and the result dosen't seem to be good on all the condition.

Forth, the code I write for calculate the average left and right lines is total a mass.


### 3. Suggest possible improvements to your pipeline

If the pipline could auto_detect where the region of interesting is, it would seems to be lot more better. And I should write a function to auto_tune the paremeters of the HoughLinesP. Let the computer do all this nasty works is the whole point of programming anyway. And beautify my code bit more will be very helpful for those who read it, just dosen't have the time and means to do this yet.
