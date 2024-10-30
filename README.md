# Cartoonify-Image by using OpenCV with Python:

# Step 1: Importing the required modules
We will import the following modules:

CV2: Imported to use OpenCV for image processing
easygui: Imported to open a file box. It allows us to select any file from our system.
Numpy: Images are stored and processed as numbers. These are taken as arrays. We use NumPy to deal with arrays.
Imageio: Used to read the file which is chosen by file box using a path.
Matplotlib: This library is used for visualization and plotting. Thus, it is imported to form the plot of images.
OS: For OS interaction. Here, to read the path and save images to that path.

Code:

<img width="571" alt="image" src="https://github.com/user-attachments/assets/d4dd0952-e6fc-41c9-9dc6-e30936946d8c">

# Step 2: Building a File Box to choose a particular file
In this step, we will build the main window of our application, where the buttons, labels, and images will reside. We also give it a title by title() function.

Code:

<img width="564" alt="image" src="https://github.com/user-attachments/assets/5cb64c09-05cb-4814-bb7b-a7d11f754f9a">

# Step 3: Convert our image into a numpy array for storing the image
Now, just think, how will a program read an image? For a computer, everything is just numbers. Thus, in the below code, we will convert our image into a numpy array.

Code:

<img width="564" alt="image" src="https://github.com/user-attachments/assets/872c1669-c57c-46d2-8062-674f30f25bd8">

# Step 4: Transforming an image to grayscale
Code:

<img width="564" alt="image" src="https://github.com/user-attachments/assets/6f0b2a14-2ac8-4204-8ce9-641953a33076">


cvtColor(image, flag) is a method in cv2 which is used to transform an image into the colour-space mentioned as ‘flag’. Here, our first step is to convert the image into grayscale. Thus, we use the BGR2GRAY flag. This returns the image in grayscale. A grayscale image is stored as grayScaleImage.

After each transformation, we resize the resultant image using the resize() method in cv2 and display it using imshow() method. This is done to get more clear insights into every single transformation step.

# Step 5: Smoothening a grayscale image
Code:

<img width="564" alt="image" src="https://github.com/user-attachments/assets/9bf5d3e5-7055-4ae5-9ede-f9f78f99888a">

To smoothen an image, we simply apply a blur effect. This is done using medianBlur() function. Here, the center pixel is assigned a mean value of all the pixels which fall under the kernel. In turn, creating a blur effect.

# Step 6: Retrieving the edges of an image
Code:

<img width="564" alt="image" src="https://github.com/user-attachments/assets/0d33290a-48e3-427c-838d-ed917c8d6f16">

Cartoon effect has two specialties:

1.Highlighted Edges
2.Smooth colors
In this step, we will work on the first specialty. Here, we will try to retrieve the edges and highlight them. This is attained by the adaptive thresholding technique. The threshold value is the mean of the neighborhood pixel values area minus the constant C. C is a constant that is subtracted from the mean or weighted sum of the neighborhood pixels. Thresh_binary is the type of threshold applied, and the remaining parameters determine the block size.

# Step 7: Preparing a Mask Image
Code:

<img width="617" alt="image" src="https://github.com/user-attachments/assets/2ffb0671-9e46-4531-9079-7584d7f21901">

In the above code, we finally work on the second specialty. We prepare a lightened color image that we mask with edges at the end to produce a cartoon image. We use bilateralFilter which removes the noise. It can be taken as smoothening of an image to an extent.

The third parameter is the diameter of the pixel neighborhood, i.e, the number of pixels around a certain pixel which will determine its value. The fourth and Fifth parameter defines signmaColor and sigmaSpace. These parameters are used to give a sigma effect, i.e make an image look vicious and like water paint, removing the roughness in colors.

Yes, it’s similar to BEAUTIFY or AI effect in cameras of modern mobile phones.

# Step 8: Giving a Cartoon Effect
Code:

<img width="617" alt="image" src="https://github.com/user-attachments/assets/117e502f-c0e8-45fc-9e5c-a3e5d1bd3180">

So, let’s combine the two specialties. This will be done using MASKING. We perform bitwise and on two images to mask them. Remember, images are just numbers?

Yes, so that’s how we mask edged image on our “BEAUTIFY” image.

This finally CARTOONIFY our image!

# Step 9: Plotting all the transitions together
Code:

<img width="617" alt="image" src="https://github.com/user-attachments/assets/bd5f6d3c-f750-4e45-9d96-4b2ac78bb9e1">

To plot all the images, we first make a list of all the images. The list here is named “images” and contains all the resized images. Now, we create axes like subl=plots in a plot and display one-one images in each block on the axis using imshow() method.

plt.show() plots the whole plot at once after we plot on each subplot.

# Step 10: Functionally of save button
Code:

<img width="1093" alt="image" src="https://github.com/user-attachments/assets/0803e5d1-b1bd-4b45-87a4-f54885de8843">

Here, the idea is to save the resultant image. For this, we take the old path, and just change the tail (name of the old file) to a new name and store the cartoonified image with a new name in the same folder by appending the new name to the head part of the file.

For this, we extract the head part of the file path by os.path.dirname() method. Similarly, os.path.splitext(ImagePath)[1] is used to extract the extension of the file from the path.

Here, newName stores “Cartoonified_Image” as the name of a new file. os.path.join(path1, newName + extension) joins the head of path to the newname and extension. This forms the complete path for the new file.

imwrite() method of cv2 is used to save the file at the path mentioned. cv2.cvtColor(ReSized6, cv2.COLOR_RGB2BGR) is used to assure that no color get extracted or highlighted while we save our image. Thus, at last, the user is given confirmation that the image is saved with the name and path of the file.

# Step 11: Making the main window

<img width="777" alt="image" src="https://github.com/user-attachments/assets/40999168-82b7-4b25-a084-e49f5bf3a184">

# Step 12: Making the Cartoonify button in the main window

![image](https://github.com/user-attachments/assets/706c8e1c-70c8-44ed-9565-977c64199b73)

# Step 13: Main function to build the tkinter window

Final Output:
![image](https://github.com/user-attachments/assets/7efcb027-4e1b-4b94-8b88-607ba3f49c4b)


