# Run3 muon system analysis

### Installing anaconda

```bash
# select a directory to install anaconda
cd /nfs/dust/cms/user/lbenato/

# get the anaconda installer
# Note: To have the latest version, you can look up the list at
# https://repo.continuum.io/archive/
wget https://repo.continuum.io/archive/Anaconda3-2023.09-0-Linux-x86_64.sh

# install anaconda
bash Anaconda3-2023.09-0-Linux-x86_64.sh

# press ENTER to review the license agreement and type "yes" to accept

# ATTENTION! When asked where to install anaconda,
# do NOT press enter to confirm the default location,
# but provide your dust home directory instead
# (type: /nfs/dust/cms/user/lbenato/anaconda3).

# Answer all other prompts with the recommended option (in brackets).
# Optional: To have an easier way to activate your conda environment,
# you can allow anaconda to edit your .bashrc file.

# load anaconda - valid for DESY only
# IMPORTANT: You have to run this command every time you log in to NAF!
export PATH=/nfs/dust/cms/user/lbenato/anaconda3/bin:$PATH

```


### Creating a conda environment

We will be working inside a conda environment. To create and activate the environment, follow the instructions below:

```bash
# create a conda environment called "run3"
# most recent versions of python cause issues with root/uproot/awkward
conda create -p /nfs/dust/cms/user/lbenato/anaconda3/envs/run3 python=3.7

# activate the environment
# IMPORTANT: You also need to run this command every time you log in to NAF!
source activate /nfs/dust/cms/user/lbenato/anaconda3/envs/run3
```

### Installing required packages

**Note:** When installing packages with conda, the "solving environment" step can take a long time. This is normal behavior so do not abort the installation (unless it runs longer than several hours).

```bash
# cd to your environment directory
# Note: This is important! If you try to install packages when not in
# your environment directory, you might get file I/O errors!
cd /nfs/dust/cms/user/lbenato/anaconda3/envs/run3/

#install pandas (for data manipulation and analysis)
conda install pandas

# install matplotlib
conda install matplotlib

# install pytables
conda install pytables

# install scikit-learn
conda install scikit-learn

# install ROOT
conda config --remove channels conda-forge
conda config --add channels conda-forge
conda config --set solver libmamba
##conda config --experimental-solver=libmamba
conda install -c conda-forge root

# install awkward
conda install -c conda-forge awkward

# install uproot
conda install -c conda-forge uproot

## install uproot_methods
##conda install -c conda-forge uproot-methods

# install root_numpy
#conda config --set solver classic#this for root_numpy
conda install -c conda-forge root_numpy

# If having issues:
conda config --set channel_priority flexible

# install jupyterhub kernel
cd /nfs/dust/cms/user/lbenato/anaconda3/envs/run3 #you should be here already, better to be sure
conda activate run3
pip install ipykernel --user
python -m ipykernel install --user --name="run3"
```

### Cloning this repository

```bash
cd /nfs/dust/cms/user/lbenato
mkdir XXX #this is just my personal choice
cd XXX
git clone https://github.com/lbenato/MDS_run3.git
```
