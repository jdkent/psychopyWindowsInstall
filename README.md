# Installing psychopy on a windows machine

This instructional guide will walk through getting a windows computer to run psychopy

## Step 1: [Install Git for Windows](https://git-scm.com/download/win)

While you don't need git for psychopy, it comes with a terminal emulator that will be useful for installing psychopy.
(And if you're generating code, you'll want to consider versioning the code with git)

**Notes**
- open the exe file when it finishes downloading after you follow the link
- accept all defaults during installation (except you can change the default text editor from vim to nano since nano is more friendly to beginners)
- insert image
- Open the Git Bash terminal, right click on the icon and pin it to your taskbar, it will allow for easy access. [supplemental windows instructions on how to do this](https://support.microsoft.com/en-us/help/15059/windows-8-pin-apps-folders-desktop-taskbar)

## Step 2: [Install Miniconda](https://conda.io/miniconda.html)

Select the 3.6 python version (either 32 bit or 64 bit) depending on your operating system (it's probably 64 bit), but you can follow the instructions from [microsoft help](https://support.microsoft.com/en-us/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64) to make sure.

**Notes**
- Keep all the defaults (Install just for yourself, otherwise you will have to run the terminal as an administrator if you want to install any python packages)

## Step 3: Modify the terminal environment

To access the miniconda installation open the Git Bash terminal and change your directory to your home directory.
Your terminal should look something like this:
- insert image

We will create a `.bash_profile` file that will make the miniconda commands accessible to the terminal.
To create the file you will type:
```bash
touch ~/.bash_profile
```
To edit the empty file we will type:
```bash
nano ~/.bash_profile
```
This will open up to a editor in your terminal with little buttons on the bottom.

You will now enter the following text to the editor.
```bash
PATH=${HOME}/Miniconda3:${HOME}/Miniconda3/Scripts:${PATH}
export PATH

# this is a known bug for the terminal editor
alias python='winpty python.exe'
```

Finally, either type:
```bash
source ~/.bash_profile
```
or close and open your terminal again so the changes in the `.bash_profile` will be implemented.

## Step 4: Create a conda environment for installing psychopy
Conda environments allow one to make a playground to install packages and break their environment with little consequence to your main python installation.
I wouldn't install much on the base (miniconda) installation, but do most of the installs on conda environments for each project you work on.

To create a conda environment, type the following:
```bash
conda create -n pschpy python=3.6
```

to begin using the environment, type:
```bash
source activate pschpy
```

Your terminal should look something like this:
- <insert image>

**Note**
- to deactivate the `psychpy` environment type `source deactivate`

## Step 5: [Install Psychopy](http://psychopy.org/installation.html#anaconda-and-miniconda)
We will now install psychopy, make sure the `psychpy` environment is activated.

The first install command copied from the link.
```bash
conda install numpy scipy matplotlib pandas pyopengl pillow lxml openpyxl xlrd configobj pyyaml gevent greenlet msgpack-python psutil pytables requests[security] cffi seaborn wxpython cython pyzmq pyserial
```

The second install command coped from the link
```bash
conda install -c conda-forge pyglet pysoundfile python-bidi moviepy pyosf
```
**Note**: conda couldn't find the `pysoundfile` package, so I had to install that via `pip` and re-run the above code with `pysoundfile` removed:
```bash
conda install -c conda-forge pyglet python-bidi moviepy pyosf
```

The third install command (with `pysoundfile` added)
```bash
pip install zmq json-tricks pyparallel sounddevice pygame pysoundcard psychopy_ext psychopy pysoundfile
```

TODO: what's the name of the post_install file?
Finally, run the post_install file from psychopy to properly install `psychopy`

Now you can run psychopy!
type:
```bash
psychopyApp.py
```
and the application _should_ open.

Yay, you made it! :+1:
