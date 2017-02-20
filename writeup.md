#**Finding Lane Lines on the Road**

##Writeup Template

###You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)



---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps:

1. grayscale

     <img src="/examples/grayscale.png" white>
     
2. gaussian blur
3. canny edge
    
    <img src="/examples/canny-edge.png" white>
    
4. mask region of interest

    <img src="/examples/mask-region-canny.png" white>
    
5. overlay the lines on the input image



In order to draw a single line on the left and right lanes, I modified the draw_lines() function by separating right and left lines using slope (positive slope for left lines and negative slope for right lines). Then average the slope and center of all left lines (similarly right lines) and then extrapolating the line.

Here are the outputs of lane line videos:


1. White lane lines

    <img src="/white.gif" white>


2. Yellow lane line

    <img src="/yellow.gif" yellow>


3. Optional challenge

    <img src="/extra.gif" extra>



###2. Potential shortcomings with current pipeline

1. Intersections: intersections usually have no lane lines and this pipeline will run into trouble
2. Sharp turns: This pipeline may run into trouble when there are sharp turns
3. Snow, rain, night, shadows, no lane lines: Canny edge detection may fail due to lack in contrast gradient in these cases, hence failure of this pipeline.
4. Only detects one lane.




###3. Possible improvements to this pipeline

1. Use regression with quadratic or higher order terms in order to be able to fit the curves
2. Ability to predict lane lines on patches of road where there aren't any.
