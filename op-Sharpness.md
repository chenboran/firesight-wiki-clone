# Determine 'sharpness' of an image
Experiments to determine the 'sharpness' of an input image using various methods.

## Methods
* GRAS - Absolute squared gradient

F = \dfrac{1}{nx \cdot ny} \sum_x \sum_y | I_{x,y} - I_{x+1,y} | ^2

![methods](focus/sharpness_methods.png)
![speed](focus/duration.png)