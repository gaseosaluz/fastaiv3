# Development Environment

This document contains description and notes of my development environment. While it is mostly about the software I do inlucde a small section on the hardware that I use - because it is a machine that I custom built for my machine language work.

## Hardware

TBD - I will include here a few notes on my custom built system. A high level view of the specs

## Software

For the most part the software environment that I discuss here is what Jeremy Howard recommends during his classes. I do have here a small section that defines additonal work that I do to connect remotely to my Machine Learning System (a.k.a. `inti`). I do this because I access it _remotely_ inside my home network. I thought these notes may be of use to somebody.

### Machine Learning Software

* fast.ai Library
* Pytorch 1.xxx. Actually whatever library is required by the latest version of the fast.ai library
* miniconda environemnt. Note that I do not install the full Anaconda environment as I feel it is too bloated. I simply install a base `miniconda` package and then create virtual `conda` environments with the packages I need.
* For this project (which is to work through the course material of the V3 MOOC for fast.ai - including additional homework) I created a virtual environemnet. If you want to see the packages and contents of the environment please see the `venvs` directory and you will find a file called `fastaiv3.yml` that describes the environment that I use for the clas..
* I use Jupyter Notebooks (not Jupyter Labs)

### Useful Tools

* iTerm - Terminal emulator on OS X
* tmux - Text based 'windowing' high efficiency environment. I use it to set up multiple sessions from my Mac Laptop to my Linux ML machine.
* ssh. Make sure that this is installed and keys have been generated. I use this to create a tunnel between my MacPro and my Linux ML machine. I connect via SSH or I connect to a Jupyter Notebook that is running (headless) on my ML machine.
### Development Environemnt ###
* `htop`. A juiced up version of top
* `nvtop` - A version of 'htop` to minitor the GPU utilization and memory.

My main development machine is a custom build Intel Powered (i9) machine with an NVIDIA RTX 2080 Ti GPU card. I will provide more details on the build specs in a section above at a later date.  

This machine is located in a 'remote' area in my house and I access it remotely inside my network from my Mac book Pro

### Setting Up A remote (via SSH) Jupyter Server

If you want to run the fast.ai code in one machine (in my case a Ubuntu 18.04 machine with a GPU card) but work remotely (on a Mac Laptop - but any other computer browser will work) then

    1. From a terminal in window (in my Mac I use `iTerm2`) your remote workstation (in my case my Mac Book Pro) open a terminal instance and type:

    ssh -L 8000:localhost:8888 your_usr_id@your_server_ip
    ssh -L 8000:localhost:8888 edm@inti.local
    
    This will log you into your remote server (creating an SSH tunnel to it). 
    
    2. From your server (from step 1) cd to your project directory and activate your virtual environment of choice. You should have installed Juptyer into that environment.

    <your_shell_prompt>$ jupyter notebook

    3. Note that the '8888' address is the address for the 'remote' server (where you started the notebook). To access the notebook in a remote machine, remember that you tunneled to it earlier and you used port number 8000. So the address on your remote machine should be:

     http://localhost:8000/?token=<generated token>

    This will open the Jupyter notebook on your loccal machine, but connected to the remote machine. All code will run on the remote machine.
    
    You can now proceed to browse to the course directory and start the course or run your own experiments.
    

