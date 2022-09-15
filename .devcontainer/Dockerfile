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

# Set working directory
WORKDIR /home/scpdxcs
ENV HOME /home/scpdxcs

# Add and install the System Depdendencies
ADD ./requirements.txt /home/scpdxcs

RUN pip3 install \
  -f https://download.pytorch.org/whl/torch_stable.html \
  -f https://data.pyg.org/whl/torch-1.12.1+$DEVICE.html \
  -f https://pytorch-geometric.com/whl/torch-1.12.1+$DEVICE.html \
  -r ~/requirements.txt