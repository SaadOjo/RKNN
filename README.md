## DTSIS: RKNN Compute Stick Documentation

#### Authored by: **Syed Saad Saif**

### This repository contains tutorials and guidelines that will be useful for developing AI solutions meant to be run on the RKNN Compute stick.

_**Before starting make sure that you have access to the required files and satisfy the dependencies.**_

* Required files:

    1. _**ai**_ folder. 
    
        This is available at the DTSIS **Network Attached Storage** (NAS).  
        Copy this folder to your home directory. 

* Dependencies:

    1. Operating System: **UBUNTU 18.04 LTS**

        Verify ubuntu version:
 
        > ### lsb_release -a 

        ```bash
        > No LSB modules are available.  
        > Distributor ID:	Ubuntu  
        > Description:	Ubuntu 18.04.4 LTS  
        > Release:	18.04  
        > Codename:	bionic
        ```


    2. Graphics Card: **NVIDIA Card Supporting CUDA** {mention cuda verison}

        check graphics card by running:
        > ### nvidia-smi
        ```bash
        Fri Aug 28 09:57:30 2020       
        +-----------------------------------------------------------------------------+
        | NVIDIA-SMI 440.100      Driver Version: 440.100      CUDA Version: 10.2     |
        |-------------------------------+----------------------+----------------------+
        | GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
        | Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
        |===============================+======================+======================|
        |   0  GeForce MX150       Off  | 00000000:01:00.0 Off |                  N/A |
        | N/A   64C    P0    N/A /  N/A |    572MiB /  2002MiB |      7%      Default |
        +-------------------------------+----------------------+----------------------+
                                                                                    
        +-----------------------------------------------------------------------------+
        | Processes:                                                       GPU Memory |
        |  GPU       PID   Type   Process name                             Usage      |
        |=============================================================================|
        |    0      1957      G   /usr/lib/xorg/Xorg                           251MiB |
        |    0      2132      G   /usr/bin/gnome-shell                         208MiB |
        |    0      2446      G   ...quest-channel-token=1807755420600173261    73MiB |
        |    0      5885      G   ...uest-channel-token=11862114564350336331    36MiB |
        +-----------------------------------------------------------------------------+
        ```

### After making sure that you have access to the required files and satisfy the dependencies you can proceed to the next steps.

## Important notes about tutorials:

* ### Shell Variables

    In the tutorials Shell variables are used extensively to allow the user to easily copy paste commands into the terminal. However, note that some problems can arise if the tutorial is not followed exactly or if some of the steps are skipped. **Some notes as well as common problems and their solutions are listed here.**

    * Shell variables apply only to the current shell and will not carry over if you open a new terminal.

    * To see if a specific variable is registered in the shell run:

        > ### set | grep [NAME_OF_VARIABLE]

        ```
        TEST_VARIABLE='TEST VARIABLE'
        ```
    * If you still experience issues with shell variables, you can substitute the variable names with the values. Use your judgement to infer what values need to go inplace of the shell varaibles.

        **Example:**
        
        > Shell variables set to:
        >
        > BUS='002'
        > 
        > DEVICE='004'

        The command:

        > ### ls -l /dev/bus/usb/$BUS/$DEVICE

        Can be substitued by:

         > ### ls -l /dev/bus/usb/002/004




    

## Links to documentation:
1. [Enviornment Setup](enviornment_setup.md)

