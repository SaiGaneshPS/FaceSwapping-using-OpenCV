# FaceSwapping-using-OpenCV

The following program is used to take a face from one image and apply it as a mask over another image. Initially all the steps done to swap the faces are shown. In the end, a function is built that can be used to swap faces when the images are given as input. 

The function follows the same steps as mentioned bellow :

* Step 1 : Read the images and convert to grayscale
  
  The first step is to read the two images that will have the faces swapped. This is done using "cv2.imread" and the images are converted to their grayscale version and   stored in another variable
  
* Step 2 : Get the landmark points for the faces

  Load the frontal face detector to detect faces as well as the predictor to find the shape of the face or the outline of the face both from the dlib library.
  
* Step 3 : Convert the faces into delaunay triangles using the landmark points
  
  In this step, the face is segmented into triangles so that in only these triangles can be exchanged between the images. This is done using the delaunay                 triangulation.

  _Why this step is important?_ :worried:

  The face cant be just replaced on the whole because they might have different size and perspective. When we split the face into triangles, only these triangles can     be swapped and this way the original proportions are not lost.

* Step 4 : Match the dimensions of the triangles by warping
  
  The triangles of the first face are taken and distorted to the triangles of the second image so that the dimensions of the face matches. This will make sure that the   images retain their facial features.
  
* Step 5 : Swap the face masks generated to form the resulting image
  
  This step is simple, the face masks generated by the above step are swapped and the result image is formed. But, the colors and saturation of the edges are very       different.
  
* Step 6 : Use the seamlessClone function to match the outlines clearly

  To solve the discolouration, the edges are smoothed to make the masks look the same, this is done using the seamlessClone function of the OpenCV. The attribute         MIXED_CLONE gives better output in some cases, but most of the times NORMAL_CLONE gives a valid output.
  

## Sample Input :
 
 Input Number 1 :
 
 ![image](https://user-images.githubusercontent.com/60283852/165671442-cbcaad0a-6163-43ff-94b3-afa402b30428.png?style=centerme)

 Input Number 2 :
 
 ![image](https://user-images.githubusercontent.com/60283852/165671479-150ad86b-f52f-4b72-a7fd-e05fb4bde9da.png)

 Final image :
 
 ![image](https://user-images.githubusercontent.com/60283852/165671507-9697276e-b204-4d8f-9fc1-8c252affaa47.png)
