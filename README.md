**Homework for Machine Learning for Computer Vision**

Consider a picture representing a white sheet of A4 paper with some handwritten numbers in a dark color (they have different sizes, but they are all oriented in the same direction, which is aligned with one of the edges of the paper). Consider the attached pictures as examples. Some are easy, others are harder. Note that the paper might be pictured at an angle or from a slanted perspective. In all pictures the four edges of the paper are clearly visible, but might be incomplete. Write a notebook that, given a directory, will process all images in that directory and extract all digits it can find from each picture. For each file, it should then print: 
- the name of the file, followed by
- each of the digits that has been identified on that sheet of paper, from top to bottom.


**Suggested approach**

- Load the image and resize it to a manageable size. You may want to convert it to grayscale.
- Look for edges using the Canny edge detector.
- Look for four long straight lines using the Hough line detector.
- The intersections between pairs of these lines should correspond to the corners of the paper sheet. (note: 4 lines define 6 different intersections!)
- Once you have the four corners of the sheet, you can obtain a straightened version of your sheet of paper, by a geometric transformation.
- Binarize and find connected components (this might be tricky when illumination is uneven. How to fix that?).
- Cut a square bounding box around each connected component.
- Resize that to a 28x28 and classify it using a convnet trained on the MNIST dataset.
