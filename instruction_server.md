<p align="center">
  <img src="https://thumbs.gfycat.com/ThornyIllegalIndochinesetiger-size_restricted.gif" height="200px" alt="" />
</p>
<h1 align="center">:fire:GPU Cluster Instruction:fire:</h1>
<p align="center">
  <a href="#"><img src="http://hits.dwyl.io/L1NNA/Information.svg" alt="" /></a>
  <a href="#"><img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square" alt="" /></a>
  <a href="#"><img src="https://img.shields.io/github/issues/L1NNA/Information.svg?style=flat-square" alt="" /></a>
  <a href="#"><img src="https://img.shields.io/badge/badges-awesome-green.svg?style=flat-square&color=brightgreen" alt="" /></a>
  <a href="#"><img src="https://img.shields.io/github/license/Naereen/StrapDown.js.svg?style=flat-square&color=brightgreen" alt="" /></a>
</p>
<p align="center">
  <span>Contributors: Chris Molloy and Michael Wrana</span>
</p>



# Introduction
This is a tutorial for using the L1nna laboratory's GPU computing cluster.  It contains 8 Nvidia [RTX6000s](https://www.nvidia.com/en-us/design-visualization/quadro/rtx-6000/), each with 24GB of GDDR6 memory.  The server is ideal for performing GPU-intensive computing tasks that wouldn't be possible on your local machine.  Before you begin, please read the Queen's policy on [Acceptable Use of Information Technology Resources](https://www.queensu.ca/secretariat/policies/senate/electronic-information-security-policy-framework/acceptable-use-information).
# Important Links and Resources

- [Server Access](https://p.l1nna.com/)
- [Jupyter Lab Docs](https://jupyterlab.readthedocs.io/en/latest/)
- [Jupyter Notebook Docs](https://jupyter-notebook.readthedocs.io/en/stable/)
- [Bash Introduction](https://programminghistorian.org/en/lessons/intro-to-bash)
- [VSCode Introduction](https://code.visualstudio.com/docs/introvideos/basics)
- [Conda Docs](https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html)
- [Conda Cheatsheet](https://docs.conda.io/projects/conda/en/4.6.0/_downloads/52a95608c49671267e40c689e0bc00ca/conda-cheatsheet.pdf)
- [Tensorflow Guide](https://www.tensorflow.org/guide)
- [PyTorch Guide](https://pytorch.org/docs/stable/index.html)

# Initialization
Once you have connected your GitHub to the server you will now see the Hub Control Panel. The Hub Control Panel is where you can initialize or terminate your session. 

### Allocating Server Resources
Before you can begin using your the server you must first specify the resources you need.

![image](https://user-images.githubusercontent.com/25777239/92413172-dbf70a00-f11c-11ea-8fc7-2b22fd881824.png)

On your first startup of the server you will be allocated 200GB of storage. These 200GB will always be yours, so there is no need to worry about your work not being saved when you terminate your session.  If you ever require more storage contact the server host.
# Termination

![image](https://user-images.githubusercontent.com/25777239/92413201-fdf08c80-f11c-11ea-9f9c-702bfbdf4902.png)

**\*IMPORTANT!\*** Closing your JupyterLab tab will not  end your session and free up resources.  You must go to File -> Hub Control Panel, then in the new tab click the "Stop My Server" button.  All your files on the server will be automatically saved upon ending a session.
### Server Life cycle
After 12 hours of inactivity your session will be terminated.  All your files will be automatically saved to your allocated storage.


# JupyterLab

Once you have completed server initialization you will be connected to Jupiter through the server.

![image](https://user-images.githubusercontent.com/25777239/92413219-152f7a00-f11d-11ea-8be6-8688cac65986.png)

Here you can create a new notebook, console or terminal window, or you can launch an instance of VS Code.

### VS Code

![image](https://user-images.githubusercontent.com/25777239/92413231-1d87b500-f11d-11ea-8d07-889b2b0532c8.png)

VS Code on the server works exactly like a local version, this includes the ability to add extensions.  Your extensions and settings will be automatically saved in your server storage when your connection is terminated.

# GPU, Tensorflow & PyTorch

To check if the GPUs are actually avaiable, you can open a terminal and issue:
```
nvidia-smi
```
This will show the utilization status of the attached GPU devices. If you want to keep monitoring the utilization, you can type:
```
nvidia-smi -i
```

Tensor flow and PyTorch are both part of the base python environment on the server. To ensure that both packages are correctly installed you can test a Python import statement.  Note that after creating a new Conda environment, installing Tensorflow and PyTorch is required.

```
import tensorflow
tensorflow.__version__
```

to ensure Tensorflow has been installed, and 
```
import torch
torch.__version__
```
to ensure Pytorch has been installed.

If both snippets return a version number then that package has been correctly installed.

# Conda Environments
Currently, you are unable to activate conda environments through the standard JupyterLab terminal, instead you must use the VS Code Terminal.  Create a new VS Code page by opening it from the JupyterLab launcher.  Next open the menu in the top left and go to Terminal -> New Terminal.  From here you should be able to use all standard Conda commands.

### Linking Conda Environments to Python
After creating a new Conda environment, you can create a quick-link on the JupyterLab launcher to create a Python terminal with the new Conda environment.  First, activate your new Conda environment.  Then install `ipykernel` into that new environment.  Finally create a new kernel :

```
$ conda activate test
(test)$ conda install ipykernel
(test)$ ipython kernel install --user --name=<any_name_for_kernel>
(test)$ conda deactivate
```
Now, the a notebook for the new kernel should appear in your JupyterLab launcher after restarting JupyterLab.

![EnvironmentTutorial](https://user-images.githubusercontent.com/25777239/92413251-385a2980-f11d-11ea-95dc-bf666647be53.jpg)

[Source](https://stackoverflow.com/questions/53004311/how-to-add-conda-environment-to-jupyter-lab)

### Removing an added Environment
If you decide you no longer want a conda environment simply deleting it should remove the linked jupyter notebook launcher.  It it persists, however, you can type `jupyter kernelspec list` into the JupyterLab console to list avaliable kernels and remove the unwanted 

one with `jupyter kernelspec uninstall unwanted-kernel`.

[Source](https://stackoverflow.com/questions/42635310/remove-kernel-on-jupyter-notebook)

###### 
