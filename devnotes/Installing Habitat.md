# Installing Habitat

## 0. Install Anaconda
https://www.anaconda.com/distribution/#download-section  
Do create an easily manageable environment for habitat first!  
(See below: Install Dependencies)  
https://github.com/facebookresearch/habitat-sim#installation
  
Always activate the environment before using habitat by:  
```
conda activate habitat
```
## 1. Install both habitat-api and habitat-sim and Test the environment
Follow the official instructions.  
https://github.com/facebookresearch/habitat-api#installation

## 2. Request dataset download script and Use it
(See below: Dataset Download)  
https://niessner.github.io/Matterport/  
Usage:  
```
python2 download_mp.py --task habitat -o data/scene_datasets/mp3d/
```

## Issues & Tips
0.  
https://github.com/facebookresearch/habitat-sim#testing  
**Unsolved**  
Physics is under development and not working  

1.  
Completely uninstall python:  
**Solution:**  
Delete  
~/Library/Frameworks/Python.framework  

2.  
*Warning: Permanently added the RSA host key for IP address 'x.x.x.x' to the list of known hosts.*  
**Solution:**  
```
ssh-keygen
cat /Users/horonya/.ssh/id_rsa.pub
```
https://github.com/settings/keys  

3.  
*zsh: command not found: conda*  
*zsh: command not found: brew*  
**Solution:**  
chsh -s /bin/bash  

optional: Install brew  
https://brew.sh/  
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

4. 
*CommandNotFoundError: Your shell has not been properly configured to use 'conda activate'.*  
**Solution:**  
```
source ~/anaconda3/etc/profile.d/conda.sh
```
