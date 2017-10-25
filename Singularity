BootStrap: docker
From: nvidia/cuda:8.0-cudnn6-runtime-ubuntu16.04

################################################################################
%labels
################################################################################
MAINTAINER Wolfgang Resch
VERSION v3

################################################################################
%environment
################################################################################
export PATH=/usr/local/sbin:/usr/sbin:/sbin:~/base/bin:~/build/bin/:/bin:/usr/bin:/usr/local/bin:/usr/local/cuda/bin:

################################################################################
%post
################################################################################

###
### install keras + tensorflow + other useful packages
###
apt-get update
apt-get install -y wget libhdf5-dev graphviz locales python python-pip git xvfb
locale-gen en_US.UTF-8
apt-get clean

wget ftp://ftp.cmbi.ru.nl/pub/software/dssp/dssp-2.0.4-linux-i386 -O /usr/local/bin/dssp
sudo chmod a+x /usr/local/bin/dssp

git clone https://github.com/mittinatten/freesasa.git
cd freesasa
autoreconf -i
./configure
make && make install

pip install --upgrade pip
pip install tensorflow-gpu==1.3.0
pip install keras==2.0.8
pip install setuptools wheel Pillow scikit-learn pandas matplotlib ipython==5.5.0
pip install h5py
pip install pyside
pip install mayavi
pip install --upgrade notebook


###
### destination for NIH HPC bind mounts
###
mkdir /gpfs /spin1 /gs2 /gs3 /gs4 /gs5 /gs6 /gs7 /gs8 /data /scratch /fdb /lscratch

