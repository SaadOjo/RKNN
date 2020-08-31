# DTSIS: Python Example for RockX
### Authored by: Syed Saad Saif

RockX is a library for rockchip accelerator devices that provided pretrained models for common AI tasks such as **Object Detection** and **Face Recognition**. 

The complete list of RockX modules is as follows:

{add python list:}


# Enviornment Setup

1. Create a conda virtual enviornment for RockX. Since we share a lot of packages from the **rknn_cpu** enviorment, let's clone it.

    _**Useful tip: You can find the names of the current envoirnment by running:**_ 

    > ### conda env list
    ```
    # conda environments:
    #
    base                     /home/dtsis-ai/miniconda3
    rknn_cpu              *  /home/dtsis-ai/miniconda3/envs/rknn_cpu
    test                     /home/dtsis-ai/miniconda3/envs/test
    ```
    To clone virtual enviornment run:

    > ### conda create --clone rknn_cpu --name rockx

1. To activate the **rockx** enviornment run:

    > ### conda activate rockx

1. Install the rockx pip package:

    * Navigate to ```~/ai/rockchip/RockX_SDK_V1.2.0_20200302/python```

    OR

    * Alternatively download the **RockX SDK** from:

        [Toybrick Download Page.](http://t.rock-chips.com/portal.php?mod=list&catid=11&product_id=4) (Translate it from Chinese)

        * Extract and navigate to python sub-directory.

    * Install pip3 package by running:

        _**Note: change the wheel filename in case of a different RockX version.**_

        > ### pip3 install RockX-1.2.0-py3-none-any.whl

    * Verify if the package is installed by running:

        > ### pip3 list | grep RockX

# Python Example

_**Note: Make sure that you are in the rockx virtual enviornment before running RockX examples.**_
    
