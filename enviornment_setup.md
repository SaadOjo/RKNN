## DTSIS: Enviornment Setup for RKNN
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

        1. Navigate to: ```~/ai/dependencies/rknn-toolkit-v1.4.0-packages/```

        1. Run:
            > ### pip3 install rknn_toolkit-1.4.0-cp36-cp36m-linux_x86_64.whl

        1. Verify that rknn toolkit is properly installed

    * #### Giving USB Compute Stick required permissions  
        1. Plug the Compute Stick in to the USB port of your device.
        
        1. Run:
            
            > ### lsusb

            ```bash
            Bus 002 Device 004: ID 2207:0018
            Bus 002 Device 003: ID 0bda:8153 Realtek Semiconductor Corp. 
            Bus 002 Device 002: ID 05e3:0626 Genesys Logic, Inc. 
            Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
            Bus 001 Device 006: ID 04f3:0903 Elan Microelectronics Corp. 
            Bus 001 Device 005: ID 8087:0a2b Intel Corp. 
            Bus 001 Device 004: ID 0bda:58e4 Realtek Semiconductor Corp. 
            Bus 001 Device 003: ID 046d:c534 Logitech, Inc. Unifying Receiver
            Bus 001 Device 007: ID 9636:9300  
            Bus 001 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
            Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
            ```
            Make sure that you see the line with _**ID 2207:0018**_

            This device is the Compute Stick and it means that device is recognized by the computer.

            * To Store the **Bus** number and **Device** number as envoirnment varables run.

            _These variables will be used in the following steps._ 

        1. Navigate to: ```~/ai/rockchip/tools ```

        1. To make script executable run:
            > ### chmod +x ./update_rk1808_ai_cs_rule.sh

        1. To change Compute Stick USB permissions run:
            > ### ./update_rk1808_ai_cs_rule.sh

        1. To verify if the device permissions have been updated run:

            > ### ls -l /dev/bus/usb/$BUS/$DEVICE    
            ```bash
                crw-rw-rw- 1 root root 189, 131 Ağu 28 08:55 /dev/bus/usb/002/004
            ```
            Make sure that the permisions are as expected. i.e **crw-rw-rw-**

    * #### Verify inference can be performed on the newly configured Compute Stick

        1. Navigate to: ```~/ai/rockchip/examples/inference_test``` 


            

        

        
            



    


    