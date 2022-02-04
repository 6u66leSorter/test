# Application for detecting oil slicks on images #
The analysis process is divided into several stages:
1. Highlight black color in the picture
>This happens by applying a color filter to the frame in a given range (min_p, max_p)
2. Splitting the filtered image into squares 
>The size of the squares can be changed. By default it is 0.063 of the image width
3. Searching for oil in squares 
>Comparing the number of black pixels and a given number (total number of pixels in a square multiplied by a certain factor, default 0.03)
4. Determining the result and coloring the marked squares if necessary
>After searching for oil squares, we get a list of numbers. If it is not empty, then there is oil.
