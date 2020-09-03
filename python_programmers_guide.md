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

_**Note:** It might be useful to create your own packages and also make changes to existing ones. You can also upload to PyPI. To create your packages follow the resources provided below as a reference._ 

* [Making a python Package.](https://python-packaging-tutorial.readthedocs.io/en/latest/setup_py.html)
* [Beginner's Guide.](https://medium.com/swlh/beginners-guide-to-create-python-wheel-7d45f8350a94)
## Install libraries

_**Note: Make sure that you are in the desired conda virtual enviornment before proceeding with library installation.**_

1. Navigate to: ```~/ai/helper/libraries/wheels/```

1. Install the wheel packages:

    _**Note: Please pay attention to the version numbers as they might change with updates to packages, always install the latest version when multiple wheels are available.**_
    * To install multithreading video capture library run:
    > ### pip3 install dtsis_video_capture-1.0-py3-none-any.whl

    _**Note: This library is adapted form the project at: ```https://github.com/gilbertfrancois/video-capture-async```**_

    * To install the metrics library run:
    > ### dtsis_metrics-1.0-py3-none-any.whl

    * ### Install the text overlay library by running:
    > 

Note that the source code of the wheels is also provided at ```~/ai/helper/libraries/source/``` and can be reviewed for better understanding how the code works. 

## Library APIs

### Video Capture Multithreading:

* Import the library like: 
    ```python
    from dtsis_capture import VideoCaptureThreading
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
The metrics library contains two classes **fps** and **average**:

1. ### **average**
    The _**average**_ library can be used to create a running average of noisy variables (such as model inference time) be able to better understand the evolution of the variable.

    1. Import the library:
        ```python
            from dtsis_metrics import average
        ```
    
    1. Create a new instance for every variable you want to average. Here we assume that we have a variable ```noisy_variable``` of which we would like to get a running average. Give the number of samples to average over as an argument to the constructor.

        ```python
        ...
        noisy_var_average = average(100)
        ```
    1. Pass the value the variable to be averaged. Consider we have a loop, we will pass the value of the variable at each loop iteration.
        ```python
        while True:
            #Value of noisy variable updated
            ...
            noisy_var_average.update(noisy_variable) 
        ```
    1. Get the averaged (running average) value of the variable by calling:
        
        ```python
            averaged_noisy_var = noisy_var_average.average()
        ```
        Please note that until the **update** method is called at least the **number of samples to average** (argument passed to the constructor) times, the **average** method will just return the latest value of the variable. 

    1. ### **fps**

    The _**fps**_ library is a convenient way to calculate the fps of your main loop.

    1. Initialize the python fps function by:
        
        ```python
        fps_counter = fps()
        ```
        Note that the timer starts first timer starts as soon as you call the constructor so it is better to initialize it just before entering the loop. However note that this should only affect the first fps value and will not matter in the long run.

    1. Inside the loop call the update method at exactly once.
        ```python
        while True:
            ...
            #rest of code
            ...
            fps_counter.update()
        ```

    1. Get the current fps value by calling:
        ```python
            fps_value = fps.counter.get_fps()
        ```

### Text Overlay

It is useful to show some information overlayed on the screen. opencv provides a function but it requries a lot of parameters to be calculated manually. This library provides a wrapper to the opencv text overlay function to make this a bit easier.

## Boilerplate codes

1. Navigate to: ```~/ai/helper/boilerplate_codes/```

# Python OpenCV essentials

# Numpy essentials