# What is Video

In computer vision perspective, video(Digital video) is an electronic representation of moving visual images in the form of encoded digital data. Basically, video is created by a series of image frames. Each image frame has shape width x height x channel.

```
FPS: "frame per second" is measure the rate at which frames are displayed is known as the frame rate.
```

## Getting Started with Video using OpenCV Python

### Outline:
1. Get video source
2. Read source video
3. Display video
4. Save video

### Prerequisites

The main library you need to install before starting ( [Full code in python file](https://github.com/Hank-Tsou/Computer-Vision-OpenCV-Python/blob/master/tutorials/Basic_Features/Video/Video.py))

```
pip install opencv-contrib-python
```

### 1. Get video source

#### - Use function cv2.VideoCapture(Argument_1) to "get" a video source. 

- Argument_1: 
  - Read from video file: give a video name in the working directory or full video path (String).
  - Read from webcam: give 0, it will open the default camera (Integer).
```python
# get video source from video file
cap = cv2.VideoCapture("cat.mp4")

# get video source from webcam
cap = cv2.VideoCapture(0)
```
```
Note: Use function "cv2.VideoCapture(_).isOpened()" to check get video success or not. (Boolean)
```

### 2. Read source video
              
#### - Use function cv2.VideoCapture(__).read() to "read" a video frame by frame. 

- no argument
- return: (boolean, frame), When read a frame return true and frame image else return false.
```python
ret, frame = cap.read()
```

### 3. Display video

#### - Use function imshow(Argument_1, Argument_2) with while loop to display a video.
- Argument_1: display window name (String)
- Argument_2: pass your image frame into the function
```python 
cv2.imshow('frame',frame)             # display frame image
cv2.waitKey(10)                       # control the output speed of the video.
if cv2.waitKey(1) & 0xFF == ord('q'): # PRESS "q" to exit
    break
    
cap.release()                          # When everything done, release the capture
cv2.destroyAllWindows()                # destroy all the windows
```
```
Note: Make sure proper versions of ffmpeg or gstreamer is installed. Sometimes, it is a headache 
to work with Video Capture mostly due to wrong installation of ffmpeg/gstreamer. (OpenCV-Python Tutorial)
```

### 4. Save or Write video

#### Define the codec
```python 
# FourCC is a 4-byte code used to specify the video codec.
fourcc = cv2.VideoWriter_fourcc(*'XVID')
```
#### create VideoWriter object by using function cv2.VideoWriter(arg_1, arg_2, arg_3, arg_4 [, arg_5])
- arg_1: output file name, ex: output.avi
- arg_2: fourcc
- arg_3: number of frames per second (fps)
- arg_4: frame size
- arg_5: last one is isColor flag. If True(default), encoder expect color frame, otherwise works with grayscale frame.
```python
out = cv2.VideoWriter('output.avi',fourcc, 10.0, (640,480))
```

#### - Use function  cv2.VideoWriter(__).imwrite(Argument_1) to save a video.
- Argument_1: passing image frame
```python
out.write(frame) # save video 
...
out.release() # when finished, release video writer
```

## Code
- [Full code in python file](https://github.com/Hank-Tsou/Computer-Vision-OpenCV-Python/blob/master/tutorials/Basic_Features/Video/Video.py)

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Reference & Acknowledgments

* OpenCV-Python Tutorial: https://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_tutorials.html
* OpenCV Document: https://docs.opencv.org/3.4/
* Wiki: https://en.wikipedia.org/wiki/Digital_video

