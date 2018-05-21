# Introduction to Graphical Information Systems Using Python

This repository contains worked examples in [Jupyter
notebooks](http://jupyter.org/) for the 3-day online course
[Introduction to Python
GIS](https://automating-gis-processes.github.io/CSC18/) by CSC
Finland. The materials are originally drawn from the [Automating GIS
Processes](https://automating-gis-processes.github.io/2017/) masters
course at the University of Helsinki.

## Installing GIS Python Modules on Ubuntu Linux

Performing GIS tasks in Python relies on a suite of python modules
that can sometimes have complex dependencies. The easiest way to get a
working installation is to build python environment that contains
specific module versions drawn from the same packaging source. This
has the advantage that you can load the environment as needed, so it
won't break existing installations.  Here I use the Anaconda Python
distribution and create a Python 3.5 environment called ```gis``` and install modules from the [conda-forge](https://conda-forge.org/) organisation.

### Download and install Anaconda:

From the command line do the following:

```
wget https://repo.continuum.io/archive/Anaconda3-4.1.1-Linux-x86_64.sh
bash Anaconda3-4.1.1-Linux-x86_64.sh
```

My preference is to install the distribution in a shared directory
```/opt/share/anaconda3_GIS``` and use a command-line alias to make it
visible to the system (I have multiple Python installations that I
need for different tasks). If you want to do this edit your
```$HOME/.bash_aliases``` file to contain:

```
alias aconGIS="export PYTHONPATH=/opt/share/anaconda3_GIS; export PATH=/opt/share/anaconda3_GIS/bin:/opt/share/anaconda3_GIS/lib/python3.5/site-packages:$PATH;"
```

If this is going to be your default Python, you can just add the line
without the surrounding ```alias aconGIS=" ... "```. Restart your
terminal window, execute ```aconGIS``` (if necessary) and check you are
pointing to the correct Python install using ```which python```.

### Install GIS Modules

Download this repository by clicking on "Clone or Download" above, or executing the following on the command line:

```
git clone https://github.com/crpurcell/IntroPythonGIS.git
```

We are going to create a new "conda" environment and install most
Python modules using a yml file (which specifies the environment name,
modules and version numbers):

```
cd IntroPythonGIS
conda env create -f gis.yml
```

We need to install PyCRS using the standard ```pip``` command. This is
a fixed version from GitHub user ```mullenkamp```.

```
pip install https://github.com/mullenkamp/PyCRS/archive/master.zip
```

Lastly, the QGIS software is very useful to check that your Python
scripts are doing the right thing. Install this from the Ubuntu
repositories using the command ```sudo apt-get install gqis``` (admin
privileges needed).


## Running the Python Jupyter Notebooks

* Before running the notebooks, download the example datasets and move
the data into a sub-directory ```IntroPythonGIS/Data```. Data are
available from
[here](https://github.com/Automating-GIS-processes/Lesson-2-Geo-DataFrames/raw/master/data/Data.zip),
[here](https://automating-gis-processes.github.io/CSC18/_static/data/L2/Europe_borders.zip),
[here](https://automating-gis-processes.github.io/CSC18/_static/data/L3/addresses.txt)
and
[here](https://github.com/Automating-GIS-processes/Lesson-4-Classification-overlay/raw/master/data/data.zip). *

To run the Jupyter Notebooks, do the following on the command line:
```
aconGIS              # (if you made an alias in your .bash_aliases file)
source activate gis  # to activate the python environment
jupyter-notebook     # to start the Jupyter notebook server.
```

Go to your browser and have fun doing GIS analysis in Python!
