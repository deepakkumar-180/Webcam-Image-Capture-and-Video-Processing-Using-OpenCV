# EXP-2 Image Capture and Video Processing Using OpenCV

## Aim

To write a Python program using OpenCV to capture an image from the webcam and perform the following operations:

1. Write the frame as a JPG file  
2. Display the video  
3. Display the video by resizing the window  
4. Rotate and display the video  

---

## 🛠️ Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  

---

## ⚙️ Algorithm

### Step 1:
Import the required libraries and initialize the webcam using `cv2.VideoCapture()`.

### Step 2:
Capture frames continuously from the webcam.

### Step 3:
Save a frame as a JPG image using `cv2.imwrite()`.

### Step 4:
Display the live video stream using `cv2.imshow()`.

### Step 5:
Resize the frame and rotate it using OpenCV functions, then display the processed frames.

---

### Developed By :DEEPAKKUMAR S


### Register No :212225230042
## Program
```
import cv2

cap = cv2.VideoCapture(0)

if not cap.isOpened():
    print("Cannot open webcam")
    exit()

fourcc = cv2.VideoWriter_fourcc(*'mp4v')

# Video 1: Original video
out1 = cv2.VideoWriter('original_video.mp4', fourcc, 20.0, (640, 480))

# Video 2: Resized video
out2 = cv2.VideoWriter('resized_video.mp4', fourcc, 20.0, (640, 480))

# Video 3: Rotated video
out3 = cv2.VideoWriter('rotated_video.mp4', fourcc, 20.0, (480, 640))

# Video 4: Original video with JPG capture
out4 = cv2.VideoWriter('captured_video.mp4', fourcc, 20.0, (640, 480))

image_saved = False

while True:
    ret, frame = cap.read()

    if not ret:
        break

    frame = cv2.resize(frame, (640, 480))

    # Condition 1: Capture JPG image and display video
    if not image_saved:
        cv2.imwrite('captured_image.jpg', frame)
        image_saved = True

    cv2.imshow('1. Capture JPG and Display Video', frame)
    out1.write(frame)

    # Condition 2: Display resized video
    resized = cv2.resize(frame, (640, 480))
    cv2.imshow('2. Resized Video', resized)
    out2.write(resized)

    # Condition 3: Rotate and display video
    rotated = cv2.rotate(frame, cv2.ROTATE_90_CLOCKWISE)
    cv2.imshow('3. Rotated Video', rotated)
    out3.write(rotated)

    # Condition 4: Display and save another video
    cv2.imshow('4. Captured Video', frame)
    out4.write(frame)

    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

cap.release()
out1.release()
out2.release()
out3.release()
out4.release()
cv2.destroyAllWindows()

print("All videos and the JPG image have been saved.")
```


## Output

### i) Write the frame as JPG image
Captured image is saved as `captured_image.jpg`

### ii) Display the video
Live webcam video is displayed

### iii) Display the video by resizing the window
Video is shown in resized resolution (640 × 480)

### iv) Rotate and display the video
Video is displayed after rotation (90° clockwise)

---

## Result

Thus, the image is successfully captured from the webcam and various video processing operations such as saving, displaying, resizing, and rotating are performed using OpenCV.
