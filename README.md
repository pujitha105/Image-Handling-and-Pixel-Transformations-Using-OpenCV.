# Image-Handling-and-Pixel-Transformations-Using-OpenCV 

## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## Algorithm:
### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.  
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).  
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

## Program Developed By:
- Name: kolluru pujitha 
- Register Number: 212223240074

  ### Ex. No. 01

#### 1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.

import cv2
import numpy as np
import matplotlib.pyplot as plt
read_image=cv2.imread('Eagle_in_Flight.jpg')
# read the image as grayscale
gray_image=cv2.imread('Eagle_in_Flight.jpg',0)


#### 2. Print the image width, height & Channel.

print("Shape of grayscale image : ",gray_image.shape)
print("Size of grayscale image : ",read_image.size)


#### 3. Display the image using matplotlib imshow().

#Display Grayscale image
plt.imshow(gray_image, cmap="gray")
plt.title("Grayscale image")
plt.axis('off')
plt.show()


#### 4. Save the image as a PNG file using OpenCV imwrite().

#Save the image as png file using OpenCV imwrite()
cv2.imwrite('Eagle_in_Flight.jpg',read_image)


#### 5. Read the saved image above as a color image using cv2.cvtColor().

color_image=cv2.cvtColor(read_image,cv2.COLOR_BGR2RGB)


#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.

#Display the colour image using matplotlib imshow() & print the image with, height & channel
shape_img=color_image.shape
print("Shape of the color image : ",shape_img)
size_img=color_image.size
print("Size of the color image : ",size_img)
plt.imshow(color_image)
plt.title('Eagle in fight (RGB)')
plt.axis('on')
plt.show()


#### 7. Crop the image to extract any specific (Eagle alone) object from the image.

# Crop the size to extract any specific object from the image
crop_image=color_image[50:425,200:550]
plt.imshow(crop_image)
plt.title('Cropped image')
plt.axis('off')
plt.show()


#### 8. Resize the image up by a factor of 2x.

# Resize the image up by a factor of 2x
resized=cv2.resize(crop_image, None, fx=50, fy=50, interpolation=cv2.INTER_LINEAR)
resized.shape


#### 9. Flip the cropped/resized image horizontally.

# FLip the cropped/resize image horizontally
flip_horz=cv2.flip(crop_image,1)
plt.figure(figsize=[18,5])
plt.imshow(flip_horz)
plt.title('Horizontal')
plt.show()


#### 10. Read in the image ('Apollo-11-launch.jpg').

# Read in the image
apollo_img=cv2.imread('Apollo-11-launch.jpg')


#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):

# Add the text to the dark area
text = 'Apollo 11 Saturn V Launch, July 16, 1969'
font_face = cv2.FONT_HERSHEY_PLAIN
font_scale=2
color=(255,255,255)
thickness=2
cv2.putText(apollo_img,text,(30,50),font_face,font_scale,color,thickness,cv2.LINE_AA)
rgb_image=cv2.cvtColor(apollo_img,cv2.COLOR_BGR2RGB)
plt.imshow(rgb_image)
plt.axis('off')


#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.

x1,y1=50,50
x2,y2=400,600
rect_color=(255,0,255)
thickness=3
im=cv2.rectangle(apollo_img,(x1,y1),(x2,y2),rect_color,thickness)
img_rgb = cv2.cvtColor(im, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(12,6))
plt.imshow(img_rgb)
plt.axis("off")
plt.show()


#### 13. Display the final annotated image.

# Add the text to the dark area
text = 'Apollo 11 Saturn V Launch, July 16, 1969'
font_face = cv2.FONT_HERSHEY_PLAIN
font_scale=2
color=(255,255,255)
thickness=2
cv2.putText(apollo_img,text,(30,50),font_face,font_scale,color,thickness,cv2.LINE_AA)
rgb_image=cv2.cvtColor(apollo_img,cv2.COLOR_BGR2RGB)
plt.imshow(rgb_image)
plt.axis('off')


#### 14. Read the image ('Boy.jpg').

# read the image
boy_img=cv2.imread('boy.jpg')


#### 15. Adjust the brightness of the image.

# Adjust the brightness
# YOUR CODE HERE
bright_image=cv2.convertScaleAbs(boy_img,alpha=1,beta=50) # increase brightness
dark_image=cv2.convertScaleAbs(boy_img,alpha=1,beta=-50) # decrease brightness
plt.figure(figsize=(12,6))



#### 16. Create brighter and darker images.

# create the brighter and darker
value=50
matrix=np.ones(boy_img.shape,dtype="uint8")*value
img_brighter = cv2.add(boy_img, matrix)
img_darker = cv2.subtract(boy_img, matrix)


#### 17. Display the images (Original Image, Darker Image, Brighter Image).

# Original Image
plt.figure(figsize=(8,5))
plt.imshow(cv2.cvtColor(boy_img,cv2.COLOR_BGR2RGB))
plt.title('Original image')
plt.axis('off')
plt.show()

# Brighter image
plt.figure(figsize=(8,5))
plt.imshow(cv2.cvtColor(img_brighter,cv2.COLOR_BGR2RGB))
plt.title('Brighter image')
plt.axis('off')
plt.show()

# Darker Image
plt.figure(figsize=(8,5))
plt.imshow(cv2.cvtColor(img_darker,cv2.COLOR_BGR2RGB))
plt.title('Darker image')
plt.axis('off')
plt.show()


#### 18. Modify the image contrast.

# Create two higher contrast images using the 'scale' option with factors of 1.1 and 1.2 (without overflow fix)
# Modify the image contrast
matrix1 = np.ones(boy_img.shape,dtype="float32")*1.1
matrix2 = np.ones(boy_img.shape,dtype="float32")*1.2
img_higher1 = (boy_img*matrix1).astype(np.uint8)
img_higher2 = (boy_img*matrix2).astype(np.uint8)


#### 19. Display the images (Original, Lower Contrast, Higher Contrast).

# Display the original image
plt.figure(figsize=(8,5))
plt.imshow(cv2.cvtColor(boy_img,cv2.COLOR_BGR2RGB))
plt.title('Original image')
plt.axis('off')
plt.show()

# Display the contrast image
plt.figure(figsize=(8,5))
plt.imshow(cv2.cvtColor(img_higher1,cv2.COLOR_BGR2RGB))
plt.title('Contrast image')
plt.axis('off')
plt.show()

# Display the Darker image
plt.figure(figsize=(8,5))
plt.imshow(cv2.cvtColor(img_higher2,cv2.COLOR_BGR2RGB))
plt.title('Darker image')
plt.axis('off')
plt.show()


#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.

# Split the image into B,G,R components
blue, green, red = cv2.split(boy_img)

# Display the blue image
plt.figure(figsize=(8,5))
plt.imshow(blue)
plt.title('Blue image')
plt.axis('off')
plt.show()

# Display the green image
plt.figure(figsize=(8,5))
plt.imshow(green)
plt.title('Green image')
plt.axis('off')
plt.show()

# Display the red image
plt.figure(figsize=(8,5))
plt.imshow(red)
plt.title('Red image')
plt.axis('off')
plt.show()


#### 21. Merged the R, G, B , displays along with the original image

# Merged the R,G,B image
blue, green, red = cv2.split(boy_img)
merged=cv2.merge((blue, green, red))

# Display the merged (RGB image)
plt.figure(figsize=(8,5))
plt.imshow(cv2.cvtColor(merged,cv2.COLOR_BGR2RGB))
plt.title('Merged image')
plt.axis('off')
plt.show()


#### 22. Split the image into the H, S, V components & Display the channels.

# Split the image into the H,S,V components
hsv_img=cv2.cvtColor(boy_img,cv2.COLOR_BGR2HSV)
h,s,v=cv2.split(hsv_img)

# Disply the Hue image
plt.figure(figsize=(8,5))
plt.imshow(h)
plt.title('Hue channel')
plt.axis('off')
plt.show()

# Disply the Saturation image
plt.figure(figsize=(8,5))
plt.imshow(s)
plt.title('Saturation channel')
plt.axis('off')
plt.show()

# Display the Value image
plt.figure(figsize=(8,5))
plt.imshow(v)
plt.title('Value channel')
plt.axis('off')
plt.show()

#### 23. Merged the H, S, V, displays along with original image.

#Merged the H,S,V with original image
hsv_img=cv2.cvtColor(boy_img,cv2.COLOR_BGR2HSV)
h,s,v=cv2.split(hsv_img)
merge_hsv=cv2.merge((h,s,v))
merge_bgr=cv2.cvtColor(merge_hsv,cv2.COLOR_HSV2BGR)

# Diaplay the original image
plt.figure(figsize=(8,5))
plt.imshow(cv2.cvtColor(boy_img,cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')
plt.show()

# Display the merged HSV->BGR
plt.figure(figsize=(8,5))
plt.imshow(cv2.cvtColor(merge_bgr, cv2.COLOR_BGR2RGB))
plt.title("Merged HSV → BGR")
plt.axis("off")
plt.show()


## Output:
- i) Read and Display an Image.
  Display the Gray scale image
  <img width="1117" height="584" alt="image" src="https://github.com/user-attachments/assets/122efe24-bbac-4ca9-a9cf-1b88952c1b4d" />

  Display the color image
  <img width="999" height="570" alt="image" src="https://github.com/user-attachments/assets/a2534155-8316-4182-8fc4-cf0f64c50009" />

  Cropped image
  <img width="986" height="603" alt="image" src="https://github.com/user-attachments/assets/6caa7eed-c4ff-4f9a-94ae-d156ae857ce7" />

  Horizantal image
  <img width="958" height="639" alt="image" src="https://github.com/user-attachments/assets/b7428b24-0c03-4f30-a7cd-f6858f15d04b" />

  Add text
  <img width="1151" height="599" alt="image" src="https://github.com/user-attachments/assets/ac7530fa-05c2-4cde-b744-f337b3ddee8c" />

  Set the rectangle in meganta color
  <img width="1157" height="799" alt="image" src="https://github.com/user-attachments/assets/13736e96-0e74-492d-b54d-7eee08f79526" />

- ii) Adjust Image Brightness.
  Disply the original image
  <img width="1017" height="619" alt="Screenshot 2025-08-25 181946" src="https://github.com/user-attachments/assets/c1d5949f-ec3e-4c8f-b4d3-6eb87d63c0f3" />

  Disply the brighter image
  <img width="1031" height="626" alt="Screenshot 2025-08-25 182019" src="https://github.com/user-attachments/assets/cab5fbb2-8497-4d70-9143-cae17bba66af" />

  Disply the darker image
  <img width="1017" height="619" alt="image" src="https://github.com/user-attachments/assets/13d7f254-21b4-413d-b4a1-cf92d5cef99f" />




- iii) Modify Image Contrast.
  Disply the original image
  <img width="999" height="625" alt="image" src="https://github.com/user-attachments/assets/912f7a67-4220-49bf-a38a-c6c1db51efa7" />

  Disply the contrast image
  <img width="1028" height="619" alt="image" src="https://github.com/user-attachments/assets/9e82af7b-aa47-4607-8b66-ea5bbb23a73f" />

  Display the Darker(contrast) image
  <img width="1118" height="625" alt="image" src="https://github.com/user-attachments/assets/2bf306a0-9e2d-4a8e-8067-0a3944ef2a6a" />

  Display the split the image into B,G,R components
  Display the blue image
  <img width="1042" height="618" alt="image" src="https://github.com/user-attachments/assets/81a7e775-d703-4d93-872d-c0bb96955ff9" />

  Dsiplay the green image
  <img width="998" height="633" alt="image" src="https://github.com/user-attachments/assets/6026c17b-b675-4a05-8fee-0cbdbccd5d5d" />

  Display the red image
  <img width="1033" height="617" alt="image" src="https://github.com/user-attachments/assets/7b7901e1-0e8e-448d-9b7b-588e6b61c764" />

  Display the merged image
  <img width="1010" height="625" alt="image" src="https://github.com/user-attachments/assets/a65fb611-eeb7-4257-a25c-305c567bc772" />

  Diaplay the Hue image
  <img width="1093" height="620" alt="image" src="https://github.com/user-attachments/assets/3a68c6b9-c3ad-4ea2-953d-80efbf050cc5" />

  Display the Saturation image
  <img width="1048" height="619" alt="image" src="https://github.com/user-attachments/assets/b1309e5b-02fe-4c5f-abf0-b074848626dd" />

  Display the Value image
  <img width="1046" height="621" alt="image" src="https://github.com/user-attachments/assets/128d9dd5-1a24-482b-a956-a63ce57014be" />

  Display the merged HSV->BGR
  <img width="943" height="622" alt="image" src="https://github.com/user-attachments/assets/636f2e3f-0e58-45e5-9970-d82bb7f523cb" />


## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.
