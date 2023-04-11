ARG BASE_IMAGE

FROM ${BASE_IMAGE}
SHELL ["/bin/bash", "-c"]

ARG DEVICE

LABEL org.opencontainers.image.authors="sebastian.hurubaru@stanford.edu"

# Update and install required tools
RUN apt-get update -y && apt-get upgrade -y

RUN DEBIAN_FRONTEND=noninteractive apt-get install --no-install-recommends -y \
  wget git sudo vim git-lfs \
  software-properties-common

# Install Python 3.8
RUN add-apt-repository -y ppa:deadsnakes/ppa && apt-get install -y python3-pip

# Add and install the System Depdendencies
ADD ./requirements.txt ./

RUN if [ -z "$DEVICE" ] ; then \
      pip3 install \
        -f https://download.pytorch.org/whl/torch_stable.html \
            gradescope-utils>=0.4.0 \
            jupyter>=1.0.0 \
            matplotlib>=3.2.2 \
            matplotlib-inline>=0.1.2 \
            networkx>=2.6.3 \
            numpy>=1.21.6 \
            pandas>=1.3.5 \
            scipy>=1.7.3 \
            scikit-learn>=1.0.2 \
            pillow>=7.1.2 \
            torch==1.13.1 \
            python-louvain==0.16; \
      # Separate on MacOS with Apple Silicon, to be able to install PyG  
      pip3 install \
        torch-scatter \
        torch-sparse \
        torch-geometric \
        ogb \
        deepsnap; \

    else \

      pip3 install \
      -f https://download.pytorch.org/whl/torch_stable.html \
      -f https://data.pyg.org/whl/torch-2.0.0+$DEVICE.html \
      -f https://pytorch-geometric.com/whl/torch-2.0.0+$DEVICE.html \
      -r ./requirements.txt; \
  fi
