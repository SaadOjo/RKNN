# DTSIS: Python Programmer's guide for Computer Vision

### Authored by: **Syed Saad Saif**

# Helper libraries and boilerplate code
All computer vision applications share a common steps which include:

* ### Frame capture from camera

* ### Image pre-processing

* ### AI Inference

* ### Result post-processing

* ### Image overlay and display

Furthermore, there are metrics that need to be calculated for performance evaluation. These metrics include.

* ### Average Frame Rate (FPS)

* ### Average Model Inference Time

* ### Pre-processing Time

* ### Post-processing Time

* ### Image Overlay and Draw Time

Since our work is primarily based on embedded systems improving performance by removing bottlenecks is a integral part of our work. Performance metrics are a useful tool to for this process.

As you can see that there is a lot of common work that needs to be done for a computer vision application. It is therefore a good idea to pre-establish a workflow and prepare libraries and boilerplate code to minimize time spent on repetitive pre-preparation. 

**Custom in-house helper python libraries and boilerplate codes are provided for your convenience.**

## Install libraries

_**Note: Make sure that you are in the desired conda virtual enviornment before proceeding with library installation.**_

1. Navigate to: ```~/ai/helper/libraries/wheels/```

1. Install the wheel packages:

    _**Note: Please pay attention to the version numbers as they might change with updates to packages, always install the latest version when multiple wheels are available.**_
    * To install multithreading video capture library run:
    > ### pip3 install video_capture-1.0-py3-none-any.whl

    _**Note: This library is adapted form the project at: ```https://github.com/gilbertfrancois/video-capture-async```**_

    * To install the metrics library run:
    > ### metrics-1.0-py3-none-any.whl

    * ### Install the text overlay library by running:
    > 
Note that the source code of the wheels is also provided at ```~/ai/helper/libraries/source/``` and can be reviewed for better understanding how the code works. 

## Library APIs

### Video Capture Multithreading:

* Import the library like: 
    ```python
    from video_capture.capture import VideoCaptureThreading
    ```
* Initialize the capture stream like:
    ```python
    cap = VideoCaptureTreading(0, 1280, 720)
    ```
    The first argument is the **camera id**, then the desired **width** and **height** respectively.

* Initializing the capture stream does not automatically start the video stream. Start the stream by calling:

    ```python
    cap.start()
    ```

* To get the frame call:
    ```python
    ret, frame = cap.read()
    ```
    **ret** returns if the frame was captures sucessfully.
    
    The return value **ret** should be in a loop to make sure frame capture is sucessful before processing the frame. An example is as follows:

    ```python
        
    While True:
        if ret != True:
            continue
        (frame processing code)
    ```

    **frame** contains a numpy array of **shape = (HEIGHT, WIDTH, CHANNELS)** and data **type of uint8**. Pay attention to the shape of the frame. A lot of errors can be avoided in the shape is kept in mind. 

* Finally, stop device capture by calling:
    ```python
    cap.stop()
    ```

### Metrics 
    Average
    FPS
### Text Overlay

## Boilerplate codes

1. Navigate to: ```~/ai/helper/boilerplate_codes/```

# Python OpenCV essentials

# Numpy essentials