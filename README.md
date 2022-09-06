# XCS224W Colab 5 Student Code Repository
This repository contains all the code for your assignment!
## Running the Jupyter notebook locally

We have created a `Dockerfile` in the `.devcontainer` subirectory. 
If you are using [Visual Studio Code](https://code.visualstudio.com/) 
you can develop directly in container with it. We have provided a 
 `devcontainer.json` configuration file that when executed, will
 build automatically the `Docker` image and start `VSCode` in the container.
 For finding out the prerequisites and how to deal with the configuration file 
 `devcontainer.json` please check the [Remote development in Containers tutorial](https://code.visualstudio.com/docs/remote/containers-tutorial).

 The `Dockerfile` is able to handle systems with or without `GPU`s. By default the 
 `devcontainer.json` builds the image with `GPU` support. If you don't have a `GPU`
 check the comments inside the `devcontainer.json` to be able to change the arguments
 required to build a Docker image without `GPU` support.

 Additionally, in order for `Docker` to be able to access the `GPU`, please install the 
 [NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#setting-up-nvidia-container-toolkit)

 If you are not using `Visual Studio Code` as IDE, you should be familiar with `Docker` 
 to be able to extract the build and run parameters from the `devcontainer.json` configuration file
 and execute them manually on your system! 