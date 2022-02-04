# Application for detecting oil slicks on images #
The analysis process is divided into several stages
+ Highlight black color in the picture
+ Splitting the filtered image into squares (The size of the squares can be changed. By default it is 0.063 of the image width)
+ Searching for oil in squares by comparing the number of black pixels and a given number (total number of pixels in a square multiplied by a certain factor, default 0.03)
+ Determining the result and coloring the marked squares if necessary
