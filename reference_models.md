# DTSIS: Reference AI Models for Computer Vison Applications
### Authored by: Syed Saad Saif

Our main goal at the DTSIS AI department is to have high performance models suitable to be run on embedded AI inference accelerators. The models must have a good balance between accuracy and inference time. Open-source implementation of AI models are a great resource which you can use directly or adapt to your specific application or use as a reference to create your own custom model. Note that at the end we must convert the model to rockchip's proprietary format (.rknn). Keep in mind that this process is not easy and the ability to sucessfully convert this model depends on a variety of factors. Further details about model conversion are provided [here.](rknn_model_conversion.md)

# Obtain pre-trained model ready for conversion

Before you can convert the model to RKNN we must have a trained model in one of the formats that the RKNN converter supports. More details [here.](rknn_model_conversion.md) We can reach this step by one of the following ways.  

1. ### **Download a pre-trained model.**
    This is is suitable in-case the dataset the model is trained on is suitable for your application. Examples are face detection, as long as the pre-trained model is trained on a diverse dataset, the face detector should work well and does not need to be trained on a custom dataset. Counter example is object detection. There are some pre-trained models available trained on datasets such as [COCO](https://tech.amikelive.com/node-718/what-object-categories-labels-are-in-coco-dataset/) or PASCAL VOC the classes of the datasets on which the model was trained might be different than what we wan to find. In that case downloading a pre-trained model is not suitable. Also take note that even if the classes is the same but the distribution of the data used for training is different that what we expect to use the model on, using a more representative dataset for training will improve real word performance.

 1. ### **Find a implementation (trainable code) of a model and train on desired dataset.**
    As mentioned previously sometimes we cannot use a pre-trained model if the data-set has different classes or even if the classes are same the distribution of the images might be different that the expected use case it is better to train the model on a more representative dataset. 

 1. ### **Find a implementation of a model modify architecture according to our needs and train on desired dataset.**
    [Vanilla](https://en.wikipedia.org/wiki/Vanilla_software) version of the implementation might need to be modified for one of two reasons. 

    1. Unable to convert model to rknn. 


        Some layers might be unsupported in this case they might be swapped with alternates. As an example ELU is not supported by RKNN (as of version 1.3.2) and the layer can be replaced by ReLU. 
    
    2. Modify the implementation to better suit the dataset.

        * Optimizing hyper-parameters.

            Better results can be obtained if hyper-parameters such as learning rate, l2-regularization level, and drop-out are [optimized](https://en.wikipedia.org/wiki/Hyperparameter_(machine_learning)) according to the dataset.  

        * Modifying model architecture.

            The model architecture might need to be modified to better suit the dataset. Significant performance gains can be made by removing redundant parts of the network (redundant with respect to the dataset distribution). Read the respective research paper thoroughly to try to understand is there is a redundancy that can be removed. As an example consider a object detector. In the object detector there are specific layers that are there to find objects of specific sizes. If your dataset distribution does not consist of objects of a certain scale range, the respective layer from the model can be removed. 
 1. ### **Develop model from scratch and train on desired dataset.**
    Finally, sometimes it might be required to develop a model architecture from scratch. This would usually not the method that you would use, however this method does provide complete freedom and might be useful if you want to try something new. A use case could be a new research paper that does not have an implementation publicly available, in that case the model can be developed using the paper as reference. 


# What to look in a model
At times it might seem like a good idea to look for the models with the highest accuracy, this would be true if we had unlimited compute power but since we have to run the model of a small embedded accelerator we must use a computationally light model to satisfy the fps (frames per second) requirement. 

**As a rule of thumb follow the following steps:** 

* Establish a desired fps range requirement for the model, discuss this with your supervisor. 

* Consider the pre-processing and post processing time required for your specific task. The pre-processing and post-processing times should not change greatly according to the model. Do keep in mind that the final application will be written is C/C++ and therefore will be faster than your prototype program. The calculated times should be calculated considering this fact.

* Calculate the required range of model inference times. 
    
    > **let:** fps = [min_fps, max_fps]
    >
    > total_processing_time = pre-processing-time + post-processing-time
    >
    > total_time_period = [1000/min_fps, 1000/max_fps]
    >
    > inference_time = total_time_period - processing_time

    This should give a range of inference times that are acceptable.  



Another important factor is the likely-hood of the model to be converted to rknn. There various factors that affect this likely-hood. Common issues that prevent conversion include:

* Unsupported layers

* Not fully supported platforms.
    _Newer version of tensorflow is not fully supported by rknn model converter.(as of RKNN version 1.3.2)_

# Resources for model implementation and research papers

1. [Papers with Code](https://paperswithcode.com/)

    This is a great resource to find papers that have open-source implementations available. Many times implementations in many frameworks (tensorflow, pytorch etc) are available and the most suitable implementation can be selected. 

2. [arxiv.org](https://arxiv.org/)

    Up-to-date research papers for machine learning (and more) are available here. 

# Dataset is key

Understand that goal is to train the model such that the performs well on the distribution that it is expected to encounter in the field. The evaluation metrics that we observe here are key. Try to create a representative dataset and calculate metrics on this dataset to have an idea how the model will perform on in the real world.