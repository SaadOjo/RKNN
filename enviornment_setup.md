## Enviornment Setup for RKNN
#### Authored by: Syed Saad Saif

### _**Read README.md before you continue!**_

Before we can use the RK1808S0 Stick we need to perform enviornment setup.

1. ## Setup virtual enviornment to install rknn-toolkit and dependencies.

    * #### Install conda to manage our virtual enviornment. (Skip this step already installed)

        1. Download the miniconda installer from [here.](https://docs.conda.io/en/latest/miniconda.html#linux-installers)
  
        1. Alternatively, use the downloaded version at: &nbsp; ```~/ai/dependencies/Miniconda3-latest-Linux-x86_64.sh```

        1. Make script executable: (Replace with real script name)   
            > ### chmod +x <name_of_installer_script.sh>
    
        1. Execute the script: (Replace with real script name)
            > ### ./<name_of_installer_script.sh>

        1. press **S** to skip EULA. Agree to the prompts.

        1. Close and reopen the terminal **OR** run:
            > ### source ~/.bashrc 

    * #### Create a virtual enviornment named **rknn_cpu** with python version **3.6.9**
        > ### conda create --name rknn_cpu python=3.6.9

    * #### Activate the newly created enviornment:
        
        > ### conda activate rknn_cpu 

        Note: The enviornment can be deactivated by: **conda deactivate**
    * #### Verify the python version:

        > ### python3 --version

        ```bash
            > Python 3.6.9 :: Anaconda, Inc.
        ```
    * #### Install required packages.

        1. Install openCV:
            > ### pip3 install opencv-python
        2. Install Tensorflow:
            > ### pip3 install --user tensorflow==1.14
    
        1. Download the rknn toolkit [here.](https://github.com/rockchip-linux/rknn-toolkit/releases/download/v1.4.0/rknn-toolkit-v1.4.0-packages.zip) (version 1.4.0)
            * Extract the zip archive.

            * Navigate to the extracted folder.

            ### OR

        1. Navigate to ```~/ai/dependencies/rknn-toolkit-v1.4.0-packages/```

        1. Run:
            > ### pip3 install rknn_toolkit-1.4.0-cp36-cp36m-linux_x86_64.whl





    


    